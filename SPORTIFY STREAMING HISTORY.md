## **SPORTIFY STREAMING HISTORY**





CREATE TABLE spotify\_streams (

    spotify\_track\_uri VARCHAR(100),

    ts TIMESTAMP,

    platform VARCHAR(50),

    ms\_played INT,

    track\_name VARCHAR(255),

    artist\_name VARCHAR(255),

    album\_name VARCHAR(255),

    reason\_start VARCHAR(50),

    reason\_end VARCHAR(50),

    shuffle BOOLEAN,

    skipped BOOLEAN

);





-- Import Data into spotify\_streams



COPY spotify\_streams(spotify\_track\_uri,ts,platform, ms\_played,track\_name,artist\_name,album\_name,reason\_start,reason\_end,shuffle,skipped)

FROM 'C:\\Users\\Tnluser.PG02LWNZ\\Desktop\\SQL\\My Project\\Spotify streaming history\\spotify\_history.csv' 

CSV HEADER;





SELECT \* FROM spotify\_streams;







🟢 Easy Level:



-- 1)List all distinct platforms used



SELECT DISTINCT platform FROM spotify\_streams;







-- 2) Show all tracks that were skipped



SELECT track\_name, artist\_name FROM spotify\_streams

WHERE skipped = 'true';







-- 3) Find all tracks played in shuffle mode



SELECT track\_name, artist\_name FROM spotify\_streams

WHERE shuffle = 'true';







-- 4) Count total number of streams in the dataset



SELECT COUNT(\*) AS total\_streams FROM spotify\_streams;







🟡 Moderate Level:



-- 1) Get all streams by a specific artist (e.g., 'Maroon 5')



SELECT track\_name, artist\_name FROM spotify\_streams

WHERE artist\_name = 'Maroon 5'

GROUP BY track\_name, artist\_name;







-- 2) Count the number of times each track was played



SELECT track\_name, COUNT(track\_name) AS play\_count

FROM spotify\_streams

GROUP BY track\_name

ORDER BY play\_count DESC;







-- 3) Total play time (ms\_played) in min for each artist



SELECT artist\_name, SUM(ms\_played)/60000 AS total\_play\_time

FROM spotify\_streams

GROUP BY artist\_name

ORDER BY total\_play\_time DESC;







-- 4) Average play time per platform



SELECT platform, ROUND(AVG(ms\_played),2) as avg\_play\_time

FROM spotify\_streams

GROUP BY platform;







-- 5) Top 5 most played albums by total ms\_played



SELECT album\_name, SUM(ms\_played) as total\_ms\_played

FROM spotify\_streams

GROUP BY album\_name

ORDER BY total\_ms\_played desc

LIMIT 5;







-- 6) Find the most played track (by total ms\_played)



SELECT track\_name AS most\_played\_track, SUM(ms\_played) AS total\_ms\_played

FROM spotify\_streams

GROUP BY track\_name

ORDER BY total\_ms\_played desc

LIMIT 1;







🔴 Advanced Level:



-- 1) 	Show top 3 artists by total playtime for each platform



WITH top\_artist AS

(SELECT artist\_name, platform, sum(ms\_played) as total\_run\_time,

  RANK() OVER(PARTITION by platform ORDER BY SUM(ms\_played)desc) AS rnk

FROM spotify\_streams

GROUP BY artist\_name, platform)



SELECT artist\_name, platform, total\_run\_time

FROM top\_artist

WHERE rnk <= 3;







-- 2) Find tracks that were never skipped and played more than 3 times



SELECT track\_name, COUNT(\*) AS play\_count

FROM spotify\_streams

WHERE skipped = 'false'

GROUP BY track\_name

HAVING COUNT(\*) > 3;







-- 3) Calculate the total play time per month



SELECT EXTRACT(month from ts) AS month, SUM(ms\_played) AS monthly\_play\_time

FROM spotify\_streams

GROUP BY month

ORDER BY month;





-- 4) Calculate the total play time per year



SELECT EXTRACT(year from ts) as year, SUM(ms\_played) AS yearly\_play\_time

FROM spotify\_streams

GROUP BY year

ORDER BY year;







-- 5) 	Find the percentage of tracks that were skipped



SELECT

   ROUND(100.00\* SUM(CASE WHEN skipped = 'true' THEN 1 ELSE 0 END)/ COUNT(\*),2) AS skipped\_percent

FROM spotify\_streams;







-- 6) 	Top tracks by playtime of each artist.



WITH top\_artist AS

(SELECT artist\_name, track\_name, SUM(ms\_played) AS total\_run\_time,

  RANK() OVER(PARTITION BY artist\_name ORDER BY SUM(ms\_played)desc) AS rnk

FROM spotify\_streams

GROUP BY artist\_name, track\_name)



SELECT artist\_name, track\_name, total\_run\_time

FROM top\_artist

WHERE rnk = 1;







-- 7) 	Top 3 most frequent start reason globally



SELECT reason\_start, COUNT(\*) AS frequency

FROM spotify\_streams

GROUP BY reason\_start

ORDER BY frequency DESC

LIMIT 3;





-- 8) Analyze peak listening hour across the day



SELECT EXTRACT(hour from ts) AS hour\_of\_the\_day,

       COUNT(\*) AS stream\_count

FROM spotify\_streams

GROUP BY hour\_of\_the\_day

ORDER BY stream\_count DESC;







-- 9) Find the most played track per day (by ms\_played)



SELECT \*

FROM (

    SELECT DATE(ts) AS play\_date, track\_name, artist\_name, SUM(ms\_played) AS total\_played,

           RANK() OVER (PARTITION BY DATE(ts) ORDER BY SUM(ms\_played) DESC) AS daily\_rank

    FROM spotify\_streams

    GROUP BY DATE(ts), track\_name, artist\_name

) ranked

WHERE daily\_rank = 1;







-- 10) Calculate rolling 3-day average playtime per artist.



SELECT artist\_name,

&nbsp;      DATE(ts) AS play\_date,

&nbsp;      SUM(ms\_played) AS daily\_play,

&nbsp;      round(AVG(SUM(ms\_played)) OVER (PARTITION BY artist\_name ORDER BY DATE(ts) 

&nbsp;	             ROWS BETWEEN 2 PRECEDING AND CURRENT ROW),2) AS rolling\_3\_day\_avg

FROM spotify\_streams

GROUP BY artist\_name, DATE(ts);





