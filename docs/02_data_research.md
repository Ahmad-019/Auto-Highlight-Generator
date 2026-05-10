# Data Research & Sourcing

## Data Source
The primary data source is the **YouTube Data API v3**. The application programmatically fetches data based on the unique Video ID provided by the user.

## Data Types Collected
1. **Metadata:** Video titles, descriptions, and engagement metrics (Views, Likes).
2. **User Feedback:** Public comments and top-level comment threads.
3. **Textual Content:** Data is retrieved in JSON format and converted into Pandas DataFrames for processing.

## Ethical Standards
All data collection is performed through official Google Cloud API channels, ensuring compliance with privacy standards and YouTube's Terms of Service.
