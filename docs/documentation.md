# Project Technical Documentation

# 5. Data Research and Acquiring Effort
To achieve the project goals, we researched several data sources and chose the **YouTube Data API v3**. We developed a robust data acquisition pipeline in Python to fetch high-volume comment threads (up to 50,000 comments) using authenticated API requests.

# 6. Data Description and Understanding
* **Primary Source:** YouTube video comments and metadata.
* **Key Fields:** * `Comment Body`: Text analysis source.
    * `Timestamp`: The temporal marker for highlights.
    * `Like Count`: Engagement metric.
* **Understanding:** Analysis showed that comments with timestamps are the most reliable indicators of "Highlights."

# 7. Data Primary Cleaning and Transformation
We implemented an ETL process that includes:
* **Text Normalization:** Removing noise and special characters from Arabic/English text.
* **Extraction:** Using Regular Expressions (Regex) to identify time-stamps.
* **Translation:** Automating translation via `deep-translator` to support multilingual NLP.

# 8. Data Visualization and Insights
The dashboard generates interactive Plotly charts:
* **Emotion Breakdown:** Categorizing audience sentiment.
* **Engagement Heatmap:** Visualizing where the emotional intensity is highest across the video duration.

# 9. Dashboard Design & Business Insights
The dashboard is designed using **Streamlit** with a custom **"Cherry Red"** theme. It provides content creators with "Business Insights" by instantly identifying which segments of a long video are worth repurposing as short-form content.

# 10. Advanced Analytics and AI Modeling
We utilized a **Hybrid Sentiment Model**:
* **Rule-based Engine:** For Arabic slang and emojis.
* **Deep Learning Model:** `DistilRoBERTa` for multi-label emotion classification (Happy, Sad, Angry, etc.).

# 11. Tools Research and Selection Effort
* **Backend:** Python.
* **Analysis:** Pandas, NumPy, Transformers.
* **Frontend:** Streamlit, CSS Injection.
* **Visualization:** Plotly.

# 12. Project Deployment Effort
The application is deployed on **Render**, managed via a `requirements.txt` file which handles all library dependencies, ensuring a stable production environment.

# 13. Results
The system successfully identifies the "Top 3 Golden Moments" in any given video, achieving results that correlate strongly with human-driven engagement metrics.

# 14. References
1. Google Cloud: YouTube Data API v3 Documentation.
2. Streamlit.io: API Reference and Deployment Guides.
3. Hugging Face: Transformers Model Hub.
