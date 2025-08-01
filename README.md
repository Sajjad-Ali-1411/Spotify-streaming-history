
# 🎵 Spotify Listening Behavior Analysis

This project explores a Spotify streaming dataset using structured SQL queries. It showcases how to analyze music listening behavior across platforms, artists, albums, time, and user interactions (e.g., shuffle, skips).

---

## 📁 Project Structure

- `SQL_Easy_Medium_Advanced.sql`: Contains categorized SQL queries — easy, moderate, and advanced — to analyze the Spotify streaming dataset.
- `Spotify_SQL_Queries_Easy_Medium_Advanced.docx`: A well-formatted Word document with questions and solutions.
- `Advanced_SQL_Streaming_Questions.docx`: Contains deeper analytical SQL questions using advanced SQL features.
- Sample data (not included due to privacy, but you can structure it as per the `CREATE TABLE` below).

---

## 🧾 Table Schema

```sql
CREATE TABLE spotify_streams (
    spotify_track_uri VARCHAR(100),
    ts TIMESTAMP,
    platform VARCHAR(50),
    ms_played INT,
    track_name VARCHAR(255),
    artist_name VARCHAR(255),
    album_name VARCHAR(255),
    reason_start VARCHAR(50),
    reason_end VARCHAR(50),
    shuffle BOOLEAN,
    skipped BOOLEAN
);
```

## 🧠 Skills Demonstrated

- SQL querying (basic to advanced)
- Data aggregation and time-based analysis
- Behavioral insights using structured data
- Use of window functions and conditional logic
- Real-world scenario thinking with music streaming data

---

## 🔍 What to Learn from This Project

### 🟢 Easy Level
- Data retrieval
- Filtering rows based on conditions (e.g., skipped, shuffle)
- Counting rows and basic aggregations

### 🟡 Moderate Level
- Grouping and aggregating (play count, total playtime)
- Filtering aggregated results
- Top N analysis (e.g., top 5 albums)
- Platform-based insights

### 🔴 Advanced Level
- Window functions (e.g., `RANK`, `ROLLING AVERAGE`)
- Time-series aggregations (e.g., monthly stats)
- Behavior-based analytics (e.g., skip rates, peak hours)
- Most played tracks by artist or date

---

## 📌 How to Use

1. Clone the repository.
2. Import the table schema into your SQL database.
3. Load your dataset (in the same format as `spotify_streams`).
4. Run queries from the provided `.sql` or `.docx` files using your SQL client (MySQL, PostgreSQL, SQLite, etc.).
5. Extend the project with data visualization (e.g., using Power BI, Tableau, or Python libraries).

---


## 💡 Key Insights

- Mobile and desktop platforms dominate the streaming behavior, with slight differences in usage patterns across the day.
- Top artists like 'The Beatles', 'The Killers', 'John Mayer', and others account for a large share of total playtime — artist popularity skews heavily.
- Skips occur in a significant portion of sessions (e.g., ~40–60%), highlighting listener selectivity and content fatigue.
- Tracks played in shuffle mode are skipped less often, indicating randomness may increase engagement.
- Most streamed tracks and albums align with current chart trends, validating the dataset’s relevance to real-world preferences.
- Listening behavior peaks in the evening hours, especially post 6 PM, indicating optimal promotion windows.
- Playtime per artist per month reveals strong seasonality trends (e.g., holiday spikes or summer anthems).
- A small group of albums and artists consistently dominate top charts, reinforcing the "80/20 rule" in music consumption.
- Certain tracks are never skipped and played multiple times — clear indicators of highly engaging content.
- The most frequent start reasons are "track completion" and "user action", suggesting users are actively engaged rather than passively listening.

---

## 📈 Business Recommendations

- Promote new releases or sponsored content during evening peak hours to maximize reach and engagement.
- Leverage shuffle mode or similar "discovery" features to reduce skips and increase time spent listening.
- Create retargeting campaigns for high skip-rate users or tracks, and offer personalized playlists to re-engage them.
- Invest in exclusive content or collaborations with top artists who drive the majority of stream time.
- Launch monthly or seasonal listening reports for users, highlighting their top artists/tracks to increase stickiness.
- Introduce replay-focused playlists based on tracks played without skipping and more than 3 times — these show strong emotional or habitual listening.
- Focus ad placements and push notifications on platforms that show the highest average playtime, especially during high engagement hours.
- Encourage platform features that replicate "start reason: track completion", such as seamless transitions or story-like music playback.


## 📄 License

This project is open-source and available for educational and personal use.

---

## 🙌 Acknowledgments

Inspired by personal music streaming logs and exploratory data analysis practices.
