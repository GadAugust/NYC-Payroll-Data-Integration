# NYC Payroll Data Integration Capstone Project

## Description of the Project

The City of New York is undertaking a project to integrate payroll data across all its agencies. This project aims to develop a Data Analytics platform with two primary objectives:
- **Financial Resource Allocation Analysis**: Analyze how the City's financial resources are allocated and how much of the City's budget is devoted to overtime.
- **Transparency and Public Accessibility**: Make the data available to the public to show how the City's budget is being spent on salary and overtime pay for all municipal employees.

## Tools Used

- **Azure Blob Storage**
  - For storing raw data files.
- **Blob Container**
  - For organizing the blob storage.
- **Azure Data Factory**
  - For creating and managing ETL pipelines.
- **Azure SQL Database**
  - For staging and processing data.
- **SQL Server**
  - For hosting the final data warehouse.
- **Power BI**
  - For data visualization and reporting.

## Warehouse Schema

### The Datawarehouse Grains And Dimensional Model
[The datawarehouse Defined Grains and Model](https://github.com/GadAugust/NYC-Payroll-Data-Integration/blob/main/NYCDataModel.drawio.pdf)

### Data Architecture
[Data Architecture of the pipeline](NYCDataArchitecture.pdf)



## Step-by-Step Description of the Processes Involved in Executing the Project

### ETL Pipeline Process

1. **Data Source**
   - Remote folder with CSV files containing Employee master data and monthly payroll data from various City Agencies.
     [Data Source](NYC_Data_Set.zip)
2. **Data Processing**
   - Steps to process the data and load it into the data warehouse.
   - Utilize Azure Blob Storage and Blob Container to store and organize the data.
   - Use Azure Data Factory (ADF) to create ETL pipelines for data ingestion.
   - Load data into Azure SQL Database for staging and initial processing.
3. **Data Aggregation**
   - Create aggregate tables in the SQL Server to facilitate easy analysis of key business questions.
4. **Quality Assurance**
   - Monitor and ensure the quality and consistency of data throughout the pipeline.
5. **Public Access**
   - Implement limited access privileges to enable public access to the NYC Data warehouse.
   - Use Power BI for data visualization and reporting.
