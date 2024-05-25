# Case Study : How Does a Bike-Share Navigate Speedy Success?


## Purpose

This is my capstone project of the Google Data Analytics Professional Certificate which I followed through Coursera. Under this project, I access the public dataset provided by a fictional company.I will share my insights and provide informed recommendations on the marketing strategies that will contribute to the company’s remarkable success.In this project, following steps will be followed: **Ask, Prepare, Process, Analyze, Share, Act.**


## Background

**Scenario:**

I am a junior data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. Therefore, my team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, my team will design a new marketing strategy to convert casual riders into annual members.

**About the Company:**

In 2016, Cyclistic launched a successful bike-share oering. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime. Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members. Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, The director of marketing believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, she believes there is a very good chance to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.

## Ask


**Business Task**: Design marketing strategies aimed at converting casual riders into annual members.


\
Three questions will guide the future marketing program:






1. How do annual members and casual riders use Cyclistic bikes differently?
2. Why would casual riders buy Cyclistic annual memberships?
3. How can Cyclists use digital media to influence casual riders to become members?


\
Moreno has assigned you the first question to answer: How do annual members and casual riders use Cyclistic bikes differently?


With the purpose of recognizing patterns and extracting useful insights from the recognized patterns, this study aims to investigate the usage patterns of annual members and casual riders of Cyclistic bikes.




## Prepare


The dataset utilized in this case study can be accessed through the following link: https://divvy-tripdata.s3.amazonaws.com/index.html


In the context of this case study, we employed data pertaining to a single complete annual period, specifically the year 2023. This data is organized on a monthly basis and can be found at the aforementioned location. For example: 202301-divvy-tripdata.zip. Upon further examination, it was observed that all files possess the same 13 columns or attributes, and the data types are consistent throughout.


As the data is structured by month, during this phase, we have created a new singular table with the necessary columns utilizing SQL queries.


The query used for this is as follows:


```
SELECT * 
INTO dbo.[cyclistic_bike] 
FROM (

SELECT ride_id, rideable_type, started_at, ended_at, start_station_name, end_station_name, member_casual
FROM dbo.[202301]
UNION ALL

SELECT ride_id, rideable_type, started_at, ended_at, start_station_name, end_station_name, member_casual
FROM dbo.[202302]
UNION ALL

SELECT ride_id, rideable_type, started_at, ended_at, start_station_name, end_station_name, member_casual
FROM dbo.[202303]
UNION ALL

SELECT ride_id, rideable_type, started_at, ended_at, start_station_name, end_station_name, member_casual
FROM dbo.[202304]
UNION ALL

SELECT ride_id, rideable_type, started_at, ended_at, start_station_name, end_station_name, member_casual
FROM dbo.[202305]
UNION ALL

SELECT ride_id, rideable_type, started_at, ended_at, start_station_name, end_station_name, member_casual
FROM dbo.[202306]
UNION ALL

SELECT ride_id, rideable_type, started_at, ended_at, start_station_name, end_station_name, member_casual
FROM dbo.[202307]
UNION ALL

SELECT ride_id, rideable_type, started_at, ended_at, start_station_name, end_station_name, member_casual
FROM dbo.[202308]
UNION ALL

SELECT ride_id, rideable_type, started_at, ended_at, start_station_name, end_station_name, member_casual
FROM dbo.[202309]
UNION ALL

SELECT ride_id, rideable_type, started_at, ended_at, start_station_name, end_station_name, member_casual
FROM dbo.[202310]
UNION ALL

SELECT ride_id, rideable_type, started_at, ended_at, start_station_name, end_station_name, member_casual
FROM dbo.[202311]
UNION ALL

SELECT ride_id, rideable_type, started_at, ended_at, start_station_name, end_station_name, member_casual
FROM dbo.[202312]

```






## Process


During this stage, the focus is on data cleansing and preparation. Within this phase, the following steps were undertaken:


Null values were identified and removed from the table using SQL queries.




```
# TO identify the null values

SELECT *
FROM dbo.[cyclistic_bike]
WHERE
   ride_id IS NULL
   OR rideable_type IS  NULL
   OR started_at IS NULL
   OR ended_at IS NULL
   OR start_station_name IS NULL
   OR end_station_name IS NULL
   OR member_casual IS NULL
;



# TO delete the null values

DELETE FROM dbo.[cyclistic_bike]
WHERE
ride_id IS NULL
OR rideable_type IS  NULL
OR started_at IS NULL
OR ended_at IS NULL
OR start_station_name IS NULL
OR end_station_name IS NULL
OR member_casual IS NULL;
```




Duplicate values were identified and removed from the table using SQL queries.




```
WITH DUPLICATE_COUNT AS (
    SELECT *, COUNT(*) AS duplicate_count
    FROM dbo.[cyclistic_bike]
    GROUP BY 
        ride_id,
        rideable_type,
        started_at,
        ended_at,
        start_station_name, 
        end_station_name,
        member_casual
    HAVING COUNT(*)>1
) 
DELETE O
FROM dbo.[cyclistic_bike] as O
INNER JOIN DUPLICATE_COUNT AS D
    ON  O.ride_id = D.ride_id 
        AND O.rideable_type = D.rideable_type 
        AND O.started_at = D.started_at
        AND O.ended_at = D.ended_at 
        AND O.start_station_name = D.start_station_name
        AND O.end_station_name = D.end_station_name
        AND O.member_casual = D.member_casual


;
```
