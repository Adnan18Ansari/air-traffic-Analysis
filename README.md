# Air Traffic Analysis During Covid-19 

## Introduction
Aviation provides the only rapid worldwide transportation network, which makes it essential for global business. It generates economic growth, creates jobs, and facilitates international trade and tourism. The air transport industry supports a total of 65.5 million jobs globally. It provides 10.2 million direct jobs.

This project aims to analyse the impact of Covid-19 on the aviation industry. It also provided a great opportunity to develop skills and experience in a range of tools such as Apache Airflow, Apache Spark, Tableau and some of the AWS cloud services.

## Architecture
<p align="left">
    <img src="https://github.com/Adnan18Ansari/air-traffic-Analysis/blob/main/images/Final-architecture.png">
</p>

## Airflow Data Pipeline
<p align="left">
    <img src="https://github.com/Adnan18Ansari/air-traffic-Analysis/blob/main/images/Airflow_graph_view.png">
</p>

Airflow orchestrates the following tasks:-
1. Upload the data and scripts from local machine to S3 bucket
2. Provision an EMR cluster
3. Submit a spark job to EMR cluster that executes the ETL workflow
4. Wait for the spark submission to complete
5. Terminate the EMR cluster


## Data sources
1. [Opensky](https://zenodo.org/record/6603766)
    The data in this dataset is derived and cleaned from the full OpenSky dataset to illustrate the development of air traffic during the COVID-19 pandemic. It spans all flights seen by the network's more than 2500 members since 1 January 2019.
    In order to avoid the out-of-memory issue, data is incrementally loaded into the s3 bucket.
2. [JHU CSSE](https://github.com/CSSEGISandData/COVID-19)
    This dataset includes time-series data tracking the number of people affected by COVID-19 worldwide
3. [Airport Codes](https://datahub.io/core/airport-codes)
    The data is in CSV and contains the list of all airport codes.
4. [Country-Codes](https://datahub.io/core/country-list)
    The dataset contains country names (official short names in English) in alphabetical order as given in ISO 3166-1 and the corresponding ISO 3166-1-alpha-2 code elements. [ISO 3166-1]
5. [Continent-codes](https://www.kaggle.com/datasets/andradaolteanu/country-mapping-iso-continent-region)
    The dataset was used to map countries with continents.
6. [States](https://www.kaggle.com/datasets/arjunaraoc/india-states)
    Contains ISO-3 codes and names of Indian States.


## Setup
### 1. Prerequisite
1. Docker and Docker Compose v1.27.0 or later
2. [AWS account]
3. [AWS CLI installed and configured]
4. [Tableau Desktop]

### 2. Run setup.sh
Download the data and create an s3 bucket by running `setup.sh`.
`setup.sh` also starts to incrementally load the opensky data to the S3 bucket.
After `setup.sh` runs successfully, start the docker container.

### 3. Docker and Airflow
We use the following docker containers -
1. Airflow
2. Postgres DB (as Airflow metadata DB)
Open the Airflow UI on localhost:8080 in browser, and start the covid_flights_dag DAG.

### 4. AWS
Once the dag-run is successful, check the output folder of the S3 bucket.
<p align="left">
    <img src="https://github.com/Adnan18Ansari/air-traffic-Analysis/blob/main/images/S3_outputdir.png">
</p>

### 5. Tableau Dashboard 
<p align="left">
    <img src="https://github.com/Adnan18Ansari/air-traffic-Analysis/blob/main/images/Tableau/GLOBAL.png">
</p>

<p align="left">
    <img src="https://github.com/Adnan18Ansari/air-traffic-Analysis/blob/main/images/Tableau/INDIA.png">
</p>
