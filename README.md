# Delhivery Data Analysis and Processing

## About Delhivery

Delhivery is the largest and fastest-growing fully integrated player in India by revenue in Fiscal 2021. Their goal is to build the operating system for commerce by combining world-class infrastructure, high-quality logistics operations, and cutting-edge engineering and technology capabilities.

The Data team at Delhivery leverages this data to enhance the quality, efficiency, and profitability of their business, maintaining a competitive edge.

## Objective

The objective of this project is to understand and process data from data engineering pipelines to:

1. Clean, sanitize, and manipulate data to extract useful features.
2. Interpret raw data to assist the data science team in building forecasting models.

## Dataset

**Dataset Link:** [delhivery_data.csv](data/delhivery_data.csv)

## Column Profiling

| Field Name                       | Description |
|----------------------------------|-------------|
| data                             | Tells whether the data is testing or training data |
| trip_creation_time               | Timestamp of trip creation |
| route_schedule_uuid              | Unique Id for a particular route schedule |
| route_type                       | Transportation type (FTL: Full Truck Load, Carting: Handling system consisting of small vehicles (carts)) |
| trip_uuid                        | Unique ID given to a particular trip (A trip may include different source and destination centers) |
| source_center                    | Source ID of trip origin |
| source_name                      | Source Name of trip origin |
| destination_center               | Destination ID |
| destination_name                 | Destination Name |
| od_start_time                    | Trip start time |
| od_end_time                      | Trip end time |
| start_scan_to_end_scan           | Time taken to deliver from source to destination |
| is_cutoff                        | Unknown field |
| cutoff_factor                    | Unknown field |
| cutoff_timestamp                 | Unknown field |
| actual_distance_to_destination   | Distance in Kms between source and destination warehouse |
| actual_time                      | Actual time taken to complete the delivery (Cumulative) |
| osrm_time                        | An open-source routing engine time calculator which computes the shortest path between points in a given map (Includes usual traffic, distance through major and minor roads) and gives the time (Cumulative) |
| osrm_distance                    | An open-source routing engine which computes the shortest path between points in a given map (Includes usual traffic, distance through major and minor roads) (Cumulative) |
| factor                           | Unknown field |
| segment_actual_time              | This is a segment time. Time taken by the subset of the package delivery |
| segment_osrm_time                | This is the OSRM segment time. Time taken by the subset of the package delivery |
| segment_osrm_distance            | This is the OSRM distance. Distance covered by subset of the package delivery |
| segment_factor                   | Unknown field |

## Concepts Used

- Feature Creation
- Relationship Analysis between Features
- Column Normalization / Standardization
- Handling Categorical Values
- Missing Values - Outlier Treatment / Identification

## Basic Data Cleaning and Exploration

1. Handle missing values.
2. Analyze the data structure.
3. Merge rows using the hints provided.
4. Build features to prepare the data for analysis. Extract features from:
    - **Destination Name:** Split and extract features (City, Place, State).
    - **Source Name:** Split and extract features (City, Place, State).
    - **Trip_creation_time:** Extract features like month, year, and day.

## In-Depth Analysis and Feature Engineering

1. Calculate the time taken between `od_start_time` and `od_end_time` and keep it as a feature.
2. Compare the calculated time with `start_scan_to_end_scan`. Perform hypothesis testing or visual analysis.
3. Compare `actual_time` (aggregated) with `OSRM time` (aggregated). Perform hypothesis testing or visual analysis.
4. Compare `actual_time` (aggregated) with `segment actual time` (aggregated). Perform hypothesis testing or visual analysis.
5. Compare `osrm_distance` (aggregated) with `segment osrm distance` (aggregated). Perform hypothesis testing or visual analysis.
6. Compare `osrm_time` (aggregated) with `segment osrm time` (aggregated). Perform hypothesis testing or visual analysis.
7. Identify outliers in numerical variables using visual analysis.
8. Handle outliers using the IQR method.
9. Perform one-hot encoding of categorical variables (e.g., route_type).
10. Normalize/standardize numerical features using MinMaxScaler or StandardScaler.

## Conclusion

This project aims to clean and process the dataset to assist in building accurate forecasting models. By performing the above steps, we aim to extract meaningful insights and features from the raw data, enabling the data science team to develop robust predictive models.
