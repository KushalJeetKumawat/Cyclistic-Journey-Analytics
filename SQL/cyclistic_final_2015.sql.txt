
CREATE OR REPLACE TABLE `query-practice-466604.cyclistic_project_eoc_2.cyclistic_final_2015`
 AS
WITH base_trips AS ( 
  SELECT
    usertype,
    ZIPSTART.zip_code AS zip_code_start,
    ZIPSTARTNAME.borough AS borough_start,
    ZIPSTARTNAME.neighborhood AS neighborhood_start,
    ZIPEND.zip_code AS zip_code_end,
    ZIPENDNAME.borough AS borough_end,
    ZIPENDNAME.neighborhood AS neighborhood_end,
    DATE_ADD(DATE(TRI.starttime), INTERVAL 5 YEAR) AS start_day,
    DATE_ADD(DATE(TRI.stoptime), INTERVAL 5 YEAR) AS stop_day,
    WEA.temp AS day_mean_temperature,
    WEA.wdsp AS day_mean_wind_speed,
    WEA.prcp AS day_total_precipitation,
    CASE WHEN WEA.prcp > 0 THEN 1 ELSE 0 END AS is_rainy_day,
    TIMESTAMP_DIFF(TRI.stoptime, TRI.starttime, MINUTE) AS trip_minutes,
    TRI.start_station_id,
    TRI.bikeid,
    TRI.starttime
  FROM
    `bigquery-public-data.new_york_citibike.citibike_trips` AS TRI
  INNER JOIN
    `bigquery-public-data.geo_us_boundaries.zip_codes` ZIPSTART
      ON ST_WITHIN(ST_GEOGPOINT(TRI.start_station_longitude, TRI.start_station_latitude),
                   ZIPSTART.zip_code_geom)
  INNER JOIN
    `bigquery-public-data.geo_us_boundaries.zip_codes` ZIPEND
      ON ST_WITHIN(ST_GEOGPOINT(TRI.end_station_longitude, TRI.end_station_latitude),
                   ZIPEND.zip_code_geom)
  INNER JOIN
    `bigquery-public-data.noaa_gsod.gsod20*` AS WEA
      ON PARSE_DATE("%Y%m%d", CONCAT(WEA.year, WEA.mo, WEA.da)) = DATE(TRI.starttime)
  INNER JOIN
    `query-practice-466604.cyclistic_project_eoc_2.us_zip_codes` AS ZIPSTARTNAME
      ON ZIPSTART.zip_code = CAST(ZIPSTARTNAME.zip AS STRING)
  INNER JOIN
    `query-practice-466604.cyclistic_project_eoc_2.us_zip_codes` AS ZIPENDNAME
      ON ZIPEND.zip_code = CAST(ZIPENDNAME.zip AS STRING)
  WHERE
    WEA.wban = '94728'
    AND EXTRACT(YEAR FROM DATE(TRI.starttime)) = 2015
),

-- Congestion at station
station_hourly AS (
  SELECT
    start_station_id,
    DATE(starttime) AS trip_date,
    EXTRACT(HOUR FROM starttime) AS trip_hour,
    COUNT(*) AS starts
  FROM base_trips
  GROUP BY start_station_id, trip_date, trip_hour
),
station_congestion AS (
  SELECT
    start_station_id,
    AVG(starts) AS avg_hourly_starts,
    MAX(starts) AS max_hourly_starts,
    SAFE_DIVIDE(MAX(starts), NULLIF(AVG(starts),0)) AS congestion_ratio
  FROM station_hourly
  GROUP BY start_station_id
),

-- Bike utilization proxy
station_utilization AS (
  SELECT
    start_station_id,
    COUNT(*) AS trips_from_station,
    COUNT(DISTINCT bikeid) AS distinct_bikes,
    SAFE_DIVIDE(COUNT(*), COUNT(DISTINCT bikeid)) AS trips_per_bike
  FROM base_trips
  GROUP BY start_station_id
)

-- Final aggregated output grouped by geography + day
SELECT
  b.usertype,
  b.zip_code_start,
  b.borough_start,
  b.neighborhood_start,
  b.zip_code_end,
  b.borough_end,
  b.neighborhood_end,
  b.start_day,
  b.stop_day,
  b.day_mean_temperature,
  b.day_mean_wind_speed,
  b.day_total_precipitation,
  b.is_rainy_day,
  COUNT(*) AS trip_count,
  SUM(b.trip_minutes) AS total_trip_minutes,
  AVG(b.trip_minutes) AS avg_trip_minutes,
  c.avg_hourly_starts,
  c.max_hourly_starts,
  c.congestion_ratio,
  s.trips_per_bike
FROM base_trips b
LEFT JOIN station_congestion c
  ON b.start_station_id = c.start_station_id
LEFT JOIN station_utilization s
  ON b.start_station_id = s.start_station_id
GROUP BY
  b.usertype, b.zip_code_start, b.borough_start, b.neighborhood_start,
  b.zip_code_end, b.borough_end, b.neighborhood_end,
  b.start_day, b.stop_day,
  b.day_mean_temperature, b.day_mean_wind_speed,
  b.day_total_precipitation, b.is_rainy_day,
  c.avg_hourly_starts, c.max_hourly_starts, c.congestion_ratio,
  s.trips_per_bike
ORDER BY b.start_day;

