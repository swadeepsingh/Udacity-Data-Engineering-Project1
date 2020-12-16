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

songplays - records in log data associated with song plays i.e. records with page NextSong

songplay_id, 
start_time,
user_id, 
level, 
song_id, 
artist_id, 
session_id, 
location, 
user_agent

## Dimension Tables

users - users in the app

user_id, 
first_name, 
last_name, 
gender, 
level

songs - songs in music database

song_id, 
title, 
artist_id, 
year, 
duration

artists - artists in music database

artist_id, 
name, 
location, 
latitude, 
longitude

time - timestamps of records in songplays broken down into specific units

start_time, 
hour, 
day, 
week, 
month, 
year, 
weekday

# Run

1. open terminal and 
2. run "python create_tables.py"
3. run "python etl.py"
