
# 🎧 Spotify SQL Analysis Project

## 📌 Overview

This project involves analyzing a Spotify dataset with various attributes about tracks, albums, and artists using SQL. It covers an end-to-end process of normalizing a denormalized dataset, performing SQL queries of varying complexity (easy, medium, and advanced), and optimizing query performance. The primary goals of the project are to practice advanced SQL skills and generate valuable insights from the dataset.

---

## 🗃️ Table Schema

```sql
-- create table
DROP TABLE IF EXISTS spotify;
CREATE TABLE spotify (
    artist VARCHAR(255),
    track VARCHAR(255),
    album VARCHAR(255),
    album_type VARCHAR(50),
    danceability FLOAT,
    energy FLOAT,
    loudness FLOAT,
    speechiness FLOAT,
    acousticness FLOAT,
    instrumentalness FLOAT,
    liveness FLOAT,
    valence FLOAT,
    tempo FLOAT,
    duration_min FLOAT,
    title VARCHAR(255),
    channel VARCHAR(255),
    views FLOAT,
    likes BIGINT,
    comments BIGINT,
    licensed BOOLEAN,
    official_video BOOLEAN,
    stream BIGINT,
    energy_liveness FLOAT,
    most_played_on VARCHAR(50)
);
```

---

## 🚦 Project Steps

### 1. Data Exploration
Before diving into SQL, it’s important to understand the dataset thoroughly. The dataset contains attributes such as:
- **Artist**: The performer of the track.
- **Track**: The name of the song.
- **Album**: The album to which the track belongs.
- **Album_type**: The type of album (e.g., single or album).
- **Metrics**: Danceability, energy, loudness, tempo, and more.

---

### 2. Querying the Data

After inserting the data into the table, various SQL queries can be written to explore and analyze it. Queries are categorized into **easy**, **medium**, and **advanced** levels to help progressively develop SQL proficiency.

---

## 🧪 Practice Questions

### ✅ Easy Level
1. Retrieve the names of all tracks that have more than 1 billion streams.  
2. List all albums along with their respective artists.  
3. Get the total number of comments for tracks where `licensed = TRUE`.  
4. Find all tracks that belong to the album type `single`.  
5. Count the total number of tracks by each artist.  

---

### ⚙️ Medium Level
6. Calculate the average danceability of tracks in each album.  
7. Find the top 5 tracks with the highest energy values.  
8. List all tracks along with their views and likes where `official_video = TRUE`.  
9. For each album, calculate the total views of all associated tracks.  
10. Retrieve the track names that have been streamed on Spotify more than YouTube.  

---

### 🚀 Advanced Level
11. Find the top 3 most-viewed tracks for each artist using window functions.  
12. Write a query to find tracks where the liveness score is above the average.  
13. Use a WITH clause to calculate the difference between the highest and lowest energy values for tracks in each album.  

```sql
WITH cte AS (
    SELECT 
        album,
        MAX(energy) AS highest_energy,
        MIN(energy) AS lowest_energery
    FROM spotify
    GROUP BY 1
)
SELECT 
    album,
    highest_energy - lowest_energery AS energy_diff
FROM cte
ORDER BY 2 DESC;
```

14. Find tracks where the energy-to-liveness ratio is greater than 1.2.  
15. Calculate the cumulative sum of likes for tracks ordered by the number of views, using window functions.  

---

## 🚀 Query Optimization

At advanced stages, the focus shifts to improving query performance. Techniques used include:

- **Indexing**: Creating indexes on frequently queried columns.
- **Query Execution Plan**: Using `EXPLAIN ANALYZE` to review and refine SQL query performance.

---
