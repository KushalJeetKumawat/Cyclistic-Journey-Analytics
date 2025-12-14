<h1 align="left">Cyclistic Journey Analytics: A Data-Driven Study of Ridership</h1>

<table> 
  <tr>
    <td align="center" width="33%">
      <a href="#analysis--visualization">
        <img src="https://img.icons8.com/ios-filled/100/1a73e8/sql.png" width="30px"/>
        <h4>SQL Analysis</h4>
      </a>
    </td>
    <td align="center" width="33%">
      <a href="#insights">
        <img src="https://img.icons8.com/ios-filled/100/f9ab00/combo-chart.png" width="30px"/>
        <h4>Insights and Highlights</h4>
      </a>
    </td>
    <td align="center" width="33%">
      <a href="#business-impact--recommendations">
        <img src="https://img.icons8.com/ios-filled/100/34a853/positive-dynamic.png" width="30px"/>
        <h4>Business Impact</h4>
      </a>
    </td>    
  </tr>
</table>

> **Project Journey**

> What began as millons of trip records gradually turned into patterns, places, and seasons. With each query came a new layer of meaning, and with each visualization, the story became clearer. This project reflects how data, when explored with curiosity and purpose, transforms into a story worth seeing.
---

## Project Overview 

**1. Business Context**

Cyclistic is a fictitious NYC bike-share company created for an analytics case study. This project examines how riders move through the city, including when they ride, where demand concentrates, and how different mobility conditions influence usage patterns. These insights support planning decisions, service improvements, and bike availability management.

**2. Objective of the Project** 

The goal of this project is to analyze Cyclistic’s 2015 ridership data to uncover seasonal trends, location specific demand, weather impacts, congestion patterns, and bike utilization efficiency. This helps identify high demand zones, operational bottlenecks, and opportunities for resource allocation.

**3. Data Used in the Analysis**

The analysis combines CitiBike trip records, daily weather observations, and ZIP-code level geographic information. These datasets were cleaned, merged, and transformed in Google BigQuery to create a single unified analytical dataset enriched with metrics such as trip duration, congestion ratio, and trips per bike.

**4. Project Deliverables**

The final deliverables include a structured analytical dataset, defined KPIs for operational and behavioral insights, and four interactive Tableau dashboards covering seasonality, system efficiency, top trip locations, and summer ride patterns. These visual tools enable data-driven decision-making for planning and operational improvement.

---
## Dataset Summary Panel

![Rides](https://img.shields.io/badge/Total_Trips_Analyzed-~2.3M-white?style=flat-square&labelColor=1A73E8&color=34A853) 
![Months](https://img.shields.io/badge/Peak_Month-September-white?style=flat-square&labelColor=FFD400&color=1A73E8) 
![Station](https://img.shields.io/badge/Top_Station-Chelsea_%26_Clinton-white?style=flat-square&labelColor=34A853&color=FFD400) 

> **Note**

> This project uses a fictional Cyclistic business context, while the underlying 2015 trip data is sourced from real CitiBike records.

<table>
  <tr>
    <td valign="top" width=55%">
      <table>
        <tr><th>Dataset</th><th>Type</th><th>Description</th></tr>
        <tr><td>New York CitiBike Trips </td><td>Primary</td><td>Trip-level ride data including timestamps, usertype, bike ID, and station coordinates.
</td></tr>
        <tr><td>NOAA GSOD Weather Data</td><td>Secondary</td><td>Daily temperature, wind speed and precipitation for NYC (Central Park weather station).</td></tr>
        <tr><td>U.S. ZIP Code Boundaries</td><td>Secondary</td><td>Spatial polygons mapping station coordinates to ZIP codes.</td></tr>
        <tr><td>ZIP Code Lookup Table</td><td>Additional</td><td>Mapping of ZIP codes to borough and neighborhood names.</td></tr>
      </table>
    </td>
    <td valign="top" width=45%">
      <table>
        <tr><th>Parameter</th><th>Value</th></tr>
        <tr><td>Time Period Covered</td><td>January-December 2015</td></tr>
        <tr><td>Final Analytical Dataset</td><td>Combined trips + weather + ZIP mapping + engineered metrics</td></tr>
        <tr><td>Data Source</td><td>Google BigQuery Public Datasets</td></tr>
      </table>
    </td>
  </tr>
</table>
      
---

## Project Timeline
