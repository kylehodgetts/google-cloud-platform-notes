# Big Data and IoT

[Data lifecycle | Cloud Architecture Center | Google Cloud](https://cloud.google.com/architecture/data-lifecycle-cloud-platform)

![Screenshot 2021-09-09 at 11.06.07.png](Big%20Data%20and%20IoT%20daba3c83041645e490048c5042a6d1cd/Screenshot_2021-09-09_at_11.06.07.png)

## Cloud IoT Core

- Global
- Coneect manage and ingest data from devices globally

![Screenshot 2021-09-09 at 11.07.54.png](Big%20Data%20and%20IoT%20daba3c83041645e490048c5042a6d1cd/Screenshot_2021-09-09_at_11.07.54.png)

- Device Manager handles device identity, auth, config and control
- Protocol Bridge publishes incoming telemetry to Cloud pub sub for processing
- Connect securely using MQTT or HTTPS protocols
- CA signed certificates can be used to verify device ownership on first connect
- 2-way devices comms enables config and firmware updates
- Device shadows enable querying & making control changes while devices offline
- Pay per MB of data exchanged with devices; no per device charge

## Cloud Pub/Sub

[Cloud Pub/Sub | Google Cloud](https://cloud.google.com/pubsub/)

- Global
- Infinitely scalable, at-least-once messaging for ingestion, decoupling etc
    - Glue that links everything else together in terms of data flow

![Screenshot 2021-09-09 at 11.10.54.png](Big%20Data%20and%20IoT%20daba3c83041645e490048c5042a6d1cd/Screenshot_2021-09-09_at_11.10.54.png)

- publish and consume from anywhere with consistent latency
    - based on load balancer, forwarding traffic to best region
- Messages upto 10MB
- undelivered ones stored for 7 days
    - No DLQ
- Push mode delivers via HTTPS to endpoint succeeds on HTTP success status code (2XX)
    - Slow start algorithm ramps up on success and backs off & retries on failures
- Pull mode delivers messages to requesting clients and waits for ACK to delete
    - Lets client set consumption rate
    - supports batching and long polling (keep open connection for some time until a message arrives)
- Pay for data volume
    - min 1KB per publish, push, pull request (not by message)

## Cloud Dataprep

[](https://cloud.google.com/dataprep/)

- Global
- Visually explore, clean and prepare data for analysis without running servers
- "Data Wrangling" (ad-hoc ETL) for BAs, no IT pros
- managed version of Trifacta Wrangler, managed by Trifacta
- Source data from GCS, BQ or file upload - formatted in CSV, JSON or relational
- Auto detects schemas, datatypes, possible joins and various anomalies
- Pay for underlying Dataflow job, plus management overhead charge
- Pay for other accessed services (GCS, BQ)

## Cloud Dataproc

[Dataproc | Google Cloud](https://cloud.google.com/dataproc/)

- Zonal
- batch MapReduce processing via configurable, managed Spark & Hadoop clusters
- Handles scale (adding and removing nodes) while running jobs
- Integrates with GCS, BQ, BigTable and some StackDriver services
- Image versioning to switch between versions of Spar, Hadoop etc
- Pay for underlying GCE servers in cluster - optionall preemptible (1 node should NOT be premptible)
- Pay Dataproc management fee per vCPU-hour in cluster
- Best for moving existing Spark, Hadoop setups to GCP
    - Prefer Dataflow for new data processing pipelines

## Cloud Dataflow

[Dataflow | Google Cloud](https://cloud.google.com/dataflow/)

[https://cloud.google.com/blog/products/gcp/introducing-cloud-dataflow-shuffle-for-up-to-5x-performance-improvement-in-data-analytic-pipelines](https://cloud.google.com/blog/products/gcp/introducing-cloud-dataflow-shuffle-for-up-to-5x-performance-improvement-in-data-analytic-pipelines)

- Zonal
- Smartly autoscaled & fully managed batch or stream MapReduce-like processing
- Released as open-source Apache Beam
- Autoscales & dynamically redistributes lagging work, mid-job to optimize runtime
- Integrated with Pub Sub, Datastore, BQ, BigTable, Cloud ML, StackDriver etc
- Dataflow Shuffle service for batch offloads Shuffle ops from workers for big gains
- Pay for underlying worker GCE via consolidated charges
    - Pay per second for vCPUs, RAM GBs PD/PD-SSD (Persistent Disk) more for streaming
- Dataflow Shuffle charged for time per GB used

## Cloud Datalab

[Datalab documentation | Cloud Datalab Documentation | Google Cloud](https://cloud.google.com/datalab/docs)

[https://jupyter.org/](https://jupyter.org/)

- Regional
- Interactive tool for data exploration, analysis, visualisation and machine learning
- Uses Jupyter Notebook
- Supports iterative development of data analysis algorithms in Python, SQL, ~JS
- Pay for GCE / GAE instance hosting and storing (on PD) your notebooks
- Pay for any other resources accessed (BigQuery)

## Cloud Data Studio

[Business Intelligence Modernization | Google Cloud](https://cloud.google.com/solutions/business-intelligence)

- Data data viz tool for dashboard and reporting
- Meaningful data stories / presentations enable better business decision making
- Data sources inc
    - BigQuery
    - Cloud SQL
    - Other MySQL
    - Google Sheets
    - Google Analytics
    - Analytics 360
    - AdWords
    - DoubleClick
    - Youtube Channels
- Visualisations include
    - Time series
    - bar charts
    - Pie charts
    - Tables
    - heat maps
    - geo maps
    - score cards
    - scatter charts
    - bullet charts
    - area charts
- Quick start templates
    - Custom options for impactful finish
- Familiar G Suite sharing and real-time collab
- Pay only for services accessed

## Cloud Genomics

[Cloud Life Sciences | Google Cloud](https://cloud.google.com/life-sciences)

- Global
- Store and process Genomes and related experiments
- Query complete genomic information of large research projects in seconds
- Process many genomes and experiments in parralel
- Open industry standards (e.g. from Global Alliance for Genomics and Health)
- Supports Requester Pays sharing