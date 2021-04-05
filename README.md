# Goodreads-Data-Pipeline

## An end-to-end ETL pipeline to capture and process real-time books data

## Tools Used - AWS, Python, Redshift, Spark, Airflow, PostgreSQL

## ETL Flow

- Data Collected from the API is moved to landing zone s3 buckets.
- ETL job has s3 module which copies data from landing zone to working zone.
Once the data is moved to working zone, spark job is triggered which reads the data from working zone and apply transformation. Dataset is repartitioned and moved to the Processed Zone.
- Warehouse module of ETL jobs picks up data from processed zone and stages it into the Redshift staging tables.
- Using the Redshift staging tables and UPSERT operation is performed on the Data Warehouse tables to update the dataset.
- ETL job execution is completed once the Data Warehouse is updated.
- Airflow DAG runs the data quality check on all Warehouse tables once the ETL job execution is completed.
- Airflow DAG has Analytics queries configured in a Custom Designed Operator. These queries are run and again a Data Quality Check is done on some selected Analytics Table.
- Dag execution completes after these Data Quality check.

## Goodreads Pipeline DAG
<img width="953" alt="goodreads_dag" src="https://user-images.githubusercontent.com/66754032/113553315-34ac5980-95bd-11eb-8504-a22b414da4c0.png">

## DAG View
<img width="946" alt="DAG" src="https://user-images.githubusercontent.com/66754032/113553531-88b73e00-95bd-11eb-85ff-e701309accf7.png">

