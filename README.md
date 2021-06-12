# Project: Data modeling with Postgres

This Data Engineering Nanodegree project creates a postgres database `sparkifydb` for a music app, Sparkify.

This project uses Song Dataset
The first dataset is a subset of real data from the [https://labrosa.ee.columbia.edu/millionsong/] (Million Song Dataset).
Each file is in JSON format and contains metadata about a song and the artist of that song. 
## purpose
The purpose of the database is to model song and log datasets (originaly stored in JSON format) with a star schema optimised for queries on song play analysis.


## Schema design and ETL pipeline
-----
Extract, transform, load processes in **etl.py** populate the **songs** and **artists** tables with data derived from the JSON song files, `data/song_data`. Processed data derived from the JSON log files, `data/log_data`, is used to populate **time** and **users** tables. A `SELECT` query collects song and artist id from the **songs** and **artists** tables and combines this with log file derived data to populate the **songplays** fact table.

![ER Diagram](/data/sparkifydb_erd.png?raw=true "ER Diagram")


# star schema
The star schema has 1 *fact* table (songplays), and 4 *dimension* tables (users, songs, artists, time). `DROP`, `CREATE`, `INSERT`, and `SELECT` queries are defined in **sql_queries.py**. **create_tables.py** uses functions `create_database`, `drop_tables`, and `create_tables` to create the database sparkifydb and the required tables.

![Star Schema](/data/Song_ERD.png?raw=true "Star Schema")

Using the song and log datasets, you'll need to create a star schema optimized for queries on song play analysis. This includes the following tables.

### -Fact Table
- songplays - records in log data associated with song plays i.e. records with page NextSong\n
    songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
#### -Dimension Tables
- users - users in the app\n
    user_id, first_name, last_name, gender, level
- songs - songs in music database\n
    song_id, title, artist_id, year, duration
- artists - artists in music database\n
    artist_id, name, location, latitude, longitude
- time - timestamps of records in songplays broken down into specific units\n
    start_time, hour, day, week, month, year, weekday

## Running the Python Scripts

At the terminal:

1. ```python create_tables.py```
2. ```python etl.py```

In IPython:

1. ```run create_tables.py```
2. ```run etl.py```

## Description of Files

### Directory: data/log_data

This directory contains a collection of JSON log files. These files are used to populate our Fact table - Song Plays - and to populate the Dimension tables for Users and Time.

### Directory: data/song_data

This directory contains a collection of Song JSON files. These files are used to populate Dimension tables for Songs and Artists.

## create_tables.py

This Python script recreates the database and tables used to storethe data.

## etl.ipynb

A Python Jupyter Notebook that was used to initially explore the data and test the ETL process.

## etl.py

This Python script reads in the Log and Song data files, processes and inserts data into the database.

## requirements.txt

A list of Python modules used by this project.

## sql_queries.py

A Python script that defines all the SQL statements used by this project.

## test.ipynb

A Python Jupyter Notebook that was used to test that data was loaded properly.