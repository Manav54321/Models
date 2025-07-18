# Document Similarity Search with Sentence Transformers

This repository presents a minimal and effective implementation of semantic document retrieval using vector embeddings and cosine similarity. The system is designed to identify the document that best matches the meaning of a user's input query.

---

## Overview

Traditional search methods rely on keyword overlap. This method improves upon that by leveraging **pretrained transformer-based sentence embeddings**, allowing retrieval based on *semantic similarity* rather than lexical similarity.

The process involves:

* Embedding each document and query into a high-dimensional space.
* Computing cosine similarity between the query vector and document vectors.
* Returning the document with the highest semantic alignment.

---

## Mathematical Foundation

### 1. Vector Representation

Each document `d_i` and query `q` is passed through a transformer model `f`, which encodes the text into an embedding vector:

    d_i = f(d_i),   q = f(q)

Where `f` maps raw text to ℝ^384 using a pre-trained model.

---

### 2. Cosine Similarity

Similarity between query and document embeddings is calculated as:

    cos_sim(q, d_i) = (q · d_i) / (||q|| * ||d_i||)

This metric reflects the angle between vectors. Higher values indicate greater similarity in meaning.

### 3. Ranking Mechanism

All cosine scores are computed, sorted, and the top document is returned:

```python
sorted_scores = sorted(enumerate(scores), key=lambda x: x[1])
document_index, score = sorted_scores[-1]
```

---

## Embedding Model

* **Model Name**: `sentence-transformers/all-MiniLM-L6-v2`
* **Architecture**: Distilled bi-encoder (Transformer-based)
* **Embedding Dimension**: 384
* **Provider**: HuggingFace Model Hub

---

## Example Run

```python
query = "Kylie"
```

Returns:

```
query: Kylie
best_match: Kylie Jenner commands attention with her signature style, glamorous beauty, and trendsetting influence on social media.
similarity_score: 0.7823
```
![Screenshot 2025-07-03 at 3 18 51 PM](https://github.com/user-attachments/assets/0c48f091-cf57-44b9-800c-9b3f757cb3c2)

---

## Dependencies

Install required libraries:

```bash
pip install -r requirements.txt
```

---

## Run the Script

```bash
python /Users/manavdesai/Desktop/GitHub/Langchain_Models/document_search_app.py.py
```

---
