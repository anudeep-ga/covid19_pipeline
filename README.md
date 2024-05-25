
# COVID 19 Data Pipeline

## Introduction

Our project aims to establish a robust data pipeline on Microsoft Azure for analyzing COVID-19
data sourced from the European Centre for Disease Prevention and Control (ECDC) website.
The objective is to extract meaningful insights from key datasets such as population, cases and
deaths, hospital admissions, testing, etc. The insights derived will contribute to informed
decision-making for both strategic planning and operational responses in the context of the
ongoing pandemic.


## Dataset Selection

The chosen dataset originates from the ECDC website and encompasses a comprehensive set of
COVID-19-related information. This includes datasets on population demographics, reported
cases and deaths, hospital admissions, testing metrics, and other pertinent epidemiological
data. This dataset provides a rich source of information for a thorough analysis of the
pandemic's impact.

Link: https://www.ecdc.europa.eu/en/data/downloadable-datasets

## Analysis Dimensions

Temporal Analysis:
- Objective: Examine temporal trends and variations in COVID-19 metrics.
- Actions: Analyze daily, weekly, and monthly patterns in reported cases, deaths, and hospital admissions.
Geographical Analysis:
- Objective: Understand the regional impact of COVID-19.
- Actions: Break down data by countries, regions, or other relevant geographical units.
- Explore variations in testing rates and healthcare capacities.
Demographic Analysis:
- Objective: Investigate the impact of COVID-19 across different demographic groups.
- Actions: Analyze how age, gender, and other demographic factors influence susceptibility, severity, and mortality rates.

## Data Pipeline Architecture

![Image](https://github.com/anudeep-ga/covid19_pipeline/blob/main/covid_data_pipeline.png?raw=true)

### 1. Data Ingestion
a. Using Azure Blob Storage

- Description: Uploaded the population by country dataset in TSV format, encapsulated in a gzip file, to Azure Blob Storage for efficient storage and retrieval. The Azure Blob Storage serves as a centralized repository for raw data.
- Actions:
  - Linked Services: Established connections to Azure Blob Storage.
  - Datasets: Defined datasets in Azure Data Factory (ADF) to represent the source (gzip file) and target (TSV file).
  - ADF Pipeline: Developed an ADF pipeline to orchestrate the workflow, encompassing activities such as copying data, decompressing the gzip file, and validating the data.
- Validation Activity: Implemented validation activities within the pipeline to ensure the integrity and quality of the ingested data.
- Deletion Activity: Configured activities to delete the gzip file post data extraction to optimize storage space.
- Event Trigger: Set up event triggers to automate the pipeline execution when new data is detected.
b. Ingestion from HTTP (ECDC website)
- Description: Extracted COVID-19-related data, including cases, deaths, and hospital admissions, from the European Centre for Disease Prevention and Control (ECDC) website using HTTP as the source. This ensures the pipeline stays up to date with the latest information.
- Actions:
  - HTTP Connection: Established a connection to the ECDC website an HTTP source.
  - Datasets: Defined datasets in ADF to represent the external data.
  - ADF Pipeline: Developed an ADF pipeline to fetch and ingest the data from the ECDC website.

### 2. Data Transformation
a. Transformation using Data Flows
- Description: Applied a series of transformations to the ingested data using Azure Data Flows. This includes filtering, selecting specific columns, pivoting data, joining datasets, and performing lookup operations to shape the data according to reporting requirements.
- Actions:
  - Data Flow Components: Utilized various components within Azure  ta Flows, such as source, filter, select, pivot, join, lookup, and sink.
  - ADF Pipeline: Configured an ADF pipeline to orchestrate the flow of data through the transformation process.
b. Data Bricks
- Description: Leveraged Azure Databricks to handle more complex and intensive data transformations. Databricks provides a scalable and collaborative environment for big data analytics and processing.
- Actions:
  - Cluster Configuration: Created and configured a Databricks  cluster to handle the processing workload.
  - Data Lake Storage Mounting: Mounted Data Lake Storage to provide Databricks access to relevant data.
  - Transformation: Implemented advanced transformations within the Databricks environment, taking advantage of its capabilities for distributed computing.
### 3. Azure SQL and Monitoring the Pipeline
- Description: Loaded the transformed data into Azure SQL to provide a structured and optimized storage solution for reporting purposes. Ensured the pipeline's readiness for production use by incorporating monitoring features.
- Actions:
  - Data Loading: Configured ADF to load the transformed data into  ure SQL for structured storage.
  - Monitoring Features: Enhanced the pipeline with monitoring capabilities to track performance, detect errors, and ensure data integrity.
  - Pipeline Optimization: Ensured the pipeline is robust and ready for production use by optimizing performance and reliability.

### 4. Analytics
- Description: Created visually compelling charts and dashboards using Power BI to provide meaningful insights and facilitate easier interpretation of COVID-19 data.
- Actions:
  - Data Connection: Connected Power BI to the Azure SQL database the storage location where the transformed data resides.
  - Visualization: Developed charts, graphs, and interactive dashboards to represent key metrics and trends in COVID-19 data.
  - Scheduled Updates: Enabled scheduled updates to ensure that the analytics data remains current and reflective of the latest information.

 ## BI Dashboard

![Image](https://github.com/anudeep-ga/covid19_pipeline/blob/main/covid_data_pipeline.png?raw=true)

## Conclusion
The Azure-based data pipeline's successful deployment signifies a pivotal advancement in
streamlining COVID-19 data management. From ingestion to dashboard creation, the pipeline
ensures seamless information flow, empowering stakeholders with real-time insights. Azure's
robust services contribute to scalability, reliability, and operational efficiency, enhancing the
pipeline's overall performance and utility.

## Future Work
In the future, optimizing data processing speed, exploring additional data sources, and
fortifying security measures are paramount. Continuous performance monitoring, adaptation
to emerging technologies, and integration of predictive analytics through machine learning will
further elevate the pipeline's capabilities. Regular updates will be essential to align with
evolving global health demands and maintain the pipeline's agility and effectiveness.
