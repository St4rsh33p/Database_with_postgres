# Introduction

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a Postgres database with tables designed to optimize queries on song play analysis, and bring you on the project. Your role is to create a database schema and ETL pipeline for this analysis. You'll be able to test your database and ETL pipeline by running queries given to you by the analytics team from Sparkify and compare your results with their expected results. 

# Project Description

In this project, you'll apply what you've learned on data modeling with Postgres and build an ETL pipeline using Python. To complete the project, you will need to define fact and dimension tables for a star schema for a particular analytic focus, and write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.



# Database Schema

For this project we are using the following database schema

## Table Songplays

- ![image](https://user-images.githubusercontent.com/107310236/205116093-b08b3df3-bc47-4886-a6e8-99a2655d0036.png)

## Table Artists
  
-  ![image](https://user-images.githubusercontent.com/107310236/205115853-a6c890c8-ed22-422c-bef1-dbf1a35b1b21.png)  

## Table Songs

- ![image](https://user-images.githubusercontent.com/107310236/205116330-9bcd2228-c181-47bf-83b4-f08662a8d187.png)

## Table Time

- ![image](https://user-images.githubusercontent.com/107310236/205116429-631af852-7788-4a11-9e7c-bd89fa9776e0.png)

## Time Users

- ![image](https://user-images.githubusercontent.com/107310236/205116507-0da5211e-6ebe-4548-872b-2a17f6032931.png)



## Process to make it work

### Datasets

To make it work we are working with two datasets(<strong>song_data<strong> & <strong>log_data<strong>)

### Database

- This prject give us few scripts to complete. The one we are going to use to create the database is <strong>create_tables.py<strong>, which will import all the queries which are stored in <strong>sql_queries<strong> and execute them.
  
- All the statements have Primar Keys which will be assigned from the data into the ETL process.
 
### ETL 
  
- This scripts provides the functions to make work the ETL process.
  
### Datasets
  
For each datasets we have different functions which will extract the data and insert them into the different tables.

#### Songs Dataset
  
  Execute the function process_song_file on every .json file located on the "data/song_data" folder. This will extract data for the songs and artists tables
  
  ![image](https://user-images.githubusercontent.com/107310236/205120497-a315ebd9-05de-4ffd-9a79-a3a4bf02b7d6.png)

#### Log Dataset
  To extract the data from this dataset we will need to do something else:

  ![image](https://user-images.githubusercontent.com/107310236/205300931-4aeebf03-7687-4e2e-8254-90546b58ed00.png)
  
  to make this easier to process we convert the timestamp value into datatime:
  
  ![image](https://user-images.githubusercontent.com/107310236/205301085-cfb3a3d5-0477-4002-b297-3286165ebcf5.png)
  
  to extract the data for the "time" table we use this method:
  
  ![image](https://user-images.githubusercontent.com/107310236/205301398-6f568b01-91bb-4b67-b963-816c880ee85d.png)
  
  and to obtain data for the "users" table we'll use this method:
  
  ![image](https://user-images.githubusercontent.com/107310236/205301638-746398cf-0f29-40aa-b3e1-323ea12bef4c.png)


  Once you have all this steps done, now comes the final step, we have to use the data provided by the "log" json fles and do a search to extract the "song_id" and the "artist_id":
  
  ![image](https://user-images.githubusercontent.com/107310236/205302201-d65c4abe-5241-4273-ab85-84986c4b9df4.png)


## ETL PROCESS

  Once we have created the database and the tables we can start ETL PROCESS.
  
