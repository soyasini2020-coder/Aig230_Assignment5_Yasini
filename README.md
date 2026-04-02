# AIG230 Natural Language Processing - Assignment 5

## Course Information
- Prof: David Quispe
- Term: Winter 2026
- Institution: Seneca Polytechnic

## Corpus Choice
I selected Option A from NLTK Gutenberg and used `austen-emma.txt`.

## Part A - Text Preprocessing (50%)

### A1. Load the corpus
The notebook loads the corpus through NLTK and reports:
- Total number of characters
- Total number of tokens before preprocessing

### A2. Preprocess
Preprocessing pipeline used:
- Lowercasing
- Tokenization
- Removal of punctuation/non-alphabetic tokens
- Stopword removal
- Lemmatization

Why these choices:
- Lowercasing reduces vocabulary duplication.
- Removing punctuation reduces noise.
- Stopword removal improves interpretability for BoW/TF-IDF.
- Lemmatization preserves meaningful base forms better than stemming for literary text.

The notebook also reports after preprocessing:
- Total number of tokens
- Vocabulary size
- Top 20 most frequent tokens with counts

### A3. Reflection
Preprocessing improves consistency and helps vector-based features focus on informative terms. However, very aggressive filtering can remove useful grammatical context for language modeling. For embeddings, richer context often gives better semantic neighborhoods. Overall, preprocessing should be selected based on the downstream task.

## Part B - Text Representation (25%)

### B1. Create documents
I split the corpus into fixed-size chunks of 500 tokens.

Justification:
- Produces enough documents for comparison
- Keeps local context in each document
- Fits the required 500-1000 token guideline

### B2. Vectorize
The notebook builds:
- Bag-of-Words with CountVectorizer
- TF-IDF with TfidfVectorizer

It reports matrix shapes and shows top 15 TF-IDF terms for two documents, followed by interpretation.

### B3. Similarity
The notebook computes cosine similarity from TF-IDF vectors and reports:
- Most similar pair of documents (excluding self-similarity) and score
- A short explanation of a notable similarity
- A small 5x5 similarity table

## Part C - Word Embeddings (25%)

### C1. Prepare training data
I used sentence-level token lists built from the corpus preprocessing pipeline (while preserving context useful for embeddings).

### C2. Train Word2Vec
Model and hyperparameters:
- vector_size = 100
- window = 5
- min_count = 3
- sg = 0 (CBOW)
- epochs = 10

Why these values:
- Suitable model size for a single-book corpus
- Context window captures nearby relationships
- Rare-token filtering reduces noise
- CBOW is stable on smaller datasets
- 10 epochs supports convergence

### C3. Explore similarity
The notebook tests 5 target words and prints top 10 most similar terms, then provides interpretation of whether neighbors are reasonable.

### C4. Analogies
The notebook runs 3 analogy queries and explains why results may be weaker on a small corpus.

## Software Used
- Python 3
- Jupyter Notebook
- NLTK
- NumPy
- pandas
- scikit-learn
- gensim
- matplotlib

