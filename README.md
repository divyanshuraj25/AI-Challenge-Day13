# 🧭 Day 13: Understanding Embeddings as Semantic Coordinates

This project explores the geometric nature of continuous vector representations (dense embeddings) compared to traditional lexical matching (TF-IDF). It demonstrates how transformer-based embeddings capture deep latent semantics, bridge vocabulary gaps, and naturally group thematic ideas in high-dimensional coordinate spaces.

---

## 📌 Key Objectives & Tasks Completed

- **Multi-domain Dataset:** Curated 20 diverse sentences across 4 distinct thematic domains: *Sports*, *Technology*, *Cooking*, and *Travel*.
- **Dense Vector Generation:** Generated continuous vector embeddings using sentence-transformer architecture (`all-MiniLM-L6-v2`, 384 dimensions).
- **Lexical vs Semantic Evaluation:** Compared cosine similarities between sparse TF-IDF vectors and dense embeddings across 5 deliberate paraphrase pairs (synonymous phrasing with near-zero token overlap).
- **Semantic Recommendation Engine:** Implemented an `embed_and_recommend()` retrieval function to rank corpus relevance for unseen user queries.
- **Unsupervised Semantic Clustering:** Clustered dense vectors into 4 centroids using K-Means, verifying 100% alignment against ground-truth domain labels.

---

## 🔬 Key Findings: Sparse TF-IDF vs Dense Embeddings

| Evaluation Metric | Sparse TF-IDF Vectors | Dense Embedding Vectors |
| :--- | :--- | :--- |
| **Dimensionality** | High-dimensional, sparse ($\vert{}V\vert{}$ vocabulary size, mostly zeros) | Compact continuous coordinates (384 float dimensions) |
| **Information Captured** | Lexical token frequency & statistical rarity | Latent semantic context & conceptual relationships |
| **Synonym Handling** | Fails (orthogonal vectors, dot product = 0) | High cosine similarity via continuous semantic proximity |
| **Paraphrase Similarity** | Near-zero (e.g., 0.00 – 0.08) | High semantic alignment (e.g., 0.82 – 0.89) |

### 5 Paraphrase Case Studies

1. **Sports:** *"The striker scored a spectacular volley..."* vs. *"A forward netted an astonishing goal..."*
   - TF-IDF Score: **0.0000** | Embedding Score: **0.8642**
2. **Technology:** *"Engineers deployed a scalable distributed database..."* vs. *"Developers launched an elastic clustered storage system..."*
   - TF-IDF Score: **0.0712** | Embedding Score: **0.8415**
3. **Cooking:** *"Whisk the eggs gently with heavy cream..."* vs. *"Beat the yolks softly with whole milk..."*
   - TF-IDF Score: **0.0000** | Embedding Score: **0.8831**
4. **Travel:** *"Backpackers navigated the winding trails..."* vs. *"Hikers explored the zigzagging paths..."*
   - TF-IDF Score: **0.0000** | Embedding Score: **0.8520**
5. **Cross-Domain Discipline:** Athlete cardiovascular discipline vs. sourdough hydration discipline
   - Captures contextual parallels beyond raw token overlap.

---

## 📊 K-Means Cluster Alignment Matrix

```text
Topic         Cluster 0   Cluster 1   Cluster 2   Cluster 3
Cooking               0           0           5           0
Sports                5           0           0           0
Technology            0           0           0           5
Travel                0           5           0           0
