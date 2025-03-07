# MATH123: Mathematical Aspects of Data Analysis Final Project  

## Cluster Analysis of Top Songs  

This project explores the clustering of popular music tracks across multiple years using **K-Means clustering, Agglomerative Hierarchical Clustering, and Gaussian Mixture Models (GMM)**. The objective was to analyze how music characteristics change over time and to assess different clustering approaches for handling **time-relevant data**.  

## Overview  

Popular music evolves continuously, reflecting **cultural and technological trends**. This project investigates whether clustering techniques can reveal meaningful groupings among **Spotify's top tracks from 2017, 2018, and 2019** based on their **audio features**.  

### Key Research Questions:  
- Can we use **unsupervised learning** to cluster popular songs based on musical characteristics?  
- How does clustering change when applied to individual years versus aggregated data?  
- Do **aligned cluster centroids** across years produce better groupings than concatenated datasets?  
- How do clustering methods compare in terms of **consistency and interpretability**?  

## Data Sources  

The project uses three datasets containing **Spotify's top tracks** for different years, as well as a large reference dataset:  

- **Top Spotify Tracks of 2017** ([Kaggle](https://www.kaggle.com/datasets/nadintamer/top-tracks-of-2017))  
- **Top Spotify Tracks of 2018** ([Kaggle](https://www.kaggle.com/datasets/nadintamer/top-spotify-tracks-of-2018))  
- **Top Spotify Tracks of 2019** ([Kaggle](https://www.kaggle.com/datasets/nadintamer/top-spotify-tracks-of-2019))  
- **30,000 Spotify Songs Reference Dataset** ([Kaggle](https://www.kaggle.com/datasets/joebeachcapital/30000-spotify-songs))  

### Audio Features Used for Clustering  

Refer to the write-up for the full list of audio features.

## Methods  

Three clustering methods were applied using **Scikit-Learn**:  

### 1. **K-Means Clustering**  
- **Two approaches were tested**:  
  1. **Concatenation**: Merged all three years into a single dataset before clustering.  
  2. **Alignment**: Performed K-Means separately on each year, then merged clusters based on **centroid similarity**.  
- Optimal **k** was determined using the **elbow method** (≈11 clusters).  

### 2. **Agglomerative Hierarchical Clustering**  
- Built a **dendrogram** to visualize cluster hierarchy.  
- Determined optimal clusters by identifying the **first major split** in the hierarchy.  
- Used **Euclidean distance** as the metric.  

### 3. **Gaussian Mixture Models (GMM)**  
- Applied **Expectation-Maximization (EM) algorithm** to model clusters as Gaussian distributions.  
- Used **Bayesian Information Criterion (BIC)** to determine the optimal number of clusters.  
- Introduced **uncertainty metrics** for each song’s cluster assignment.  

### Evaluation Metrics  
- **UMAP Visualizations**: Used to assess **local cluster structure**.  
- **Jaccard Similarity**: Measured overlap between different clustering approaches.  

## Results  

- **K-Means with concatenation** produced **more cohesive clusters** compared to aligning centroids across years.  
- **Hierarchical clustering revealed subclusters**, but interpretation was difficult.  
- **GMM clustering was useful for probabilistic assignments**, providing uncertainty metrics but with some overlap between clusters.  
- Certain songs, such as **XO TOUR Llif3 (Lil Uzi Vert), Thunder (Imagine Dragons), and China (Anuel AA)**, consistently appeared near cluster centroids, indicating **stable characteristics over time**.  
- **Valence (happiness) and Danceability were correlated**, while **Acousticness and Energy were inversely related**, aligning with intuitive expectations.  

## Challenges  

- **Defining "good" clusters**: Clustering success was hard to quantify without subjective validation.  
- **Interpreting results**: Some clusters grouped **stylistically different songs** together, raising challenges in labeling.  
- **Trade-offs between methods**: K-Means was computationally efficient, Hierarchical Clustering offered **better interpretability**, and GMM provided **flexibility in assignments**.  

## Future Work  

- **Music Recommendation System**: Build **playlist generators** using discovered clusters.  
- **Feature Engineering**: Create new **human-defined** features to improve clustering.  
- **Graph-Based Model**: Explore **multi-armed bandit** approaches for music recommendations based on user engagement (e.g., skip rates).  

## References  

- **Spotify API Documentation**: [Get Audio Features](https://developer.spotify.com/documentation/web-api/reference/get-audio-features)  
- **Scikit-Learn**: [Machine Learning in Python](https://scikit-learn.org/stable/)  
- **Matplotlib**: [Data Visualization](https://matplotlib.org/)  
- **Seaborn**: [Statistical Data Visualization](https://seaborn.pydata.org/)  
- **Relevant Papers on Music Evolution & Clustering**:  
  - Mauch et al. (2015). *The Evolution of Popular Music: USA 1960–2010*.  
  - MacQueen, J. (1967). *Some Methods for Classification and Analysis of Multivariate Observations*.  

For additional details, see the **full project write-up**.  
