# Advanced Analytics & Performance

## Optimization
To ensure the application can handle large datasets (up to 50,000 comments), we implemented **Streamlit Caching (`@st.cache_data`)**. This reduces API latency and prevents redundant processing.

## Sentiment-Driven Insights
Beyond simple counting, the system identifies "Emotive Signals." By assigning weights to different emotions (e.g., Controversial 1.5, Funny 1.4), the tool highlights moments that triggered the strongest audience reactions.
