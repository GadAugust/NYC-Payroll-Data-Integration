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

1. **[Data Source](NYC_Data_Set.zip)**
   - Remote folder with CSV files containing Employee master data and monthly payroll data from various City Agencies.
    

## Moving Data to Staging Layer

### Steps on How I Dynamically Built and Optimized the Pipeline

1. **Open Azure Data Factory (ADF) Data Studio**:
   - Launch the ADF Data Studio to start building and managing your data pipelines.

2. **Use Get Metadata Activity**:
   - Utilize the Get Metadata activity to retrieve metadata information about data stored in the container. This includes obtaining properties and details of the data for further processing within the data pipeline.

3. **Use Conditional Activity Foreach**:
   - Employ the Foreach activity to loop through child items retrieved by the Get Metadata activity.
   - Configure a Copy Data activity (specifying the source and sink) within the Foreach loop.
   - Use parameters and dynamic content to ensure the pipeline processes each item it loops through dynamically.
   - This setup allows the pipeline to copy data for each item to the staging layer efficiently and dynamically.

### Detailed Steps

1. **Open ADF Data Studio**:
   - Navigate to the Azure portal.
   - Open Azure Data Factory.
   - Access the Data Studio interface to start designing your pipeline.

2. **Get Metadata Activity**:
   - Drag the Get Metadata activity onto the pipeline canvas.
   - Configure the Get Metadata activity to point to the container where your data is stored.
   - Specify the fields you want to retrieve, such as `Child Items` and `Last Modified`.

3. **Foreach Activity**:
   - Drag the Foreach activity onto the pipeline canvas.
   - Inside the Foreach activity, set the items to loop through using the output of the Get Metadata activity.
   - Configure the settings to loop through each child item dynamically.

4. **Copy Data Activity**:
   - Within the Foreach activity, drag a Copy Data activity.
   - Configure the source dataset to point to the item currently being processed in the loop.
   - Set the sink dataset to point to the staging layer.
   - Use parameters and dynamic content to ensure the source dynamically changes with each iteration of the loop.

5. **Optimize the Pipeline**:
   - Ensure the pipeline is optimized for performance by monitoring execution times and making necessary adjustments.
   - Validate and debug the pipeline to ensure it works correctly and efficiently.

### Visual Representation
![WhatsApp Image 2024-06-28 at 11 05 10](https://github.com/GadAugust/NYC-Payroll-Data-Integration-Pipeline/assets/81167692/57640b24-8fdd-4f69-809f-9ba926931eaf)



3. **Data Aggregation**
   - Create aggregate tables in the SQL Server to facilitate easy analysis of key business questions.
4. **Quality Assurance**
   - Monitor and ensure the quality and consistency of data throughout the pipeline.
5. **Public Access**
   - Implement limited access privileges to enable public access to the NYC Data warehouse.
   - Use Power BI for data visualization and reporting.
