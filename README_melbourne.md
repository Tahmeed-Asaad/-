
 ## Steps to get the project up and running:  
 #### Prerequisites
   1. A running Spark instance or cluster
   2. Python 3  with pyspark

 
 ### 1. Modify the path to the S3 bucket that you want to read from and write to.
 The main method in the etl.py file contains the variables used for the S3 bucket paths. The dl.cfg file contains the AWS credentials
   1. input_data_song = 'enter-song-data-path-here'
   2. input_data_log = 'enter-log-data-path-here'
   3. output_data = 'enter-destination-path-here'
   4. Modify the AWS credentials in the dl.cfg file as needed
 
 
### 3. ETL pipeline. Run this script    
    python etl.py
 The **etl.py** module contains the methods used in the ETL pipeline.
 Data will be read from the S3 buckets(json) and loaded onto the S3 buckets(parquet) configured above.
 Results will be place into their own folders for songs, artists, users etc. respectively
 
 
### 4. Connect to the desination S3 bucket and check the folder for results    
    
    
---
    
# Data Model
### Tables

There are 5 tables in this data model

##### Dimensions  
* users (user data incl. first name, last name etc.) 
* artists (name, location etc. information about the artists) 
* songs  (song name, length of song etc.)
* time  (constains lookup information for day, hour, week etc.)

##### Facts
* songplay (which user played which song by what artist and when)  


---

### Data analysis can be done on the *song_plays* parquet files.
This table has key information about songs that have been played by the users of the application.

### Examples of queries that can be run against this table are the following.

#### *Which artist has been played the most amount of times in 2018*  

*Using pyspark you can read in the parquet files for from S3*
```python
songplays_table = sparkSession.read.parquet('path-to-song-plays/directory-name.parquet') # get the song_plays data
artist_data = sparkSession.read.parquet('path-to-songs/directory-name.parquet') #get the artist data

song_play_by_artist = songplays_table.filter(songplays_table.year ==  2018).groupBy("artist_id").count().orderBy(col("count").desc()).limit(1)
song_play_by_artist.alias("test") \
.join(artist_data.alias("songs"),song_play_by_artist.artist_id == artist_data.artist_id, "inner") \
.select("songs.artist_name","test.count").show()
```
