# Introduction

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a Postgres database with tables designed to optimize queries on song play analysis, and bring you on the project. Your role is to create a database schema and ETL pipeline for this analysis. You'll be able to test your database and ETL pipeline by running queries given to you by the analytics team from Sparkify and compare your results with their expected results. 

# Project Description

In this project, you'll apply what you've learned on data modeling with Postgres and build an ETL pipeline using Python. To complete the project, you will need to define fact and dimension tables for a star schema for a particular analytic focus, and write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.



# Database Schema

For this project we are using the following database schema

## Table Songplays

![carbon](https://user-images.githubusercontent.com/107310236/205324482-68db2877-67d8-4911-8fae-a4b9df0ebab9.png)


## Table Artists
  
![carbon (1)](https://user-images.githubusercontent.com/107310236/205324652-7fa1ed0a-31cd-4b2a-8122-ea8a2537b336.png)


## Table Songs

![carbon (2)](https://user-images.githubusercontent.com/107310236/205324745-5cfdaca1-59f2-4c21-b506-1a9fc1a85464.png)


## Table Time

![carbon (3)](https://user-images.githubusercontent.com/107310236/205324815-bebff0d9-23eb-4ddc-aad7-666402527ab8.png)

## Time Users


![carbon (4)](https://user-images.githubusercontent.com/107310236/205325232-acfc8884-eb09-46de-9e87-283045aa778d.png)



# Process to make it work

## Datasets

To make it work we are working with two datasets(<strong>song_data<strong> & <strong>log_data<strong>)

## Database

- This prject give us few scripts to complete. The one we are going to use to create the database is <strong>create_tables.py<strong>, which will import all the queries which are stored in <strong>sql_queries<strong> and execute them.
  
- All the statements have Primar Keys which will be assigned from the data into the ETL process.
 
## ETL 
  
- This scripts provides the functions to make work the ETL process.
  
### Datasets
  
For each datasets we have different functions which will extract the data and insert them into the different tables.

### Songs Dataset
  
  Execute the function process_song_file on every .json file located on the "data/song_data" folder. This will extract data for the songs and artists tables
  
![carbon (5)](https://user-images.githubusercontent.com/107310236/205325891-f02be64a-3e46-4072-bdc6-b150cf33164a.png)

### Log Dataset
 - To extract the data from this dataset we will need to do something else:

![carbon (9)](https://user-images.githubusercontent.com/107310236/205326561-6d15e3bb-83de-4e47-9180-f3b1e9124867.png)

- To make this easier to process we convert the timestamp value into datatime:
  
![carbon (8)](https://user-images.githubusercontent.com/107310236/205326449-7d4b883e-f8dd-4f65-8e45-01b584b10e69.png)


- To extract the data for the "time" table we use this method:
  
 ![carbon (10)](https://user-images.githubusercontent.com/107310236/205328223-2d36e384-fe64-4107-b878-ac9d19a3dbdc.png)

- And to obtain data for the "users" table we'll use this method:
  
 ![carbon (11)](https://user-images.githubusercontent.com/107310236/205328443-0ab121df-2c0a-415f-9eaa-955bffd217ce.png)



-  Once you have all this steps done, now comes the final step, we have to use the data provided by the "log" json fles and do a search to extract the "song_id" and the "artist_id":
  
  ![carbon (12)](https://user-images.githubusercontent.com/107310236/205328710-025b1076-1ea0-45e3-9613-b15aa69ef7c2.png)


## ETL PROCESS

  Once we have created the database and the tables we can start ETL PROCESS.
  
