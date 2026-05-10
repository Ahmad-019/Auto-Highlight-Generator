# Project Technical Documentation

# 5. Data Research and Acquiring Effort
To achieve the project goals, we researched several data sources and chose the **YouTube Data API v3**. We developed a robust data acquisition pipeline in Python to fetch high-volume comment threads (up to 50,000 comments) using authenticated API requests. This ensures the data is real-time and reflects actual audience engagement.

# 6. Data Description and Understanding
* **Primary Source:** YouTube video comments and metadata.
* **Key Fields:** * `Comment Body`: The raw text used for sentiment analysis.
    * `Timestamp`: The temporal marker used to sync comments with video highlights.
    * `Like Count`: Used as a weight to measure the reliability of the signal.
* **Understanding:** Initial analysis showed that comments containing timestamps or emotional keywords are the most reliable indicators of "Highlights."

# 7. Data Primary Cleaning and Transformation (ETL)
We implemented a custom ETL (Extract, Transform, Load) process that includes:
* **Text Normalization:** Removing noise, repetitive characters, and normalizing Arabic/English text.
* **Temporal Parsing:** Using Regular Expressions (Regex) to identify and convert string timestamps (e.g., "5:20") into numerical seconds for timeline mapping.
* **Translation:** Automating translation via the Google Translator engine to support deep-learning models that require English input.

# 8. Data Visualization and Insights
The dashboard generates interactive Plotly charts:
* **Emotion Distribution:** Categorizing audience sentiment into 6 core emotions.
* **Engagement Heatmap:** Visualizing "Emotional Spikes" across the video duration, allowing us to see exactly where the audience was most active.

# 9. Dashboard Design & Business Insights
The dashboard is designed using **Streamlit** with a custom **"Cherry Red"** professional theme. From a BI perspective, this tool provides instant "Actionable Insights" by identifying which segments of a long video are worth repurposing for marketing or short-form content.

# 10. Advanced Analytics and AI Modeling
We utilized a **Hybrid Sentiment Model** to ensure maximum accuracy:
* **Rule-based Engine:** Specifically designed to detect Arabic slang, dialects, and emojis (e.g., 'كفو', 'وحش').
* **Deep Learning Model:** Leveraging the `DistilRoBERTa` transformer for multi-label emotion classification (Happy, Sad, Angry, Funny, etc.).
* **Scoring Algorithm:** We developed a unique formula: `Score = Comment_Count × Emotion_Heat × Diversity`.

# 11. Tools Research and Selection Effort
* **Language:** Python (The industry standard for Data Science).
* **AI & NLP:** Pandas, Transformers, and Deep-Translator.
* **Frontend:** Streamlit with custom CSS injection for a professional UI.
* **Visualization:** Plotly for dynamic and interactive BI charts.

# 12. Project Deployment Effort
The application is deployed on **Render**, providing a cloud-based URL for public access. We managed all dependencies using a `requirements.txt` file to ensure the environment is stable and scalable.

# 13. Results
The system successfully identifies the "Top 3 Golden Moments" in any video. Testing showed that the AI-detected highlights match the most viral parts of the videos, proving the effectiveness of the scoring algorithm.

# 14. References
* Google Cloud Platform: YouTube Data API v3 Documentation.
* Streamlit Framework: Web Interface and Deployment Guides.
* Hugging Face: Transformers Model Hub (DistilRoBERTa).
* Python Software Foundation: Data Processing Libraries (Pandas, NumPy).
