<img width="662" alt="image" src="https://github.com/user-attachments/assets/5f31095c-84df-4386-8fa4-cdceb464f98d"># The process of stream processing, ETL, and data ingestion using Azure Databricks
This project leverages Azure cloud services to build robust, scalable, and secure data pipelines for data ingestion, processing, and transformation.
## About data
The government of New York State collects information about traffic accidents occurring across the counties of the state to analyze and implement measures to reduce the likelihood of accidents and casualties on New York's roads. Every day, hundreds to thousands of accidents are recorded within the state's jurisdiction, with information being collected from various sources.

To address this issue, a robust, flexible, and automated data processing system is required to collect, standardize, and analyze data from multiple sources, with the goal of implementing measures to reduce traffic accidents.
## Data Flow Diagram
![flow drawio](https://github.com/user-attachments/assets/38164e0f-4900-448e-af09-02ca1e86c142)

Below is the explanation of the process:
1. Data Source:

Data is initially fetched from an API endpoint (https://data.cityofnewyork.us/resource/h9gi-nx95.json), which provides JSON files containing raw accident data.
2. Azure Data Factory:

Azure Data Factory (ADF) is used as the ETL (Extract, Transform, Load) tool to ingest data from the API and process it. It handles raw ingestion and prepares the data for further processing and storage in Azure Data Lake.
3. Azure Data Lake Storage Gen 2 (ADLS):

Data is stored in Azure Data Lake following the Delta Lake architecture, divided into three layers:
Bronze Layer: Stores raw ingested accident data.
Silver Layer: Contains filtered and cleaned data, prepared for analysis.
Gold Layer: Holds feature-engineered and aggregated data, ready for machine learning or direct consumption.
3. Azure Databricks:

Azure Databricks is used to process and transform data from the Silver layer.
A machine learning model is trained on historical accident data to predict whether a new accident is likely to involve injuries or not. The model is deployed and used for real-time predictions.
4. Web Applications:

New traffic accident data is sent to the pipeline through the Web Application.
The application sends raw accident data to Azure Event Hub, which acts as the message broker.
5. Azure Event Hub:

Event Hub receives real-time raw data from the Web Application and forwards it to Azure Data Lake for storage in the Bronze Layer.
The same data is also routed to Azure Databricks, where the trained machine learning model processes it and generates a prediction.

7. Security & Governance:

Microsoft Entra ID (Azure Active Directory) and Azure Key Vault ensure secure access to resources and handle sensitive credentials such as API keys, Databricks Access token and secrets.
###### Summary:
This pipeline automates the ingestion, processing, and prediction of traffic accident data. 
## Implementation system
###### The processing flow of transferring data from API endpoints to Azure Data Lake Storage Gen2
<img width="897" alt="image" src="https://github.com/user-attachments/assets/b0dd1576-d5ea-4e6a-8ad2-7d04cbc3163a">

###### Process and move data from the Bronze layer to the Silver layer in ADLS2
<img width="901" alt="image" src="https://github.com/user-attachments/assets/945a968c-65ef-4ff3-a2c6-81d01ece344d">

###### Process and move data from the Silver layer to the Gold layer in ADLS2
<img width="903" alt="image" src="https://github.com/user-attachments/assets/3feaa742-4e04-4054-8e8e-8f3a4e45b47e">

###### Create a pipeline from notebooks in Azure Data Factory
<img width="636" alt="image" src="https://github.com/user-attachments/assets/7ab1dcaa-8538-453b-ba21-c23cbd7c36ac">

###### Implement model training on the dataset
<img width="662" alt="image" src="https://github.com/user-attachments/assets/49f41363-c2ea-4bd6-a771-fc30412256ae">

###### Visualize results based on parameters or model types
<img width="634" alt="image" src="https://github.com/user-attachments/assets/322928eb-499e-464c-8bdf-79d87707f04f">
<img width="533" alt="image" src="https://github.com/user-attachments/assets/c1772f57-b68c-4d08-9622-6e3629321832">


###### Provide an API mechanism for model usage
![image](https://github.com/user-attachments/assets/6a5e87d6-2d1f-455b-96b8-ddd4a990ff02)

Model API
![image](https://github.com/user-attachments/assets/82728d33-13bb-4930-b2e5-8bdd3ffa320a)

###### Create an Event Hub and Stream Analytics Job to Transfer Data into a Data Lake Container
<img width="901" alt="image" src="https://github.com/user-attachments/assets/f8364d98-1010-439c-8e62-3125f340e3f2">

###### Develop a web page using the model's API: send requests to the cloud system, receive responses, and parse the results
<img width="794" alt="image" src="https://github.com/user-attachments/assets/2e7d2e79-b0f4-49a9-873e-d4eaa29069b5">







