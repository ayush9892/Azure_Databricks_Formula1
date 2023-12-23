# Azure Databricks Formula1

### Concept of the Project 💡
- This project involves the acquisition of Formula1 Datasets from the Ergast API. The transformations on these datasets are subsequently processed in 3 layers, i.e., Bronze -> Silver -> Gold. The transformations are executed using Databricks. The resultant data of each transformation is loaded into DELTA Lake with the intention of enabling the Analytics team to draw meaningful and practical insights from these datasets. The primary objective is to comprehensively understand the workings of Databricks.

### Task 🎯
- The mission of this project is to transform the Bronze data (i.e., Raw data) of different formats into Silver data (i.e., Ingested data) in columnar format (i.e., Parquet), and then into Gold data (i.e., Presentation data) using PySpark in Databricks.

  
### Source Data: 📤
- Ergast (https://ergast.com/mrd/)
- I have manually ingested these datasets in different format into Datalake Gen2; [Datasets](https://github.com/ayush9892/Azure_Databricks_Formula1/tree/main/Datasets)


### Destination: 📥📍
- Azure Data Lake Gen2 Storage

## Tools ⚙

### Jobs Run

- ADF Pipeline

### Transformation

- Databricks

## Approach

### Environment Setup
- Azure Subscription
- Data Factory
- Data Lake Storage Gen2
- Azure Key vaults
- Azure Databricks Cluster

# Architecture Overview
  ![Architecture](https://learn.microsoft.com/en-us/azure/architecture/solution-ideas/media/ingest-etl-and-stream-processing-with-azure-databricks.svg#lightbox)


### Pipeline Steps:
1. Create a Linked Service To Azure Databricks
2. Create a Linked Service To Azure Data Lake storage (GEN2)
3. Create 1st Pipeline:
- Check metadata exists before executing the ingestion notebooks using the IF Condition
4. Create 2nd Pipeline:
- Execute trans/1.race_results.ipynb first, then link trans/2.driver_standings.ipynb and trans/3.constructor_standings.ipynb on success.
5. Create 3rd Pipeline:
- Create dependend execution of 1st to 2nd pipeline
- Finally execute the notebooks
6. Create Tumbling window trigger scope
  
![image](https://github.com/ayush9892/Azure_Databricks_Formula1/assets/85745368/9501b544-ae5e-40bd-ac31-78355bbcab36)

![image](https://github.com/ayush9892/Azure_Databricks_Formula1/assets/85745368/9bbb40b1-5c73-45f4-8dae-16801973ed53)

![image](https://github.com/ayush9892/Azure_Databricks_Formula1/assets/85745368/d03b4fdf-f15e-4844-b229-5edf67c57621)


# Used Technologies
- Azure DataFactory
- Azure Databricks (Pyspark)
- Azure Storage Account
- Azure Data Lake Gen2
- Azure Key vaults












