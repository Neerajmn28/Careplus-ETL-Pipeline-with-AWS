# Automated ETL Pipeline on AWS (S3 → Glue → Redshift)

### Project Overview
This project implements a fully automated, incremental ETL pipeline on AWS to process support ticket and application log data.
The pipeline is event-driven, scalable, and production-ready, using managed AWS services.
New data uploaded to Amazon S3 automatically triggers processing, transformation, and loading into Amazon Redshift for analytics.


### AWS Services Used
* Amazon S3 – Raw & processed data storage
* AWS Lambda – Event-driven automation
* AWS Glue – ETL processing & transformations
* AWS Glue Crawler – Metadata cataloging
* AWS Glue Data Catalog – Schema management
* Amazon Redshift – Data warehouse & analytics
* AWS IAM – Secure access control

### ETL Workflow
1️⃣ Data Ingestion
Raw support ticket and log files are uploaded to S3
Files follow a date-based naming convention for incremental processing

2️⃣ Automation Trigger
S3 Event Notification triggers a Lambda function
Lambda starts the AWS Glue ETL job dynamically

3️⃣ Data Transformation (Glue)
The Glue job performs:
Schema changes
Column renaming
Null value removal
Filtering invalid records
SQL-based transformations
Data type normalization
Deduplication

4️⃣ Processed Data Storage
Transformed data is written back to S3 in Parquet format
Optimized for analytics and Redshift ingestion

5️⃣ Metadata Cataloging
Glue Crawler scans processed S3 data
Creates/updates tables in Glue Data Catalog

6️⃣ Data Warehouse Load
Data is loaded incrementally into Amazon Redshift
Enables fast analytical queries


### Incremental Processing Strategy
* Event-driven ingestion (S3 triggers Lambda)
* Only newly uploaded files are processed
* No full reloads or truncations
* Prevents duplicate data ingestion
* Reduces compute cost and processing time

### Security & Permissions
* IAM roles follow least privilege principle
* Lambda permissions:
* Glue job execution
* S3 read access
* Glue permissions:
* S3 read/write
* Data Catalog access
* Redshift access controlled via IAM roles

Key Features
* Fully automated ETL
* Event-driven architecture
* Incremental data loads
* Scalable & serverless
* Analytics-ready data model
* Production-grade AWS design
