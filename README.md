# Distributional Semantics for Character Dialogue Similarity

## Introduction

This project focuses on analyzing character dialogue using distributional semantics to capture and compare linguistic patterns among characters from a TV series. By generating vector representations of characters based on their spoken dialogue, the system assesses semantic similarity between known characters and unseen test characters using cosine similarity and ranking metrics. The pipeline incorporates advanced preprocessing, linguistic feature engineering, and contextual embedding techniques.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Experiments & Results](#experiments--results)
- [Insights](#insights)
- [Dependencies](#dependencies)
- [License](#license)

## Features

- Token-level preprocessing: lemmatization, stopword and punctuation removal.
- Feature extraction: N-grams, POS tagging, TF-IDF.
- Scene-level context embedding: incorporating surrounding dialogue.
- Character vector generation from dialogue corpora.
- Similarity analysis using cosine distance.
- Evaluation with mean rank, cosine similarity, and accuracy.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/Aishuwu/distributional-semantics-dialogue.git
   cd distributional-semantics-dialogue
   ```

2. Create and activate a virtual environment:
   ```bash
   python -m venv env
   source env/bin/activate  # On Windows: env\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. Extract the ZIP archive and open the project notebook or scripts.

2. Run the preprocessing and feature extraction functions to build document-term matrices.

3. Train the model and compute similarity scores between training and held-out character vectors.

4. Generate evaluation metrics:
   - Cosine similarity heatmaps
   - Character vector ranking results
   - Accuracy of top-1 matches

## Dataset

- Dialogue data is grouped by character and scene.
- Each character's dialogue is used to generate a vector based on lexical and contextual features.
- Evaluation is performed by holding out one character instance and comparing it to others.

## Methodology

### Preprocessing
- **Tokenization** using NLTK
- **Lowercasing**
- **Punctuation and Stopword Removal**
- **Lemmatization** using WordNet

### Feature Extraction
- N-gram vectorization (uni- and bigrams)
- TF-IDF transformation
- POS-tag filtering (optional)

### Context Integration
- Adds other characters’ dialogue from the same scene to enrich the target character’s vector.

### Similarity Computation
- Cosine similarity matrix is calculated between training and held-out vectors.
- Characters are ranked by proximity.

## Experiments & Results

| Stage                         | Mean Rank | Cosine Similarity | Accuracy |
|------------------------------|-----------|-------------------|----------|
| Initial Run                  | 4.2       | 0.891             | 10%      |
| After Preprocessing          | 3.8       | 0.911             | 30%      |
| After Feature Extraction     | 2.2       | 0.907             | 50%      |
| After Adding Context         | 1.7       | 0.960             | 70%      |
| Final Grid Search Model      | 1.1       | 0.960             | 90%      |

- **Best Parameters**: `ngram_range=(1,2)`, `use_idf=True`

## Insights

- Close similarity observed between characters with strong dialogue overlap (e.g., Chandler and Joey).
- Distinct styles observed for outliers (e.g., generic “Other_Male” or “Other_None”).
- Contextual dialogue significantly improves model performance by reducing rank and increasing accuracy.

## Dependencies

```
numpy
scikit-learn
nltk
matplotlib
seaborn
pandas
```

Install them via:
```bash
pip install -r requirements.txt
```

## License

This project is made available for academic and non-commercial research use.
