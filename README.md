# Document Similarity Detection using MinHash and LSH

A Python implementation for detecting similar documents in large text collections using MinHash signatures and Locality-Sensitive Hashing (LSH) techniques.

## Overview

This project implements an efficient document similarity detection system that can handle large document collections by using:
- **MinHash**: For creating compact document signatures
- **LSH (Locality-Sensitive Hashing)**: For fast approximate similarity search
- **Jaccard Similarity**: For measuring document similarity based on shingle overlap

## Dataset

- **Source**: 20 Newsgroups dataset (downloaded from Google Drive)
- **Format**: Text files organized in newsgroup categories
- **Size**: Large collection of newsgroup posts and articles

## Key Features

### 1. Document Preprocessing
- Text tokenization using NLTK
- Stop word removal (English)
- Alphanumeric token filtering

### 2. Shingling
- Converts documents into k-shingles (default k=9)
- Creates overlapping word sequences for similarity comparison

### 3. MinHash Signatures
- Generates compact document fingerprints
- Configurable number of hash functions (default: 100)
- Preserves Jaccard similarity estimates

### 4. LSH Index
- Fast candidate pair detection
- Adjustable similarity threshold (default: 0.7)
- Efficient querying for large document collections

### 5. Similarity Computation
- Jaccard similarity calculation between candidate pairs
- Configurable similarity threshold for final results

## Technical Implementation

```python
# Key components:
- Shingle generation: get_shingles(tokens, k=9)
- MinHash computation: compute_minhash(shingles, num_hashes=100)
- LSH indexing: MinHashLSH(threshold=0.7, num_perm=100)
- Similarity measurement: jaccard_similarity(set1, set2)
```

## Requirements

```
datasketch
nltk
numpy
gdown
```

## Installation & Usage

1. **Install Dependencies**:
   ```bash
   pip install datasketch nltk numpy gdown
   ```

2. **Download NLTK Resources**:
   ```python
   nltk.download('punkt')
   nltk.download('stopwords')
   ```

3. **Run the Analysis**:
   - The script automatically downloads the 20 Newsgroups dataset
   - Processes all documents and creates MinHash signatures
   - Builds LSH index for fast similarity search
   - Outputs similar document pairs with similarity scores

## Configuration Parameters

- **Shingle Size**: `k=9` (adjustable for different granularity)
- **Hash Functions**: `num_hashes=100` (affects accuracy vs. speed)
- **LSH Threshold**: `threshold=0.7` (candidate pair detection)
- **Similarity Threshold**: `similarity_threshold=0.5` (final filtering)

## Output

The system produces:
- **Candidate Pairs**: Documents that may be similar (LSH results)
- **Similar Pairs**: Verified similar documents with Jaccard similarity scores
- **Document Statistics**: Token counts, shingle examples, and signatures

## Performance Benefits

- **Scalability**: O(n) complexity instead of O(n²) for pairwise comparison
- **Memory Efficiency**: Compact MinHash signatures vs. full document storage
- **Speed**: LSH enables sub-linear similarity search
- **Accuracy**: Maintains similarity estimation quality

## Use Cases

- **Plagiarism Detection**: Identify copied or similar academic papers
- **Content Deduplication**: Remove duplicate articles from news feeds
- **Recommendation Systems**: Find similar documents for content suggestions
- **Information Retrieval**: Cluster similar documents for better organization

## Algorithm Workflow

1. **Document Loading**: Read all text files from the dataset
2. **Preprocessing**: Tokenize and filter text content
3. **Shingling**: Generate k-shingles for each document
4. **MinHash**: Create compact signatures preserving similarity
5. **LSH Indexing**: Build hash tables for fast candidate retrieval
6. **Similarity Verification**: Compute exact Jaccard similarity for candidates

## Future Enhancements

- Support for different similarity metrics (Cosine, Edit distance)
- Real-time document similarity API
- Visualization of similarity clusters
- Integration with document databases
- Multi-language support
