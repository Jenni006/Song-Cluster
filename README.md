# Song-Clustering

A reproducible Jupyter Notebook project for exploring, preprocessing, and clustering music tracks using audio features, metadata, or precomputed embeddings. The notebook is designed for technical users who want to experiment with unsupervised learning (KMeans, DBSCAN, Agglomerative, etc.), evaluate cluster quality, and visualize results with dimensionality reduction (PCA, UMAP, t-SNE).

Table of contents
- Project overview
- Repository layout
- Getting started
- Data formats
- Notebook walkthrough
- Typical workflows
- Dependencies
- Outputs
- Reproducibility & tips
- Contributing
- License
- Contact

Project overview
Song-Cluster demonstrates how to group songs into meaningful clusters using track-level features or embeddings. It includes data ingestion, optional audio feature extraction, preprocessing, dimensionality reduction, clustering experiments, evaluation metrics, and plots for exploration.

Repository layout
- song-cluster.ipynb — primary Jupyter Notebook (analysis, preprocessing, clustering, visualization)
- data/ — input datasets (CSV, embeddings, optional audio). Not committed by default.
- outputs/ — generated exports (cluster labels, saved plots, HTML visualizations)
- requirements.txt — recommended Python dependencies
- README.md — this file

Getting started (local)
1. Clone the repo:
   git clone https://github.com/Jenni006/Song-Cluster.git
   cd Song-Cluster

2. Create & activate a virtual environment:
   python -m venv .venv
   # macOS / Linux
   source .venv/bin/activate
   # Windows
   .venv\Scripts\activate

3. Install dependencies:
   pip install -r requirements.txt
   # If no requirements file exists:
   pip install jupyter pandas numpy scikit-learn matplotlib seaborn plotly librosa umap-learn

4. Start Jupyter:
   jupyter lab    # or jupyter notebook
   Open `song-cluster.ipynb` and run cells in order.

Data formats and placement
- Metadata/feature CSV: one row per track. Example columns:
  id, title, artist, duration_ms, tempo, key, loudness, danceability, energy, valence
- Precomputed embeddings: CSV or NumPy arrays (shape n_tracks × dim)
- Raw audio files: WAV/MP3, organized by track ID or path mapping

Place datasets under `data/` and update notebook paths accordingly. Do not commit large raw audio files to the repository — prefer external storage or a dataset snapshot.

Notebook walkthrough
The notebook is organized into sections:
1. Imports, configuration and reproducible seeds
2. Data loading and validation (CSV/embeddings/audio path mapping)
3. Optional feature extraction (librosa: MFCCs, chroma, spectral features)
4. Preprocessing and feature engineering (filtering, imputation)
5. Scaling and dimensionality reduction (StandardScaler, PCA, UMAP, t-SNE)
6. Clustering experiments (KMeans, DBSCAN, Agglomerative; parameter sweeps)
7. Cluster evaluation (silhouette score, Davies–Bouldin, cluster sizes)
8. Visualizations (static and interactive)
9. Export results (CSV/JSON, saved plots)

Typical workflows
- Quick cluster experiment: load CSV with features → StandardScaler → PCA → KMeans → silhouette score → visualize clusters
- Embedding-based clustering: use precomputed embeddings instead of raw features
- Audio feature pipeline: extract features once, save to disk, run clustering on cached features

Example: export labels
```python
df['cluster'] = cluster_labels
df.to_csv('outputs/song_clusters.csv', index=False)
```

Dependencies (suggested)
jupyter
pandas
numpy
scikit-learn
matplotlib
seaborn
plotly
librosa
umap-learn

Create a requirements.txt by running:
pip freeze > requirements.txt
(or assemble from the list above)

Outputs
- 2D/3D plots of clusters (PCA / UMAP / t-SNE + coloring by cluster)
- Quality metrics: silhouette score, cluster sizes
- CSV with assigned cluster labels: `outputs/song_clusters.csv`
- Saved visualizations: `outputs/plots/*.png` or `outputs/interactive/*.html`

Reproducibility & tips
- Set random_state for reproducibility (clustering & dimensionality reduction)
- Scale features (StandardScaler or MinMaxScaler) before clustering
- Cache features extracted from audio to avoid reprocessing
- For noisy clusterings: try different feature subsets, normalization, or use pretrained audio embeddings
- For large datasets: process audio in batches; persist intermediate features to disk

Contributing
- Fork the repo
- Create a feature branch
- Implement changes and add tests/example outputs where applicable
- Submit a pull request with a clear description and reproducible steps

Contact
For questions or issues, open an issue in this repository or contact the repository owner.

Acknowledgements
This project leverages widely used libraries for music information retrieval and machine learning: scikit-learn, librosa, pandas, numpy, matplotlib, seaborn, plotly, and umap-learn.
