# Spotify Music Data Analysis

Exploratory data analysis and unsupervised machine learning on a Spotify dataset of ~90,000 tracks. The project uncovers patterns in audio features across genres and groups songs into meaningful clusters using K-Means and DBSCAN.

---

## Key Findings

- **Loudness and energy** are strongly positively correlated — louder tracks are almost always high-energy
- **Acousticness and energy** are strongly negatively correlated — acoustic instruments dominate low-energy tracks
- **Genre audio fingerprints** differ significantly: classical music scores highest on acousticness (0.92), heavy metal on energy (0.87), pop on danceability (0.73)
- **K-Means (k=4)** identified 4 musically coherent clusters — after testing k=5, the 5th cluster proved redundant and k=4 produced cleaner, more interpretable separation:
  - _Energetic Dance/Pop_ — high danceability + high energy
  - _Acoustic/Melancholic_ — low energy, high acousticness
  - _Intense/Electronic_ — very high energy, low acousticness
  - _Live/Spoken Word_ — high liveness and speechiness, dominated by comedy and samba
- **Explicit tracks** tend to have slightly higher popularity scores than non-explicit ones

---

## Tech Stack

| Category          | Libraries                                            |
| ----------------- | ---------------------------------------------------- |
| Data manipulation | `pandas`, `numpy`                                    |
| Visualization     | `matplotlib`, `seaborn`, `plotly`                    |
| Machine learning  | `scikit-learn` (KMeans, DBSCAN, PCA, StandardScaler) |
| Environment       | Python 3.10+, Jupyter Notebook                       |

---

## Project Structure

```
Music-Data-Analysis/
│
├── 01_eda.ipynb             # Initial exploration: data types, nulls, duplicates, cleaning
├── 02.preprocessing.ipynb   # Preprocessing pipeline: cleaning steps isolated
├── 03_deepEDA.ipynb         # Deep EDA: valence categories, genre profiles, correlations
├── 04_modeling.ipynb        # Clustering: Elbow method, K-Means, PCA, DBSCAN
│
├── data/                    # Dataset directory (not tracked — see Dataset section)
├── requirements.txt
└── README.md
```

---

## Dataset

The dataset contains ~114,000 Spotify tracks with 20 features including audio characteristics and metadata.

**Source:** [Spotify Tracks Dataset on Kaggle](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset)

After cleaning (removing nulls and duplicate `track_id` entries): **89,740 tracks**

**Key columns:**

| Feature            | Description                                   |
| ------------------ | --------------------------------------------- |
| `popularity`       | Track popularity score (0–100)                |
| `danceability`     | How suitable a track is for dancing (0.0–1.0) |
| `energy`           | Intensity and activity level (0.0–1.0)        |
| `acousticness`     | Confidence the track is acoustic (0.0–1.0)    |
| `valence`          | Musical positiveness (0.0–1.0)                |
| `tempo`            | Estimated beats per minute                    |
| `instrumentalness` | Predicts whether a track has no vocals        |
| `liveness`         | Presence of a live audience                   |
| `speechiness`      | Presence of spoken words                      |
| `explicit`         | Whether the track has explicit lyrics         |
| `track_genre`      | Genre label                                   |

---

## How to Run

**1. Clone the repository**

```bash
git clone https://github.com/Handras18/Music-Data-Analysis.git
cd Music-Data-Analysis
```

**2. Install dependencies**

```bash
pip install -r requirements.txt
```

**3. Download the dataset**

Download the dataset from Kaggle (link above) and place it at:
https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset

```
data/dataset.csv
```

**4. Run the notebooks in order**

```bash
jupyter notebook
```

Open and run notebooks in sequence: `01` → `02` → `03` → `04`
