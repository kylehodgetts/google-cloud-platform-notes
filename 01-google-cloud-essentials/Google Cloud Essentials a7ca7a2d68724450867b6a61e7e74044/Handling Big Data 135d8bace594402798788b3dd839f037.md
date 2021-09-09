# Handling Big Data

## Warehousing Data with BigQuery

- Fully managed data warehouse for big data
- Near real-time interactive analysis of massive datasets
- Analyze terabytes of data in seconds
- Standard SQL supported
- Storage and computing handled and billed seperately
- Query public or commercial data sets with your own
- External services queries: Cloud Storage, Cloud Bigtable & Google Drive
- Automatic data replication
- Modify data with Data Definition Language
- Use cases: real-time inventory, predictive digital marketing, analytical events
- No transactions
- Petabytes+ of capacity
- Unit size: 10 MB row

## Processing Data with Cloud Dataflow

- Fully managed service for creating pipelines to process data
- Based on Apache Beam
- Processes data on multiple machines in parallel
- Handles both streaming (live) and batch (archived) data
- No instances or clusters to establish: serverless
- Easy replication of services with templates:
    - No need to re-complile code before processing pipeline
    - Execute pipeline without dev environment and its dependencies
    - Can customize execution with template parameters
    - Can be executed via console or gcloud command
- Best option if no current implementation with Apache Hadoop or Spark
- Use cases: analytical dashboards, forecasting sales trends, ETL operations

## Coordinating Clusters with Cloud Dataproc

- Fully managed cluster data processing service
- Compatible with Apache Hadoop, Spark and Hive
- Move existing projects or pipelines without redevelopment
- Boasts fast cluster creation - 90 seconds vs 5 - 30 minutes
- Can scale clusters up and down without stopping the job
- Can switch to different versions of Hadoop, Spark and others
- Workflow templates recently added
    - Create template, add job and instantiate templates
        - Workflow 1: Create cluster, runs jobs and deletes cluster
        - Workflow 2: Works with existing cluster and runs jobs
- Similar to Cloud Dataflow
    - Both process data
    - Both handle batch and streaming data

## Messaging through Cloud Pub Sub

- Fully managed messaging middleware service
- Allows secure and highly available messages between independent apps
- Works with both Google Cloud and external services
- Full range of communication
    - 1 —> M
    - M —> 1
    - M —> M
- Both push and pull options
- Messages encrypted and HIPAA compliant
- Use cases: streaming data, event notifications, async workflows etc

## Examining more Big Data Services

### Cloud Datalab

- Interactive data analysis and machine learning environment
- Packaged as a container and runs in a VM instance
- Based on Jupyter notebooks
- Notebooks:
    - Contain code, docs in markdown and code results
    - Code results can be test, image, JavaScript or HTML
    - Can be shared with team members
    - Collection of cells containing code or markdown

### Cloud Data Studio

- Interactive report and big data visualizer
- Creates dashboards, charts and tables
- Connects to Cloud BigQuery, Cloud Spanner, Cloud SQL, and Cloud Storage
- Stores shareable files on Google Drive
- Basic process is three steps:
    - Connect to data source
    - Visualize data in report
    - Share report