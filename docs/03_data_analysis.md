# Data Analysis Methodology

## Hybrid Sentiment Analysis
The project uses a sophisticated engine that combines:
* **Arabic Lexicon:** For detecting local dialects and emojis (e.g., 'كفو', 'وحش').
* **Deep Learning Model:** Utilizing the `DistilRoBERTa` model through the Hugging Face `transformers` library for complex emotion detection.

## The "Golden Moment" Scoring
We developed a composite formula to detect video highlights:
`Score = Comment_Count × Average_Emotion_Heat × Diversity_Bonus`

## Tools & Libraries
* **Pandas & NumPy:** For data cleaning and numerical transformations.
* **Deep Translator:** To handle multilingual comment processing.
* **Transformers (PyTorch/TF):** For running the emotion classification model.
