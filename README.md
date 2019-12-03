# Data Engineering Nano Degree

## Capstone Project 

## Purpose
Analyse any correlation between crimes and temperature

## Execution

Crime data and temperature date are already at s3 and the main aim is to extract the data and process the data then store the data in a bucket for analysts to retrieve. 

## Data

### Temperature: 
[Historical Hourly Weather Data 2012-2017](https://www.kaggle.com/selfishgene/historical-hourly-weather-data)

[Credits](https://www.kaggle.com/selfishgene)

Field | Type | Details
------| ----- | ---- 
datetime | datetime | YYYY/MM/DD
Vancouver | float | Kelvin

Note: This data is available for 30 US and Canadian Cities, as well as 6 Israeli cities. I only show Vancouver.

___
### Crimes:
[Los Angeles 2010 to Present  Open Data](https://data.lacity.org)

To comply with the project requirements, the data contains more than 2,000,000 Rows

Field | Type | 
------| ----- | 
DR number | int | 
datetime | datetime | 
Crime code | int | 
Crime code description | varchar | 
Reporting District | int | 
Area Name | varchar |
Area ID | int |
Date Occured | datetime
day | int |
hour | int |
year | int | 
month | int |

This dataset partitioned by YYYY/MM/DD and stored on s3 as csv.


## Process
We will be using PySpark to analyze and store the data. We will be using Airflow to manage the orchestration.

Airflow Steps:
* Load Temperture and Crime Data
* Aggregate Temperature and Crime Data
* Check if Temperature and Crime Data are Valid
* Create a new dataframe and append it to the previous data using Parquet


#### Airflow Dag
![Airflow Dag](sample_dag.png)

#### Airflow Tree View
![Airflow Dag](treeview.png)

#### Airflow Running Jobs
![Airflow Dag](progress.png)

#### Results on S3
![S3 Results](results_s3.png)


## Results

### Sample Graph
![Sample Results](results.png)
![Sample Results 2](results1.png)
![Sample Results 3](results2.png)

## Scaling
Since this system is built on Spark and Airflow it is very much horizontally scalable. Airflow can handle the processing of millions of records. 

## Credit
Thanks to @sariabod for the inspiration


