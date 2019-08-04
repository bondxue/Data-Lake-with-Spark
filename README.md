### Project 4: Data Lake with Apache Spark

#### Introduction 
In this project, we try to help one music streaming startup, Sparkify, to move their date warehouse to a data lake. Specifically, I bulid an ETF pipline to extract their data from **S3** and processes them using **Spark**, and loads the data back into **S3** as a set of *dimensional tables*. This will allow their analytics team to continue finding insights in what songs their users are listening to.

#### Dataset 
Datasets used in this project are provided in two public **S3** buckets. One bucket contains info about songs and artists, the second bucket has info concerning actions done by users (which song are listening, etc.. ). The objects contained in both buckets are JSON files.

### Database Schema

I createa a star schema optimized for queries on song play analysis. This includes the following tables.

#### Fact Table 
+ **songplays** - records in event data associated with song plays i.e. records with page `NextSong`

#### Dimension Tables
+ **users** - users in the app
+ **songs** - songs in music database
+ **artists** - artists in music database
+ **time** - timestamps of records in **songplays** broken down into specific units



### Project Structure

+ `etl.py` - The ETL to reads data from **S3**, processes that data using **Spark**, and writes them back to **S3**
+ `dl.cfg` - Configuration file that contains info about AWS credentials