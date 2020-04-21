## Introduction

A new music streaming application developed by a startup company called Sparkify. Associated with the application usage is the data of songs and user acitivity.
Data is valuable, in order to gain insights from the collect data of songs and user activities, the data is to be analyzed.

Sparkify's analytical team is keen in determing the user's behavior, the songs that they are listing and the likelihood of liking a song. As per the current configuration of data storage, 
which is in directory of json logs on user activity and as well on songs details, analyzing is a tedious process but with increase in json logs and metadata the difficulty will increase dramatically.

In order to overcome this complexity, creation of database is recommeded which is achieved by data modeling and creation of ETL pipelines.
An optimized STAR schema is needed to be created to analyze:-
* Top trending songs
* Recommendation of songs
* How likely is a user going to subscribe to the application

A Star Schema will have:
* **Fact Table** :- **songplays** 
* **Dimension Tables** :- **users**, **songs**, **artists**, **time**


* **Tables Information** 

**songplays** : records in log data
    
    
| Column Name  | Variable |
| --- | --- |
| songplay_id   | int  |
| start_time    | timestamp  |
| user_id       | int  |
| level         | varchar  |
| song_id       | varchar  |
| artist_id     | varchar  |
| session_id    | int  |
| location      | text  |
| user_agent    | text  |

**users** : users in the app

| Column Name  | Variable |
| --- | --- |
|  user_id  |   int  |
|  first_name  |  varchar  |
|  last_name  |  varchar  |
|  gender  |  char  |
|  level  |  varchar  |

**songs** : songs in music database
| Column Name  | Variable |
| --- | --- |
|  song_id  |   varchar  |
|  title  |  text  |
|  artist_id  |  varchar  |
|  year  |  int  |
|  duration  |  float  |


**artists** :  artists in music database

| Column Name  | Variable |
| --- | --- |
|  artist_id  |   varchar  |
|  name  |  text  |
|  location  |  varchar  |
|  latitude  |  numeric  |
|  longitude  |  numeric  |

**time** :  timestamps of records in songplays broken down into specific units

| Column Name  | Variable |
| --- | --- |
|  start_time  |   timestamp  |
|  hour  |  int  |
|  day  |  int  |
|  week  |  int  |
|  month  |  int  |
|  year  |  int  |
|  weekday  |  varchar  |


## ETL
1. Created **songs**, **artist** dimension tables from extracting songs_data by selected columns.
2. Created **users**, **time** dimension tables from extracting log_data by selected columns.
3. Created the most important table fact table from the dimensison tables and log_data called **songplays**. 

## Installation

Install PostgreSQL database drivers by using the below command
```bash
pip install psycopg2
```
## Usage
1. **sql_queries.py**: contains all SQL queries of the project and this file can be used in multiple files.
2. **create_tables.py**: run this file after writing for creating tables for the project.

      #### Libraries used:
     ```python
     import psycopg2
     from sql_queries import create_table_queries, drop_table_queries
     ```
     #### Functions and its importance:
     **create_database**: This function helps in droping existing database, create new database and return the connection.

    **drop_tables**: Used to drop the existing tables.

    **create_tables**: This helps in creating above mentioned fact table and dimension tables.
3. **etl.ipynb**: reads and processes a single file from song_data and log_data and loads the data into your tables. This notebook contains detailed instructions on the ETL process for each of the tables.
4. **etl.py**:   read  and process files from song_data and log_data and load them to tables. 
    #### Libraries used:
    ```python
    import os
    import glob
    import psycopg2
    import pandas as pd
    from sql_queries import *
    import json
     ```
    #### Functions and its importance:
   
    **process_song_file**: This function is used to read the song file and insert details with selected columns into song and artist dimension table.

    **process_log_file**: read one by one log file and insert details with selected columns into user, time and songplays tables.
   
    **process_data**: collect all the file paths and call the above two function and show status of files processed.

    **main**: used to call the process_data function.

5. **test.py**: displays the first few rows of each table to let you check your database.

## execute files in the below order each time before pipeline.

   1. create_tables.py
      ```python
         $ python3 create_tables.py
   2. etl.ipynb/et.py
      ```python
         $ python3 etl.py
   3. test.ipynb
