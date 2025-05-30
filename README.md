# Turkish Text Normalization and Preprocessing Pipeline

This project is developed for the **CMPE561 (Natural Language Processing)** Master's course at **Boğaziçi University**.  
It implements a modular, rule-based pipeline for **Turkish text normalization and preprocessing**, designed to handle noisy user-generated input. The system is particularly suited for downstream NLP tasks such as syntactic parsing, named entity recognition, or information extraction in domains like social media, OCR output, or conversational text.

---

## 🔧 Components

### 1. Rule-Based Sentence Splitter
- Custom sentence boundary detection using heuristics.
- Handles Turkish-specific edge cases with abbreviation lists and punctuation exceptions.

### 2. Rule-Based Tokenizer
- Robust tokenizer that splits text into meaningful tokens while handling:
  - Turkish clitics (e.g., `-dır`, `-miş`)
  - Punctuation and quotes
  - Multi-Word Expressions (MWEs) via external lexicon files
  - Non-standard entities like:
    - Hashtags
    - Mentions
    - URLs
    - Emails
    - Currency formats

### 3. Morphological Stemmer
- **Stemmer1**: Applies suffix stripping with protected word handling.
- **Stemmer2**: Improves accuracy by sorting suffixes by length and applying them iteratively until no changes occur.

### 4. Pattern Extractors
- Regex-based detection and preservation of special tokens:
  - Dates
  - Numbers
  - Hashtags
  - Emails
  - Links
  - Currency values

### 5. Spelling Correction
- Hybrid correction system:
  - First consults a curated dictionary (`corrected_trspell10.csv`)
  - Falls back to Levenshtein-based nearest word search from a Turkish vocabulary list

### 6. Text Normalizer
- Full normalization pipeline that performs:
  - Lowercasing
  - Pattern preservation
  - Punctuation removal
  - Number-to-word conversion (via [`num2words`](https://pypi.org/project/num2words/))
  - Spell correction

### 7. Stopword Removal
- **Static**: Removes stopwords from a predefined list
- **Dynamic**: Removes tokens based on frequency threshold (e.g., > 20 times in corpus)

---

## Features

- Fully modular design: each module can be used independently
- Purely rule-based: no need for pretrained models
- High interpretability and easy customization
- Lightweight and efficient
- Suited for preprocessing Turkish texts from noisy domains

