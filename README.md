# Spotify Song Recommendation System

A content-based music recommendation system built using Python and machine learning. The project clusters songs based on their audio features using K-Means and recommends similar songs using cosine similarity.

## Features

- Data preprocessing and cleaning
- Feature scaling using MinMaxScaler
- Dimensionality reduction with UMAP
- Song clustering using K-Means
- Content-based song recommendation using cosine similarity
- Cluster visualization with Seaborn and Matplotlib

## Dataset

The project uses the Spotify Songs dataset containing over 32,000 tracks with audio features such as:

- Danceability
- Energy
- Loudness
- Speechiness
- Acousticness
- Instrumentalness
- Liveness
- Valence
- Tempo
- Duration

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- UMAP
- Matplotlib
- Seaborn

## Project Workflow

1. Load the Spotify dataset.
2. Handle missing values.
3. Scale numerical audio features.
4. Encode categorical features.
5. Reduce dimensions using UMAP.
6. Cluster songs using K-Means.
7. Recommend similar songs using cosine similarity on audio features.

## Recommendation System

The recommendation engine uses cosine similarity between the scaled audio features of songs.

Given a song name, it:

- Finds the selected song.
- Identifies songs from the same cluster.
- Calculates similarity scores.
- Returns the top matching songs ranked by similarity and popularity.

Example:

```python
recommend_songs(track_name="Believer", n=5)
```

## Visualizations

- UMAP Projection of Songs
- K-Means Cluster Visualization
- Cluster Distribution by Playlist Genre

## Project Structure

```
Song-Cluster/
│
├── Spotify song cluster.ipynb
├── spotify dataset.csv
├── README.md
└── requirements.txt
```

## Installation

Clone the repository:

```bash
git clone https://github.com/Jenni006/Song-Cluster.git
```

Install dependencies:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn umap-learn
```

Run the notebook:

```bash
jupyter notebook
```

Open **Spotify song cluster.ipynb** and run all cells.

## Future Improvements

- Web application using Streamlit or Flask
- Collaborative filtering recommendations
- Spotify API integration
- Hybrid recommendation system
- Real-time playlist generation

## Author

Jennifer Stanly

B.Tech Computer Science Engineering (AI & ML)

SRM Institute of Science and Technology