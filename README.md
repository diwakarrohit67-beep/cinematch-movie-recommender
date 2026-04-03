# 🎬 CineMatch — ML Movie Recommender System

![Python](https://img.shields.io/badge/Python-3.10+-blue?style=flat-square&logo=python)
![scikit-learn](https://img.shields.io/badge/scikit--learn-TF--IDF-orange?style=flat-square&logo=scikit-learn)
![Dataset](https://img.shields.io/badge/Dataset-TMDB%205000-red?style=flat-square)
![GitHub Pages](https://img.shields.io/badge/Deployed-GitHub%20Pages-brightgreen?style=flat-square&logo=github)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)

> A content-based movie recommendation engine built with **TF-IDF vectorization** and **Cosine Similarity**, deployed as a fully interactive single-page web app — no backend required.

🔗 **Live Demo:** [diwakarrohit67-beep.github.io/cinematch-movie-recommender](https://diwakarrohit67-beep.github.io/cinematch-movie-recommender/)

---

## 📸 Features

- 🔍 **Live search** with autocomplete across 4,803 movies
- 🤖 **ML-powered recommendations** — click any movie to get similar films instantly
- 🏷️ **Genre filtering** across 19 genres
- 📊 **Sort by** Weighted Score, Rating, Popularity, or Release Year
- 📱 Fully **responsive** — works on mobile & desktop
- ⚡ Zero backend — entire model is embedded in the HTML file

---

## 🧠 Machine Learning Pipeline

### Algorithm: Content-Based Filtering

```
Raw Data → Feature Engineering → TF-IDF Vectorization → Cosine Similarity Matrix → Hybrid Ranking
```

### Step-by-step

| Step | Detail |
|------|--------|
| **1. Data Parsing** | Parsed JSON columns: `genres`, `keywords`, `production_companies` from TMDB dataset |
| **2. Feature Engineering** | Combined `overview + genres + keywords` into a single text "soup" per movie |
| **3. TF-IDF Vectorization** | `TfidfVectorizer(max_features=10000, stop_words='english')` — converts text to a sparse feature matrix |
| **4. Cosine Similarity** | Computed pairwise cosine similarity across all 4,803 × 4,803 movie pairs |
| **5. Bayesian Weighted Rating** | IMDB-style weighted score: `(v/(v+m)) × R + (m/(m+v)) × C` to balance quality vs. popularity |
| **6. Hybrid Score** | Final score = `0.7 × content_similarity + 0.3 × weighted_rating_norm` |

### Why TF-IDF + Cosine Similarity?

- **TF-IDF** (Term Frequency-Inverse Document Frequency) gives higher weight to rare, meaningful words in a movie's description while downweighting common words
- **Cosine Similarity** measures the angle between two movie vectors — making it scale-invariant and ideal for sparse text data
- The **Bayesian weighted rating** prevents movies with very few votes from dominating recommendations

---

## 📁 Project Structure

```
cinematch-movie-recommender/
│
├── index.html              # Complete app — ML data + UI embedded in one file
├── README.md               # This file
└── tmdb_5000_movies.csv    # Source dataset (optional, for reference)
```

> The `index.html` contains the full precomputed similarity model (400 top movies × 12 recommendations each) and all 4,803 movie records embedded as JSON — no server needed.

---

## 📊 Dataset

**TMDB 5000 Movie Dataset** — sourced from [Kaggle](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)

| Property | Value |
|----------|-------|
| Total movies | 4,803 |
| Features used | `title`, `overview`, `genres`, `keywords`, `vote_average`, `vote_count`, `release_date` |
| Precomputed recommendations | Top 400 movies |
| Genres covered | 19 |

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| ML / Data | Python, pandas, NumPy, scikit-learn |
| Vectorization | `TfidfVectorizer` (scikit-learn) |
| Similarity | `cosine_similarity` (scikit-learn) |
| Frontend | Vanilla HTML, CSS, JavaScript |
| Fonts | Google Fonts (Playfair Display + DM Sans) |
| Deployment | GitHub Pages |

---

## 🚀 Run Locally

Clone the repo and open the file — no installation needed:

```bash
git clone https://github.com/diwakarrohit67-beep/cinematch-movie-recommender.git
cd cinematch-movie-recommender
# Just open index.html in your browser!
open index.html
```

### Rebuild the model from scratch (optional)

If you want to retrain on the dataset:

```bash
pip install pandas numpy scikit-learn
python build_model.py   # generates movies_data.json
```

---

## 💡 How to Use

1. **Search** for a movie you like in the search bar
2. **Click** on it from the dropdown
3. The ML model instantly shows the **top 10 most similar movies**
4. Use **genre filters** and **sort options** to explore further
5. Click **any recommended movie** to get recommendations based on that one

---

## 📈 Future Improvements

- [ ] Add collaborative filtering (user-based recommendations)
- [ ] Integrate TMDB API for real movie posters
- [ ] Add a "mood" filter (dark, funny, feel-good)
- [ ] Deploy with Flask/FastAPI backend for on-the-fly computation
- [ ] Add user ratings and personalisation

---

## 👨‍💻 Author

**Rohit Diwakar**  
Data Science & Machine Learning enthusiast

[![GitHub](https://img.shields.io/badge/GitHub-diwakarrohit67--beep-black?style=flat-square&logo=github)](https://github.com/diwakarrohit67-beep)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Rohit%20Diwakar-blue?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/rohit-diwakar-346a511a8/)
[![Kaggle](https://img.shields.io/badge/Kaggle-rohitdiwakar9927-20BEFF?style=flat-square&logo=kaggle)](https://www.kaggle.com/rohitdiwakar9927)

---

## 📄 License

This project is licensed under the MIT License — feel free to use and modify it.

---

⭐ **If you found this useful, please star the repo!**
