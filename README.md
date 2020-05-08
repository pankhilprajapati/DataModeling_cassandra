
# Project: Data Modeling with Cassandra

The goal of this project is to define a data model that will help our data scientists answer questions about user activity. In this case, we are working with a NoSQL database, Apache Cassandra, which means we have to be especially intentional in our data modeling. We first need to understand what queries our data scientists would like to run, and then we can design tables to fit those queries. We will be aiming for "1 query, 1 table".

### File Overview
- event_data/ - contains our data for user sessions in the streaming app in csv format. files are partitioned by day.
- images - contains an image of what our data looks like after an ETL process
 - data_modeling.ipynb - Has two parts:
   ETL pipeline for processing the event files and compiling them into a single csv with the desired columns
   Data modeling examples that show three queries and the creation of three tables to serve those queries
   Note: the data is not included in this repo.

To run this, you simply need to open the Notebook and run all cells.

### Data Overview
![Data](images/image_event_datafile_new.jpg)


### Work done

1. Give me the artist, song title and song's length in the music app history that was heard during  sessionId = 338, and itemInSession  = 4

- first creating the table "songs" which contains the column names "artist_name", "song_title", "song_len", "session_id"and  "item_in_session"
  and assign the primary key as sesson_id and clustering column as item_in_session (unique)
- Inserting the data using the csv 
- selecting the desired output using where clause

2. Give me only the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182

- first creating the table "artists" which contains the column names "artist_name", "song_title", "first_name", "last_name", "user_id", "session_id"and  "item_in_session"
  and assign the primary key as user_id and clustering column session_id ( for uniqueness) , item_in_session (sort by)
- Inserting the data using the csv 
- selecting the desired output using where clause

3. Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own'

- first creating the table "artists" which contains the column names "artist_name", "song_title", "first_name", "last_name", "user_id", "session_id"and  "item_in_session"
  and assign the primary key as song_title (for searching) and clustering column user-id ( for uniqueness)

- Inserting the data using the csv 
- selecting the desired output using where clause

### Acknowledge 

Udacity
