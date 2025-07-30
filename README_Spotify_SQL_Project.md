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

---

## 🔍 What You Can Learn from This Project

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

## 🧠 Skills Demonstrated

- SQL querying (basic to advanced)
- Data aggregation and time-based analysis
- Behavioral insights using structured data
- Use of window functions and conditional logic
- Real-world scenario thinking with music streaming data

---

## 📌 How to Use

1. Clone the repository.
2. Import the table schema into your SQL database.
3. Load your dataset (in the same format as `spotify_streams`).
4. Run queries from the provided `.sql` or `.docx` files using your SQL client (MySQL, PostgreSQL, SQLite, etc.).
5. Extend the project with data visualization (e.g., using Power BI, Tableau, or Python libraries).

---

## 📄 License

This project is open-source and available for educational and personal use.

---

## 🙌 Acknowledgments

Inspired by personal music streaming logs and exploratory data analysis practices.