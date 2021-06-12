# Project: Data modeling with Postgres

This Data Engineering Nanodegree project creates a postgres database `sparkifydb` for a music app, Sparkify.

This project uses Song Dataset
The first dataset is a subset of real data from the [https://labrosa.ee.columbia.edu/millionsong/] (Million Song Dataset).
Each file is in JSON format and contains metadata about a song and the artist of that song. 
## purpose
The purpose of the database is to model song and log datasets (originaly stored in JSON format) with a star schema optimised for queries on song play analysis.

- ETL
- Json to Postgres\

## Schema design and ETL pipeline
-----

![ER Diagram](/data/sparkifydb_erd.png?raw=true "ER Diagram")

![](data/sparkifdb_erd.png?raw=true)

Schema for Song Play Analysis
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
