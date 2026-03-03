Unsupervised text clustering project applying TF-IDF and multiple clustering algorithms to group news articles into semantic categories, evaluated using ARI, NMI, and F1-score.

#  Unsupervised News Article Clustering Using TF-IDF and Multiple Clustering Algorithms

## Abstract

This study presents a comparative analysis of unsupervised clustering techniques applied to a multi-class news article dataset. Natural Language Processing (NLP) techniques were employed for text preprocessing and feature extraction using TF-IDF representations. Three clustering algorithms were evaluated: **KMeans**, **AgglomerativeClustering**, and **DBSCAN**. Performance was assessed using external clustering evaluation metrics including ARI, NMI, and V-Measure. Experimental results indicate that K-Means achieved the most consistent and interpretable clustering performance.

## 1. Introduction

Text clustering is a fundamental task in Natural Language Processing and Information Retrieval. The objective of this project is to evaluate the effectiveness of classical clustering algorithms in grouping news articles into coherent semantic categories without supervised training.

The dataset contains news articles categorized into five domains:

* Business
* Entertainment
* Sport
* Tech
* Politics

Although true labels are available, they are used strictly for evaluation purposes.

## 2. Methodology

### 2.1 Data Collection and Preparation

The dataset consists of 1,730 news articles stored as individual text files. Articles were programmatically loaded and labeled according to directory structure.

### 2.2 Text Preprocessing

The following preprocessing steps were applied:

* Lowercasing
* Removal of punctuation and numeric characters
* Stopword removal (NLTK)
* Tokenization
* Lemmatization using WordNet Lemmatizer

This ensured standardized and noise-reduced textual input.


## 3. Feature Extraction

Two feature extraction methods were explored:

* Bag-of-Words (CountVectorizer)
* TF-IDF (TfidfVectorizer)

TF-IDF representation with 4,000 maximum features was selected for clustering experiments due to its superior representation of term importance across documents.

Final TF-IDF matrix dimension:

**1730 × 4000**

## 4. Clustering Algorithms

The following unsupervised learning algorithms were implemented:

### 4.1 K-Means Clustering

Partition-based clustering minimizing within-cluster variance.

### 4.2 Agglomerative Hierarchical Clustering

Bottom-up clustering using cosine distance and average linkage.

### 4.3 DBSCAN

Density-based clustering using cosine distance matrix.

## 5. Evaluation Metrics

Since clustering is unsupervised, external validation metrics were used:

* Adjusted Rand Index (ARI)
* Normalized Mutual Information (NMI)
* Homogeneity
* Completeness
* V-Measure
* Silhouette Score
* Micro Precision / Recall / F1 (Hungarian label alignment)

## 6. Results

### 6.1 K-Means Performance

* ARI: 0.639
* NMI: 0.689
* V-Measure: 0.689
* F1-Score: 0.731

K-Means achieved the highest overall performance and produced semantically coherent clusters.

### 6.2 Agglomerative Clustering Performance

* ARI: 0.530
* NMI: 0.607
* V-Measure: 0.607
* F1-Score: 0.607

Hierarchical clustering showed moderate performance with reasonable topic separation.

### 6.3 DBSCAN Performance

* ARI: 0.446
* NMI: 0.616
* F1-Score: 0.493

DBSCAN generated several fine-grained clusters and topic-specific groupings but struggled to align with global category structure.

## 7. Cluster Interpretation

Top TF-IDF terms per cluster were extracted for semantic validation.

Example (K-Means clusters):

* Cluster: Film, Music, Award → Entertainment
* Cluster: Government, Party, Minister → Politics
* Cluster: Company, Market, Share → Business
* Cluster: Game, Player, Match → Sport

This demonstrates that clustering effectively captured underlying thematic structures.

## 8. Visualization

To better understand cluster separability:

* PCA (2D projection)
* t-SNE visualization
* Silhouette analysis
* Dendrogram for hierarchical clustering
* Top-term bar plots

Visualizations confirm that K-Means produced clearer global separation compared to DBSCAN.

Experimental findings suggest:

* Partition-based clustering performs well on high-dimensional sparse TF-IDF vectors.
* Density-based clustering struggles with global document separation in sparse vector space.
* Proper feature representation significantly influences clustering quality.
* External validation metrics are essential when ground truth labels exist.

## 10. Conclusion

This study demonstrates that classical clustering techniques can effectively group news articles based on textual similarity. Among the evaluated models, K-Means provided the best balance between cluster coherence and external metric performance.

Future improvements may involve dimensionality reduction techniques (e.g., LSA), contextual embeddings (Word2Vec, BERT), or advanced topic modeling approaches.

## Technologies Used

* Python
* pandas
* NumPy
* NLTK
* scikit-learn
* matplotlib
