 


# Music project 🎶

<div align="center">
  <img width="200" height="200" alt="Music Streaming Logo" src="https://github.com/user-attachments/assets/20661293-a214-4004-9042-657102fb0710" />
  <br/>
  <h2><b>Music project Database</b></h2>
</div>

---

# 📗 Table of Contents

* [📖 About the Project](#about-project)
* [🛠 Built With](#built-with)
* [✨ Key Features](#key-features)
* [🚀 Live Demo](#live-demo)
* [💻 Getting Started](#getting-started)
* [📊 ERD Diagram](#erd-diagram)
* [📈 Analytics Preview](#analytics-preview)
* [💾 Schema SQL](#schema-sql)
* [👥 Authors](#authors)
* [🔮 Future Features](#future-features)
* [🤝 Contributing](#contributing)
* [⭐️ Show your support](#support)
* [🙏 Acknowledgements](#acknowledgements)
* [❓ FAQ](#faq)
* [📝 License](#license)

---

# 📖 About the Project

> **Music project** is a simplified backend database for a  music streaming platform.  
> It models how songs, artists, and playlists relate — ideal for learning database design, SQL relationships, and query writing using **Supabase (PostgreSQL)*

---

## 🛠 Built With

- **Supabase (PostgreSQL)**  
- **SQL / dbdiagram.io**  
- **Power BI (Analytics Placeholder)**

---

## ✨ Key Features

- 🎤  artist profiles with genre and debut year  
- 🎵 Songs linked to artists via foreign keys  
- 📻 Playlists for users  
- 🧩 Ready-to-run Supabase SQL script  

---

## 🚀 Live Demo

Run directly in Supabase SQL Editor.

---

## 💻 Getting Started

Clone this repository:

```bash
git clone https://github.com/sharon975/music project.git
cd musicproject
```

---

## 📊 ERD Diagram

<img width="1332" height="441" alt="image" src="https://github.com/user-attachments/assets/4a9c1994-7167-466f-a606-60eeee865d8a" />


---



## 💾 Schema SQL

```sql
CREATE TABLE artists (
  artist_id SERIAL PRIMARY KEY,
  name VARCHAR(100),
  genre VARCHAR(50),
  country VARCHAR(50),
  debut_year INT
);

CREATE TABLE songs (
  song_id SERIAL PRIMARY KEY,
  title VARCHAR(100),
  artist_id INT REFERENCES artists(artist_id),
  duration_sec INT,
  release_year INT
);

CREATE TABLE playlists (
  playlist_id SERIAL PRIMARY KEY,
  playlist_name VARCHAR(100),
  created_by VARCHAR(100),
  song_id INT REFERENCES songs(song_id),
  date_added DATE
);

INSERT INTO artists (name, genre, country, debut_year) VALUES
('Otile Brown', 'R&B', 'Kenya', 2015),
('Nadia Mukami', 'Pop', 'Kenya', 2017),
('Sauti Sol', 'Afro-Pop', 'Kenya', 2010),
('Khaligraph Jones', 'Hip-Hop', 'Kenya', 2014),
('Nyashinski', 'R&B', 'Kenya', 2016),
('Trio Mio', 'Hip-Hop', 'Kenya', 2020),
('Fena Gitu', 'Afro-Fusion', 'Kenya', 2012);

INSERT INTO songs (title, artist_id, duration_sec, release_year) VALUES
('Dusuma', 1, 210, 2020),
('Maombi', 2, 185, 2019),
('Suzanna', 3, 250, 2020),
('Mazishi', 4, 230, 2016),
('Malaika', 5, 200, 2018),
('Cheza Kama Wewe', 6, 195, 2021),
('Siri', 7, 240, 2019);

INSERT INTO playlists (playlist_name, created_by, song_id, date_added) VALUES
('Chill Vibes', 'Brian Mwangi', 1, '2025-10-10'),
('Workout Beats', 'Mary Njeri', 4, '2025-10-09'),
('Love Songs', 'Kevin Otieno', 2, '2025-10-12'),
('Kenyan Classics', 'Alice Wambui', 5, '2025-10-14'),
('Top Hits', 'David Ochieng', 3, '2025-10-11'),
('Gen Z Vibes', 'Linet Achieng', 6, '2025-10-15'),
('Afro Fusion Mix', 'Joseph Kariuki', 7, '2025-10-16');
```

---

##output of our queries from supabase
**View all songs and artists**
```sql
SELECT s.title, a.name AS artist, s.release_year
FROM songs s
JOIN artists a ON s.artist_id = a.artist_id;
```

<img width="1316" height="576" alt="image" src="https://github.com/user-attachments/assets/dd3ffa77-6467-467b-885a-c0cc09bd9352" />

**Songs in the 'Chill Vibes' playlist**
```sql
Songs in the 'Chill Vibes' playlist
SELECT p.playlist_name, s.title, a.name AS artist
FROM playlists p
JOIN songs s ON p.song_id = s.song_id
JOIN artists a ON s.artist_id = a.artist_id
WHERE p.playlist_name = 'Chill Vibes';
```
<img width="1342" height="541" alt="image" src="https://github.com/user-attachments/assets/f5a9ad37-fb9e-42fd-ac0d-9b692b3af39a" />

** Number of songs per artist**

```sql
SELECT a.name, COUNT(s.song_id) AS total_songs
FROM artists a
LEFT JOIN songs s ON a.artist_id = s.artist_id
GROUP BY a.name
ORDER BY total_songs DESC;
```
<img width="1350" height="625" alt="image" src="https://github.com/user-attachments/assets/62483ff4-5c41-4f9e-abf6-66f6ef3b1293" />

## 👥 Author

**sharon khirasi** 
GitHub: [@sharon khirasi](https://github.com/sharon975)

---

## 🔮 Future Features

- Add user accounts  
- Track most played songs  
- Integrate analytics dashboard  

---

## 📝 License

This project is licensed under the MIT License.

