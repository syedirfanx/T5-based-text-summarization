# NLP Text Summarization

A Python implementation comparing two fundamental approaches to automatic text summarization: extractive and abstractive methods.

---

## Overview

Text summarization is the task of condensing a document into a shorter form while preserving its key information. This project implements and compares two main NLP approaches:

- **Extractive Summarization**: Scores and selects the most important sentences from the original text without modification.
- **Abstractive Summarization**: Generates new sentences that capture the main ideas, similar to how a human would summarize.

---

## Extractive Summarization

### Approach

The extractive pipeline uses NLTK for text preprocessing and a frequency-based sentence scoring method to identify the most informative sentences.

### Methodology

1. **Preprocessing**: Tokenize the input text into sentences and words, then remove stopwords and punctuation using NLTK.
2. **Sentence Scoring**: Score each sentence by counting the frequency of its meaningful words.
3. **Summary Generation**: Select the top N highest-scoring sentences using a max-heap to form the summary.

### Example Output

Given a 17-sentence input text, the model extracts the 5 highest-scoring sentences as the summary.

---

## Abstractive Summarization

### Approach

The abstractive pipeline uses the T5-large pre-trained transformer model from Hugging Face to generate human-like summaries from the input text.

### Methodology

1. **Tokenization**: Encode the input text with the T5 tokenizer using the `summarize:` task prefix.
2. **Generation**: Generate a summary using beam search with 4 beams, controlling output length with `min_length` and `max_length` parameters.
3. **Decoding**: Decode the output token IDs back into readable text.

### Model Details

| Parameter | Value |
|---|---|
| Model | t5-large |
| Max Input Length | 512 tokens |
| Max Output Length | 150 tokens |
| Min Output Length | 40 tokens |
| Num Beams | 4 |
| Length Penalty | 2.0 |

---

## Comparison

| Aspect | Extractive | Abstractive |
|---|---|---|
| Method | Sentence selection | Text generation |
| Output | Sentences from original text | Newly generated sentences |
| Model | NLTK frequency scoring | T5-large Transformer |
| Coherence | Moderate | High |
| Faithfulness | High | Model-dependent |

---

## Technologies Used

- Python
- NLTK
- NumPy
- Pandas
- Hugging Face Transformers
- PyTorch
