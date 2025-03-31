# Song Lyrics Genre Classification with LLM (Ollama)

## Project Overview
This project explores the ability of large language models (LLMs) to classify song lyrics into genres using zero-shot and few-shot prompting. 
The workflow includes:
- Data preprocessing
- Zero-shot classification with the Ollama library
- Few-shot classification with example-based learning
- Performance evaluation using precision, recall, and F1-score
- Comparative analysis of results

## Dataset

Two datasets were used:
- `genreLyrics.csv`: Raw dataset containing song lyrics and genre labels.
- `cleaned_genreLyrics_with_id.csv`: Preprocessed version with cleaned text and stripped whitespace.

Each entry contains:
- `id`: Unique identifier  
- `genre`: Genre label  
- `lyrics`: Song lyrics  

## Requirements
- Python
- Required packages:
  ```bash
  pip install ollama pandas scikit-learn numpy matplotlib

## Repository Structure
```
├── genreLyrics.csv
├── cleaned_genreLyrics_with_id.csv
├── A3_Part2.ipynb
├── README.md
```

## How to Run

1. Install Ollama and download your model (e.g. `llama3.2`).
2. Install dependencies:
   ```
   pip install ollama pandas scikit-learn
   ```
3. Run `A3_Part2.ipynb` in Jupyter Notebook.
4. Follow the evaluation and visualization cells.

## Code Structure
1. Data Preprocessing (clean_data())
Reads and cleans raw data

Handles missing values and whitespace

Saves cleaned data to cleaned_genreLyrics_with_id.csv

2. Classification Methods
    a. Zero-Shot Prompting  
The model was directly prompted with the lyrics and a fixed list of genres. No prior examples were provided.
    b. Few-Shot Prompting  
A small number of examples (up to 3 per genre) were prepended to the prompt to guide the model with context.

3. Performance was evaluated on a test set using:
- Precision
- Recall
- F1 Score

We used both macro-averaged metrics and per-genre analysis.

## Results Summary

| Strategy    | Macro Precision | Macro Recall | Macro F1 |
|-------------|-----------------|---------------|----------|
| Zero-Shot   | 0.113           | 0.098         | 0.086    |
| Few-Shot    | 0.074           | 0.033         | 0.038    |

Conclusion: Zero-shot prompting outperformed few-shot in overall metrics, especially in common genres like Rock, Pop, and Hip-Hop. Few-shot prompting struggled likely due to randomly selected examples.

## Genre-Level Insights

Genres such as Jazz, Folk, Indie, and R&B showed zero F1 scores in both strategies. These may require more training data or better prompting techniques.

## Visual Comparison

The notebook includes performance visualizations comparing precision, recall, and F1 across genres for both strategies. This helps illustrate where the model performs best and where it fails.

## Suggestions for Improvement (additional)

- Curate stronger few-shot examples (avoid random sampling).
- Fine-tune the model on labeled lyrics.
- Apply label normalization and filtering.
- Explore other prompting strategies (e.g., chain-of-thought).
