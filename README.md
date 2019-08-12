## Project 4: Data Lake with Apache Spark
---
[![Project passed](https://img.shields.io/badge/project-passed-success.svg)](https://img.shields.io/badge/project-passed-success.svg)

### Introduction 
In this project, we try to help one music streaming startup, Sparkify, to move their date warehouse to a data lake. Specifically, I bulid an ETF pipline to extract their data from **S3** and processes them using **Spark**, and loads the data into a new **S3** as a set of *dimensional tables*. This will allow their analytics team to continue finding insights in what songs their users are listening to.

### Dataset 
Datasets used in this project are provided in two public **S3** buckets. One bucket contains info about songs and artists, the second bucket has info concerning actions done by users (which song are listening, etc.. ). The objects contained in both buckets are JSON files.

### Database Schema

I createa a star schema optimized for queries on song play analysis as follows:

![schema](/images/schema.png)

This includes the following tables.

#### Fact Table 
+ **songplays** - records in event data associated with song plays i.e. records with page `NextSong`

#### Dimension Tables
+ **users** - users in the app
+ **songs** - songs in music database
+ **artists** - artists in music database
+ **time** - timestamps of records in **songplays** broken down into specific units

### Spark Process
The ETL job processes the `song files` then the `log files`. The `song files` are listed and iterated over entering relevant information in the artists and the song folders in parquet. The `log files` are filtered by the *NextSong* action. The subsequent dataset is then processed to extract the date, time, year etc. fields and records are then appropriately entered into the `time`, `users` and `songplays` folders in parquet for analysis.


### Project Structure

+ `etl.py` - The ETL to reads data from **S3**, processes that data using **Spark**, and writes them to a new **S3**
+ `dl.cfg` - Configuration file that contains info about AWS credentials
+ `test.ipynb` - test file for `etl.py`
