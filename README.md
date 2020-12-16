# Project: Data Modeling with Postgres

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.


# Description

The project aims to:

1. create a Postgres database with tables designed to optimize queries on song play analysis,  
2. data modeling with Postgres (define fact & dimension tables for a star schema),
3. write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.

# Dataset

Data is currently collected for song and user activities, in two directories: data/log_data and data/song_data, using JSON files.

# Schema
open terminal and run: "psql -h 127.0.0.1 -d sparkifydb -U student"

then in postgres db terminal run "\d+ _table_name_" to get the schema of that table


## Fact Table

### songplays - records in log data associated with song plays i.e. records with page NextSong

|   Column    |            Type             | Nullable |
| ----------- | --------------------------- | -------- |
| songplay_id | integer                     | not null |
| start_time  | timestamp without time zone | not null |
| user_id     | integer                     | not null |
| level       | character varying           | not null |
| song_id     | character varying           |          |
| artist_id   | character varying           |          |
| session_id  | integer                     | not null |
| location    | character varying           | not null |
| user_agent  | character varying           | not null |

Primary key: songplay_id

## Dimension Tables

### users - users in the app

|   Column   |       Type        | Nullable |
| ---------- | ----------------- | -------- |
| user_id    | integer           | not null |
| first_name | character varying | not null |
| last_name  | character varying | not null |
| gender     | character         | not null |
| level      | character varying | not null |

Primary key: user_id

### songs - songs in music database

|  Column   |         Type          | Nullable |
| --------- | --------------------- | -------- |
| song_id   | character varying     | not null |
| title     | character varying     | not null |
| artist_id | character varying     | not null |
| year      | integer               | not null |
| duration  | double precision      | not null |

Primary key: song_id

### artists - artists in music database

|  Column   |         Type          | Nullable |
| --------- | --------------------- | -------- |
| artist_id | character varying     | not null |
| name      | character varying     | not null |
| location  | character varying     | not null |
| latitude  | double precision      |          |
| longitude | double precision      |          |

Primary key: artist_id

### time - timestamps of records in songplays broken down into specific units

|   Column   |            Type             | Nullable |
| ---------- | --------------------------- | -------- |
| start_time | timestamp                   | not null |
| hour       | integer                     | not null |
| day        | integer                     | not null |
| week       | integer                     | not null |
| month      | integer                     | not null |
| year       | integer                     | not null |
| weekday    | integer                     | not null |


# Run

1. open terminal and 
2. run "python create_tables.py"
3. run "python etl.py"
