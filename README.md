# Chicago Crime Analytics \& Operational Resource Allocation

## Data-Driven Command Decisions for Patrol Deployment and Risk Prevention (2020–2022)



### Project Overview



Metropolitan police departments face severe resource constraints and surging call volumes. Traditional monthly summary reports often obscure critical intraday spikes, preventing command staff from effectively optimizing shift overlays.



This capstone project synthesizes 629,345 criminal incident records from the Chicago Police Department’s Citizen Law Enforcement Analysis and Reporting (CLEAR) system (2020–2022). The goal is to build an interactive, multi-page executive Power BI dashboard that shifts police command from reactive reporting to proactive, hourly, and district-level resource deployment.



### Data Architecture \& ETL Pipeline



#### 1\. Data Sources

The database integrates five core files:

* Crime\_2020.csv (211,426 X 18): Annual incident records for 2020.

&#x20;

* Crime\_2021.csv (207,430 X 18): Annual incident records for 2021.



* Crime\_2022.csv (220,550 X 18): Partial-year incident records (Jan 1 – Dec 7, 2022).



* Crime\_Types.csv (473 X 5): Primary lookup table for offense categories, IUCR, and FBI codes.



* Location\_Types.csv (177 IDs): Lookup table for physical premise descriptions.



#### 2\. Data Hygiene \& Transformation (Power Query)

Raw public safety data contains severe quality issues. The following ETL steps were executed in Power Query:

* Handling Partial Data \& Outliers: Excluded 10,035 rows missing critical spatial coordinates and dropped 25 erroneous records tagged to a non-existent "District 31".



* Structural Transposition: Transposed the sideways-laid Location\_Types table into a clean vertical tabular format.

&#x20;

* Text Normalization: Standardized shorthand offense descriptions (e.g., transforming variant spellings like Crim Sexual Assault and Criminal Sexual Assault into a uniform format).



* Column Pruning: Removed redundant raw coordinate strings and system metadata (Updated On) to minimize file footprint and optimize memory.



#### 3\. Star Schema Data Model

The final relational model utilizes a Star Schema architecture:

* Fact Table: Incidents (storing transactional event attributes, foreign keys, and status flags like Arrest and Domestic).



* Dimension Tables: Calendar, Crime Types, Location Types, and Community Areas linked via clean 1-to-many relationships.



### Key Executive Findings \& Insights

1. Volume vs. Clearance Divergence: Total reported incidents rebounded to 219,033 in 2022, yet the citywide arrest rate dropped to 11.2% (down from 16.2% in 2020). Out of 629k total records, 546,252 incidents (86.8%) resulted in no arrest, driven heavily by unassigned property theft and property damage backlogs.
2. Extreme Hourly Workload Clustering: Crime volume exhibits a steep diurnal trough between 03:00–05:00 AM, followed by a sharp ramp-up into a sustained peak window from 16:00 to 00:00.
3. Geographic Workload Concentration: District 6 (40.8K), District 11 (39.7K), and District 8 (39.1K) consistently carry the heaviest workload in the city—handling over 3x the volume of low-density outer districts like District 20.
4. Domestic \& Premise Patterns: Domestic incidents account for 19.65% of citywide crime, with 42.94% of all offences concentrated in residential and apartment complexes. Proactively enforced categories (narcotics, prostitution) maintain >95% clearance, whereas property crimes suffer sub-10% clearance.

##### 

### Strategic Recommendations for Command Staff

* Establish a "Power Shift" Overlay (16:00 – 00:00): Transition tactical units away from quiet early-morning windows (03:00–07:00) to align directly with the 39.5% afternoon-to-midnight crime surge.



* District Resource Rebalancing: Reallocate roving patrol units from low-volume regions (e.g., District 20) toward high-pressure anchors in Districts 6, 11, and 8 during Friday and Saturday evening hours.



* Commercial Retail Patrols: Increase visible foot and bike patrols in commercial corridors between 12:00 and 18:00 to mitigate high-volume property theft.



* Domestic Rapid Response Protocols: Form dedicated domestic intervention response units tied directly to high-density residential wards to address the 19.65% domestic baseline.

