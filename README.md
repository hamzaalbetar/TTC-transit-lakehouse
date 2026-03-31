# 🚍 Transit Lakehouse Project (GTFS)

## 📌 Overview

This project implements a modern data engineering pipeline using a Lakehouse architecture to process and analyze public transit data based on the GTFS standard.

The pipeline ingests raw transit data, transforms it through multiple layers, and delivers a clean analytical model using a Star Schema design.

##Dataset used:
Toronto Transit Commission

## 🏗️ Architecture

The project follows a Medallion Architecture:

### 🟤 Bronze Layer

Raw ingestion of GTFS data

No transformations applied

Data stored as-is (mostly strings)


### ⚪ Silver Layer
Data cleaning and standardization

Schema enforcement (casting data types)

Handling inconsistencies (e.g., time formats, coordinates)


### 🟡 Gold Layer
Business-ready data model

Star Schema implementation

Optimized for analytical queries


## ⭐ Data Model (Star Schema)
### 🟦 Dimensions
#### dim_routes
route_id (PK)

route_short_name

route_long_name

route_type

route_type_desc


#### dim_stops
stop_id (PK)

stop_name

stop_lat

stop_lon

wheelchair_boarding

wheelchair_access_desc


#### dim_trips
trip_id (PK)

route_id (FK)

service_id

direction_id

shape_id

route_short_name

route_type

route_type_desc


#### dim_service
service_id (PK)

monday → sunday

start_date

end_date


### 🟥 Fact Table
#### fact_stop_times
trip_id (FK)

stop_id (FK)

stop_sequence

arrival_time

departure_time


## 🧰 Technologies Used
PySpark

Databricks (Community Edition)

Delta Lake

Git & GitHub


## 📊 Key Capabilities
Trip-level and stop-level analysis

Route performance insights

Temporal analysis using standardized time metrics

Accessibility analysis (wheelchair support)


## 🚀 Future Improvements
Integrate calendar_dates for service exception handling

Build analytical dashboards (Power BI / Tableau)

Add real-time or streaming data support

Implement data quality checks and validation rules


## 🧠 Notes

This project focuses on building a clean and scalable analytical model rather than only data transformation, demonstrating core data engineering concepts including:

Medallion Architecture

Data Modeling (Star Schema)

Data Standardization

Analytical readiness
