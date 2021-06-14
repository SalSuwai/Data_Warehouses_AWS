## Data_Warehouses_AWS project summary:

applying data warehouses tools and AWS to build an ETL pipeline for a database hosted on Redshift. loading data from AWS S3 bucket to staging tables on Redshift and executing SQL statements that create the analytics tables from these staging tables.

----

#Project: Data Warehouse

####Introduction

A music streaming startup, Sparkify, has grown their user base and song database and want to move their processes and data onto the cloud. Their data resides in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.


As their data engineer, you are tasked with building an ETL pipeline that extracts their data from S3, stages them in Redshift, and transforms data into a set of dimensional tables for their analytics team to continue finding insights in what songs their users are listening to. You'll be able to test your database and ETL pipeline by running queries given to you by the analytics team from Sparkify and compare your results with their expected results.


####Project Description

In this project, we'll apply data warehouses tools and AWS to build an ETL pipeline for a database hosted on Redshift. To complete the project, we will need to load data from S3 to staging tables on Redshift and execute SQL statements that create the analytics tables from these staging tables.


##PROJECT DATASETS :

(**note**): all the datasets are in a AWS s3 from udacity located.

SONG dataset:

song_data/A/B/C/TRABCEI128F424C983.json
song_data/A/A/B/TRAABJL12903CDCF1A.json

LOG dataset:
log_data/2018/11/2018-11-12-events.json
log_data/2018/11/2018-11-13-events.json

    Song Dataset
    
The first dataset is a subset of real data from the Million Song Dataset. Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. For example, here are filepaths to two files in this dataset.

    Log Dataset
    
The second dataset consists of log files in JSON format generated by this event simulator based on the songs in the dataset above. These simulate app activity logs from an imaginary music streaming app based on configuration settings.


DATA SCHEMA : 

We will first load the data into two staging tables called staging_events and staging_songs from the data sets residing in a S3  bucket.
then we'll use STAR SCHEMA as main schema for this project with a fact table called songplays and four dimention tables called [users , songs, artists , time ], getting data to insert it in these tables will be from our two staging tables. 

table attributes:

+ staging tables 

staging_events:

        artist              VARCHAR,
        
        auth                VARCHAR,
        
        firstName           VARCHAR,
        
        gender              VARCHAR,
        
        itemInSession       INTEGER,
        
        lastName            VARCHAR,
        
        length              FLOAT,
        
        level               VARCHAR,
        
        location            VARCHAR,
        
        method              VARCHAR,
        
        page                VARCHAR,
        
        registration        FLOAT,
        
        sessionId           INTEGER,
        
        song                VARCHAR,
        
        status              INTEGER,
        
        ts                  TIMESTAMP,
        
        userAgent           VARCHAR,
        
        userId              INTEGER 
        


---------------------------------------------------
staging_songs:

        num_songs           INTEGER,
        
        artist_id           VARCHAR,
        
        artist_latitude     FLOAT,
        
        artist_longitude    FLOAT,
        
        artist_location     VARCHAR,
        
        artist_name         VARCHAR,
        
        song_id             VARCHAR,
        
        title               VARCHAR,
        
        duration            FLOAT,
        
        year                INTEGER
        
        
        
 --------------------------------------------------
 
 +final tables
 
 
 songplays:
 
        songplay_id         INTEGER         IDENTITY(0,1)   PRIMARY KEY,    # Which is a SERIAL attribute.
        
        start_time          TIMESTAMP,
        
        user_id             INTEGER ,
        
        level               VARCHAR,
        
        song_id             VARCHAR,
        
        artist_id           VARCHAR ,
        
        session_id          INTEGER,
        
        location            VARCHAR,
        
        user_agent          VARCHAR
 
 --------------------------------------------------
 
 
 users:
 
        user_id             INTEGER PRIMARY KEY,
        
        first_name          VARCHAR,
        
        last_name           VARCHAR,
        
        gender              VARCHAR,
        
        level               VARCHAR
    
_______________________________________________
    
    
songs :

        song_id             VARCHAR PRIMARY KEY,
        
        title               VARCHAR ,
        
        artist_id           VARCHAR ,
        
        year                INTEGER ,
        
        duration            FLOAT

------------------------------------------------

artists:

        artist_id           VARCHAR  PRIMARY KEY,
        
        name                VARCHAR ,
        
        location            VARCHAR,
        
        latitude            FLOAT,
        
        longitude           FLOAT
        



------------------------------------------------


time :

        start_time          TIMESTAMP       NOT NULL PRIMARY KEY,
        
        hour                INTEGER         NOT NULL,
        
        day                 INTEGER         NOT NULL,
        
        week                INTEGER         NOT NULL,
        
        month               INTEGER         NOT NULL,
        
        year                INTEGER         NOT NULL,
        
        weekday             VARCHAR(20)     NOT NULL
 
 
 -------------------------------------------------
 
 
 project steps: 
 1- create an account in AMAZON WEB SERVICES.
 
 2- create an IAM role and give it adminstration access. 
 
 3- create a redshift cluster via IaC  and give it [roleArn] 
 
 4- establish a connection to the redshift cluster then load the data in the staging tables
 
 5- extract the needed data to insert it in our final tables thus creating the star schema we wanted .
 
 
 
 ## END OF PROJECT ## 
 
 
 
 
 
 
 
