# 🎵 Music Streaming Project — Data Dictionary

This document provides detailed descriptions of all tables and columns in the **Music Streaming Project** database.  
The schema models artists, their songs, and curated playlists, representing a simplified backend of a music streaming platform.

---

## 🧩 Table: artists

| Column Name | Data Type | Description |
|--------------|------------|--------------|
| **artist_id** | SERIAL | Unique identifier for each artist (Primary Key). |
| **name** | VARCHAR(100) | Full name of the artist or band (e.g., *Sauti Sol*). |
| **genre** | VARCHAR(50) | Music genre the artist is known for (e.g., *Afro-Pop*, *Hip-Hop*). |
| **country** | VARCHAR(50) | Country of origin of the artist (e.g., *Kenya*). |
| **debut_year** | INT | The year the artist debuted or released their first track. |

---

## 🎶 Table: songs

| Column Name | Data Type | Description |
|--------------|------------|--------------|
| **song_id** | SERIAL | Unique identifier for each song (Primary Key). |
| **title** | VARCHAR(100) | Title of the song (e.g., *Suzanna*). |
| **artist_id** | INT | Foreign key referencing `artists(artist_id)` — indicates which artist performed the song. |
| **duration_sec** | INT | Song duration in seconds (e.g., *240 seconds = 4 minutes*). |
| **release_year** | INT | Year the song was officially released. |

**Relationships:**
- Each **song** belongs to **one artist**.
- One **artist** can have **multiple songs**.

---

## 🎧 Table: playlists

| Column Name | Data Type | Description |
|--------------|------------|--------------|
| **playlist_id** | SERIAL | Unique identifier for each playlist (Primary Key). |
| **playlist_name** | VARCHAR(100) | The name of the playlist (e.g., *Kenyan Vibes Mix*). |
| **created_by** | VARCHAR(100) | Name of the user or curator who created the playlist. |
| **song_id** | INT | Foreign key referencing `songs(song_id)` — links a playlist entry to a song. |
| **date_added** | DATE | Date when the song was added to the playlist. |

**Relationships:**
- Each **playlist entry** contains **one song**.
- A **song** can appear in **multiple playlists**.

---

## 🔗 Entity Relationship Summary

**Relationships:**

1. `artists (1) → (∞) songs`  
   → One artist can have many songs.  

2. `songs (1) → (∞) playlists`  
   → One song can be added to multiple playlists.

---

## 📊 ERD Overview

```
┌─────────────┐       ┌────────────┐       ┌───────────────┐
│   artists   │1-----∞│   songs    │1-----∞│   playlists   │
├─────────────┤       ├────────────┤       ├───────────────┤
│ artist_id   │       │ song_id    │       │ playlist_id   │
│ name        │       │ title      │       │ playlist_name │
│ genre       │       │ artist_id  │       │ created_by    │
│ country     │       │ duration   │       │ song_id       │
│ debut_year  │       │ release_yr │       │ date_added    │
└─────────────┘       └────────────┘       └───────────────┘
```

---

## ⚙️ Notes

- All primary keys are auto-incremented via `SERIAL`.  
- All foreign keys maintain referential integrity.  
- Dates use SQL format `YYYY-MM-DD`.  

---

✅ **Author:** Sharon Khirasi 
📅 **Version:** 1.0  
📦 **Database:** Supabase (PostgreSQL)  
🌍 **Domain:** Kenyan Music Streaming Platform

