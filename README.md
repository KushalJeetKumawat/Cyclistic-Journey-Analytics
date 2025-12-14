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

![SQL BigQuery](https://img.shields.io/badge/SQL-BigQuery-white?style=flat-square&labelColor=1A73E8&color=34A853&logo=googlebigquery&logoColor=white) 
![Tableau Dashboard](https://img.shields.io/badge/Tableau-Dashboard-white?style=flat-square&labelColor=FFD400&color=1A73E8) 
![Excel Export](https://img.shields.io/badge/Excel-Export-white?style=flat-square&labelColor=34A853&color=FFD400&logo=microsoft-excel&logoColor=white)

- **Phase 1 - Data Acquisition**

Collected trip-level data, weather records, and ZIP-code boundaries from Google BigQuery public datasets.

- **Phase 2 - Data Preparation**

Cleaned, standardized, and merged all datasets into a unified 2015 analytical table, resolving inconsistencies and aligning geographic and weather attributes

- **Phase 3 - SQL Analysis & Feature Engineering**

Created key analytical fields (trip duration, rainy-day flag, congestion ratio, trips per bike) and computed core KPIs to support visualization and interpretation.

- **Phase 4 - Dashboard Development**

Built four interactive Tableau dashboards covering seasonality, operational efficiency, top trip locations, and summer ride patterns.

- **Phase 5 - Insights & Recommendations**

Interpreted dashboard outputs to identify ridership trends, congestion hotspots, high-demand neighborhoods, and opportunites for operational improvement.

---

## Analysis & Visualization

> **Summary**

>This section summarizes the analytical work performed in BigQuery and the visualization process in Tableau.

 **SQL Analysis**

 - Trip data, weather data, and geographic information were combined in BigQuery to create a single analysis-ready dataset.
 - SQL was used to calculate key performance metrics such as trip count, trip duration, congestion ratio, and trips per bike.
 - Additional analytical fields were engineered to support operational and temporal comparisons, including seasonal labels, rainy day indicators, and hourly station activity.
 - The data was aggregated by date, usertype, and location to support a wide range of visual insights.

**Tableau Visualization**

- The final dataset was imported into Tableau Public, where four interactive dashboards was created.
- These dashboards highlight seasonal and weather trends, operational efficiency accross locations, top performing start and destination points,and detailed summer ride patterns.
- Users can explore the data through built-in parameters and filters such as month selection, usertype filtering, weather filtering, and metric toggles.
- The visualizations present the SQL analysis in a clear and accessible form for decision making.

---

## Insights

> **Explore Dashboard Highlights**

>This section breaks down major findings from each dashboard.

<table>
  <tr>
    <th>Insight Category</th>
    <th>What It Means</th>
    <th>Key Data Point</th>    
  </tr>

  <tr>
    <td><b>Seasonality</b></td>
    <td>Ridership peaks in warmer months, with fall showing the highest activity.</td>
    <td>September shows the strongest usage among all seasons.</td>
  </tr>

  <tr>
    <td><b>Weather Impact</b></td>
    <td>Riders prefer clear days, though summer demand remains stable even during rain.</td>
    <td>Summer rainy vs non-rainy trips remain nearly equal, unlike fall.</td>
  </tr>

  <tr>
    <td><b>Congestion</b></td>
    <td>Central neighborhoods experience operational strain and require capacity planning.</td>
    <td>Lower Manhattan (ZIP 10278) reaches a congestion ratio of <b>18.9</b>.</td>
  </tr>

  <tr>
    <td><b>Bike Utilization</b></td>
    <td>Certain stations are over-utilized, indicating imbalance in bike distribution.</td>
    <td>Chelsea & Clinton (ZIP 10199) shows <b>10.69 trips per bike</b>, the highest.</td>
  </tr>

  <tr>
    <td><b>Top Trip Locations</b></td>
    <td>Chelsea & Clinton and the Lower East Side act as major trip hubs.</td>
    <td>ZIP 10011 and ZIP 10003 lead in both trip count and duration.</td>
  </tr>

  <tr>
    <td><b>Summer Trends</b></td>
    <td>Peak summer activity occurs in September, with consistent demand in key neighborhoods.</td>
    <td>Lower East Side (ZIP 10003) logs <b>113,731 trips</b> in September.</td>
  </tr>  
</table>

<details>
  <summary><b>View Full Insight Comparison</b></summary>

<br>

<table>
  <tr>
    <th>Category</th>
    <th>Peak Areas / Seasons</th>
    <th>Main Influencing Factor</th>
    <th>Operational Implication</th>
  </tr>

   <tr>
    <td><b>Seasonality</b></td>
    <td>Summer & Fall</td>
    <td>Temperature & seasonal behavior</td>
    <td>Allocate more bikes and staff in peak months</td>
  </tr>

  <tr>
    <td><b>Weather Impact</b></td>
    <td>Summer holds steady even in rain</td>
    <td>Rain vs non-rain</td>
    <td>Plan redistribution differently on rainy days</td>
  </tr>

  <tr>
    <td><b>Congestion</b></td>
    <td>Chelsea & Clinton, Lower Manhattan</td>
    <td>High ride density</td>
    <td>Increase station capacity & rebalancing frequency</td>
  </tr>

  <tr>
    <td><b>Bike Utilization</b></td>
    <td>Central Manhattan zones</td>
    <td>Rider concentration</td>
    <td>Improve fleet distribution & reduce shortages</td>
  </tr>

  <tr>
    <td><b>Top Trip Locations</b></td>
    <td>Lower East Side, Chelsea & Clinton</td>
    <td>Trip duration & frequency</td>
    <td>Focus expansion & service enhancements here</td>
  </tr>

  <tr>
    <td><b>Summer Trends</b></td>
    <td>September peak</td>
    <td>Seasonal tourism & commuting</td>
    <td>Prepare for late-summer resource spikes</td>
  </tr>
</table>

</details>

--- 
