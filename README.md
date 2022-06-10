# Azure Data Fundamentals DP900

## Data Processing Modes

### Massive Parallel Processing

- Split the processing across multiple compute nodes
- Typically seperate storage and compute
- Examples: Spark, Azure Synapse Analytics

### Batch Pipelines

- Buffer and process data in groups
  - Define how often to run
  - Process huge volumes of data during off-peak hours
  - Typically takes longer to run

### Stream Pipeline

- Process individual records or micro batches of records
  - Continously run
  - Process small amounts of data all day
  - Processing of each stream unit should take only a few seconds or less

### ETL

- Extract, Transform, Load
  - Retrieve data, process, and then store it
  - Data can be from multiple sources
  - Recommended for simple processes
    - Basic data cleaning tasks, de-duplicating data, formatting data
  - Example: Ensure data privacy and compliance
    - Remove sensitive data before it reaches analytical data models
  - Can run each of the phases in parallel
    - While extract is going on, you can transform the data and load it

### ELT

- Extract, Load, Transform
  - Data is stored before it is transformed
  - Uses an iterative approach (multiple steps) to process data
  - Needs a powerful target datastore
    - Target datastore should be able to perform transformations
  - Advantage: Does not use a seperate transformation engine
  - Examples:
    - Hadoop cluster using Hive or Spark
    - Azure Synapse Analytics

## Types of Analytics

There are 5 types of Analytics:

- Descriptive Analytics - What is happening?
  - Based on historical/current data
  - Monitor status of KPIs and generate alerts
  - Example: Generating reports
- Diagnostic Analytics - Why is something happening?
  - Take findings from descriptive analytics and dig deeper
  - Example: Why did sales increase last month?
- Predictive Analytics - What will happen?
  - Predict probability based on historical data
  - Mitigate risk and indentify opportunities
  - Typically use machine learning
  - Example: What will be the future demand?
- Prescriptive Analytics - What action should we take?
  - Use insights from predictive analytics and make data-driven informed decisions
  - Still in early stages
  - Example: What can I do to increase the probability of this course being succesful in the future?
- Cognitive Analytics - Make analytic tools to thing like humans
  - Combine traditional analytics techniques with AI and ML features
  - Examples: Speech to text, text to speech, Video Analysis, Image Analysis, Semantic Analysis of Text

### Azure Analytics Services

- Azure Synapse Analytics
  - End-to-end analytics solutions
  - Data Integration + Enterprise Data Warehouse + Data Analytics
  - Create SQL and Spark pools to analyze data
- Azure Data Factory
  - Fully managed serverless service to build complex data pipelines
  - ETL, ELT, and data integration
- Power BI
  - Create visualization around data
  - Unify data and create BI reports & dashboards

## Big Data

### The 3 V's of Big Data

- Volume
  - Terrabytes to Petabytes to Exabytes
- Variety
  - Structured, Semi-structured, Unstructured
- Velocity
  - Batch or streaming

### Data warehouse vs Data lake

- Data warehouse
  - Petabytes of Storage + Compute
  - Data stored in a format ready for specific analysis.
  - Examples: Teradata, BigQuery (GCP), Redshift (AWS), Azure Synapse Analytics
  - Typically uses specialized hardware
- Data lake
  - Typically retains all raw data compressed
  - Examples: Amazon S3, Google Cloud Storage, Azure Data Lake Storage Gen2
  - Flexibility while saving cost
  - Perform ad-hoc analysis on demand
  - Analytics and intelligence services (even data warehouses) can directly read from the data lake
    - Azure Synapse Analytics, BigQuery (GCP)

### Big Data - Hadoop, Spark, and Databricks

- Apache Hadoop
  - Create datasets with a variety of data
  - Get intelligence
  - Runs on commodity servers with attached storage
  - Large clusters with thousands of nodes but you must manage the clusters yourself
  - Hadoop Distributed File System (HDFS) is the primary storage
  - Data Processing Options
    - MapReduce to process the data utilizing massive parallelization but still does read and writes from disk
      - Java
      - Python
    - HIVE to query data using SQL
    - Apache Spark to process data in-memory, can be 100 times faster than MapReduce, and can run Data Anlytics, Data Processing, and Machine Learning workloads
      - Java
      - Python
      - R
      - SQL
      - Scala
- Databricks
  - Web-based platform for working with Spark
  - Centralized platform for machine learning, streaming analytics, and business intelligence workloads
  - Founded by the creators of Apache Spark
  - Automated cluster management

### Hadoop and Spark Managed Services in Azure

- Azure HDInsight
  - Apache Hadoop managed service
  - Process big data with Hadoop & Spark
- Azure Databricks
  - Premium Spark offering
  - Focused only on running Apache Spark workloads
  - Can consume data from Azure SQL Databases, Event Hubs, & CosmosDB
- Azure Synapse Analytics
  - Apache Spark for Azure Synapse

### Example of Pulling Data into Databricks from External Blob Storage

- <https://docs.microsoft.com/en-us/azure/open-datasets/dataset-us-labor-force?tabs=pyspark#azure-databricks>

### Big Data File Formats

- Apache Parquet
  - Open source columnar storage format
  - High compression becuase of columnar storage
  - Efficient storage for big data workloads
  - First introduced by the Apache Hadoop ecosystem
  - Supported by most Big Data platforms
    - Azure Data Factory & Azure Synapse Analytics Pipelines for Source and Sink
    - Azure Data Lake Storage & Azure Blob Storage can store in Parquet format
    - Azure Synapse Analytics & Azure Databricks can be used to store tabular represenations of data in Parquet format

## Azure Storage Options

### Azure Table Storage

- Supports multi-region read replicas using Read-Access Geo-Redundant-Storage (RA-GRS) redundancy.
  - This enables a readable replica in a secondary region.
  - You cannot write data in the secondary region.

### CosmosDB

- Supports multi-region writes and read replicas.

#### CosmosDB APIs

- Core (SQL) API
  - Work with Documents via SQL syntax
  - Can be used to implement a Key-Value store 
- Cassandra API
  - Compatible with Apache Cassandra a column-family structure database
  - Support SQL syntax
- Gremlin API
  - Graph syntax
- Table API
  - Key-Value data with requests based on a namespace much like retrieving data from Blob Storage
- MongoDB API
  - MongoDB Query Language (MQL) which is object-oriented

## SQL Commands

- Data Manipulation Language (DML)
  - `INSERT`
- Data Definition Language (DDL)
  - `ALTER`

## Business Intelligence

Business Intelligence (BI) allows businesses to acheive better decision making by combining technologies, applications, and processes to collect, analyze, and present business information.  BI combines techniques like data visualization, reporting, and applications like Power BI to help businesses make decisions based on data.

### Power BI

Power BI is a collection of software services, apps, and connectors that work together to turn your unrelated sources of data into coherent, visually immersive, and interactive insights. Your data may be an Excel spreadsheet, or a collection of cloud-based and on-premises hybrid data warehouses. Power BI lets you easily connect to your data sources, visualize and discover what's important, and share that with anyone or everyone you want.

#### The Parts of Power BI

Power BI consists of several elements that all work together, starting with these three basics:

- A Windows desktop application called Power BI Desktop
  - Create complex Reports and Dashboards
- An online SaaS (Software as a Service) service called the Power BI Service
  - Share Reports and Dashboards online
  - Create simple Reports and Dashboards
- Power BI mobile apps for Windows, iOS, and Android devices
  - View shared Reports and Dashboards

These three elements—Power BI Desktop, the service, and the mobile apps—are designed to let you create, share, and consume business insights in the way that serves you and your role most effectively.

Beyond those three, Power BI also features two other elements:

- Power BI Report Builder, for creating paginated reports to share in the Power BI service. Read more about paginated reports later in this article.
- Power BI Report Server, an on-premises report server where you can publish your Power BI reports, after creating them in Power BI Desktop. Read more about Power BI Report Server later in this article.

#### Power BI Roles and Resources

- Power BI Service
  - Business Users
  - Administrators
  - Developers
- Power BI Desktop
  - Report Creators
- Power BI Report Builder
  - Enterprise Report Creators

#### Power BI Workflow

1. Connect to data sources from within the Power BI Desktop applicaton and build a report.
2. Publish that report from Power BI Desktop to the Power BI service and share it.
3. View the Report on mobile devices by business users.
