# Distributional Semantics: Character Dialogue Similarity Analysis

## Introduction

This project explores distributional semantics to analyze and compare dialogue styles among fictional characters based on their spoken lines. By converting dialogue into vector space representations using token-level and contextual linguistic features, the system evaluates semantic similarity between characters. This methodology offers insights into character roles, relationships, and linguistic uniqueness.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Experiments & Evaluation](#experiments--evaluation)
- [Results](#results)
- [Insights](#insights)
- [Dependencies](#dependencies)
- [License](#license)

## Features

- Text preprocessing with lemmatization, stopword removal, and POS tagging.
- Flexible n-gram and TF-IDF vectorization for character dialogues.
- Option to incorporate contextual dialogue from surrounding characters.
- Cosine similarity scoring between character vectors.
- Evaluation via mean rank, accuracy, and confusion matrix visualizations.
- Interactive error analysis with heatmaps and sorted similarity matrices.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/distributional-semantics-dialogue.git
   cd distributional-semantics-dialogue
   ```

2. Create and activate a virtual environment (optional):
   ```bash
   python -m venv env
   source env/bin/activate  # Windows: env\Scripts\activate
   ```

3. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. Open and run the notebook:
   ```
   NLP_Assignment_2_distributional_semantics.ipynb
   ```

2. Follow the steps:
   - Load and preprocess character dialogue data.
   - Generate vector representations for characters using TF-IDF.
   - Compute cosine similarities and rank characters.
   - Evaluate performance based on mean rank, cosine similarity, and classification accuracy.

## Dataset

- Dialogue dataset grouped by speaker and scene.
- Each document represents one character’s combined speech across scenes.
- Evaluation includes identifying a held-out character using semantic similarity to training vectors.

## Methodology

### Preprocessing
- Convert text to lowercase.
- Remove punctuation and stopwords.
- Apply lemmatization using NLTK’s WordNetLemmatizer.
- Optionally filter by POS tags for more targeted features.

### Feature Extraction
- Vectorize dialogues using `CountVectorizer` or `TfidfVectorizer`.
- Use `ngram_range` for unigram or bigram feature expansion.
- Apply IDF weighting for more informative term representation.

### Context Integration
- Surrounding character dialogue (within the same scene) is added to simulate richer discourse context.
- Improves vector generalization and similarity clustering.

### Evaluation
- For each held-out character vector, rank all training characters based on cosine similarity.
- Metrics:
  - **Mean Rank**: Lower is better.
  - **Cosine Similarity**: Higher is better.
  - **Accuracy**: Top-1 match correctness.

## Experiments & Evaluation

| Configuration            | Mean Rank | Cosine Similarity | Accuracy |
|--------------------------|-----------|-------------------|----------|
| Basic Model              | 4.2       | 0.891             | 10%      |
| With Preprocessing       | 3.8       | 0.911             | 30%      |
| With N-Gram + IDF        | 2.2       | 0.907             | 50%      |
| With Context Integration | 1.7       | 0.960             | 70%      |
| Grid Search Optimization | 1.1       | 0.960             | 90%      |

## Results

- Final model achieved **90% accuracy** with top-1 ranking on test character dialogue.
- Contextual dialogue dramatically improved semantic coherence in character vectors.
- POS-filtering and bigram analysis helped separate close characters.

## Insights

- Characters with frequent shared scenes and linguistic patterns cluster closely.
- Outlier or generic characters (e.g., "Other_None") rank poorly, as expected.
- Incorporating context significantly boosts the ability to distinguish similar speakers.

## Dependencies

```
nltk
numpy
pandas
scikit-learn
matplotlib
seaborn
```

Install with:
```bash
pip install -r requirements.txt
```

## License

This project is available for academic and research use only.
