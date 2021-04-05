# Goodreads-Data-Pipeline

## An end-to-end ETL pipeline to capture and process real-time books data

## Tools Used - AWS, Python, Redshift, Spark, Airflow, PostgreSQL

- Captured real-time books data and moved it to S3 bucket; wrote Spark ETL jobs to post the data to Redshift staging tables
- Designed an Airflow DAG to run for every 10 minutes to ensure data quality and send emails in case of pipeline failures
- Successfully tested the execution flow of the data pipeline by processing 11.4 GB of mock-up data every 10 minutes
