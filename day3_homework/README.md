# DAY 3 HOMEWORK SUMMARY

In this homework, I built a search system on top of my own dataset.

I first indexed my chunked GitHub documentation and implemented text-based search using keyword matching. Then, I added vector search using embeddings to capture semantic meaning. Finally, I combined both approaches into a hybrid search system.

After testing all three methods, I observed that they returned similar results for my use case. This helped me understand that the limitation was not the search methods, but the nature of the dataset.

The main takeaway for me was: The quality of the data has a bigger impact than the search algorithm itself.

## Search Implementation

### Step 1 — Preparing the Search Dataset

In this step, I prepared my chunked data for search.

I transformed each chunk into a structured format including:

chunk
title
description
filename

This allowed me to use the same dataset for both lexical and vector-based search.

Step 2 — Text Search (Lexical Search)

I implemented text-based search using the minsearch library.

Logic

I matched the query with document fields based on keyword overlap.
Documents containing more matching words were ranked higher.

Purpose

This approach is simple, fast, and easy to debug.
I used it as a baseline to understand how basic search behaves.

### Step 3 — Vector Search

I implemented semantic search using embeddings.

Logic

I converted each document chunk into a vector using a transformer model.
Then, I encoded the query and calculated similarity scores between the query and document vectors.

Model used
multi-qa-distilbert-cos-v1
Purpose

Unlike text search, this approach focuses on meaning rather than exact keyword matching.

### Step 4 — Hybrid Search

I combined both text search and vector search into a hybrid approach.

Logic
First, I retrieved results using text search
Then, I retrieved results using vector search
Finally, I merged the results and removed duplicates
Purpose

This allowed me to benefit from both keyword precision and semantic understanding.

### Step 5 — Modular Search Functions

To make the system reusable, I organized the logic into functions:

text_search(query)
vector_search(query)
hybrid_search(query)

This made it easier to test and compare different approaches.


