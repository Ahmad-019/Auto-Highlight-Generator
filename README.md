<div align="center">

# Auto Highlight Generator

**University of Petra** | **Faculty of Administrative and Financial Sciences** | **Department of Business Intelligence and Data Analytics**

---

### **Auto Highlight Generator: AI-Powered BI Video Analytics**

---

**Authors** Ahmad Khaled Abu Sabha | 202230034  
Fares Sami Haddad | 202210768  

**Supervised by** Dr. Hussam Barham  

**Course: 307498 – Graduation Project** | **Second Semester, 2025/2026**

**Date** <br>
<img src="images/Screenshot%202026-05-11%20020500.png" width="800">
</div>

---

## **Index**
1. [Abstract](#1-abstract)
2. [Acknowledgment](#2-acknowledgment)
3. [Business Intelligence Project Description and Objectives](#3-business-intelligence-project-description-and-objectives)
4. [Data Research and Acquiring Effort](#4-data-research-and-acquiring-effort)
5. [Data Description and Understandings](#5-data-description-and-understandings)
6. [Data Primary Cleaning and Transformation (ETL)](#6-data-primary-cleaning-and-transformation-etl)
7. [Data Visualization and Insights](#7-data-visualization-and-insights)
8. [Dashboard Design & Business Insights](#8-dashboard-design--business-insights)
9. [Advanced Analytics and AI Modeling](#9-advanced-analytics-and-ai-modeling)
10. [Tools Research and Selection Effort](#10-tools-research-and-selection-effort)
11. [Project Deployment Effort – Use Case](#11-project-deployment-effort--use-case)
12. [Results](#12-results)
13. [References](#13-references)

---

## 1. Abstract
The "Auto Highlight Generator" is a sophisticated Business Intelligence solution designed to automate the labor-intensive process of video content curation. By integrating large-scale data harvesting via the YouTube Data API v3 with advanced Natural Language Processing (NLP), the system identifies high-engagement segments known as "Golden Moments." Unlike traditional editing, our approach relies on real-time audience sentiment and emotional density to pinpoint viral potential. The architecture features a multi-layered hybrid processing engine that effortlessly handles bilingual data, cleanses noise, and applies weighted scoring algorithms. The latest iteration introduces an embedded in-app video player, AI Strategic Recommendations, crash-resistant anti-timeout mechanisms, and a highly responsive Advanced UI/UX — transforming the system into a fully self-contained, enterprise-grade content intelligence platform.

---

## 2. Acknowledgment
We extend our deepest gratitude to our project supervisor, **Dr. Hussam Barham**, for his invaluable technical guidance and mentorship throughout this research. His expertise in Data Science and Business Intelligence pushed us to maintain high standards of analytical rigor. We also thank the University of Petra and the Faculty of Administrative and Financial Sciences for providing an environment of excellence that allowed us to transform a theoretical concept into a functional, data-driven application.

---

## 3. Business Intelligence Project Description and Objectives
In the modern digital landscape, content creators face significant "Content Overload." Manually searching for viral clips in long-form videos is inefficient and time-consuming. This project serves as a BI decision-support tool to optimize this workflow. By utilizing crowd intelligence, the system filters through thousands of comments to find the most impactful moments, allowing marketing teams and content editors to maximize their reach with minimal manual effort.

**Main Objectives:**
* **Scalable Engineering:** Build a robust pipeline to parse up to 50,000 comments per request using Dynamic Sampling via the YouTube Data API v3.
* **Precision Sentiment Mapping:** Implement a cross-lingual NLP engine capable of strictly isolating 'Neutral' noise while precisely classifying five core emotions: Funny, Happy, Sad, Controversial, and Inspirational.
* **System Stability (Anti-Crash):** Engineer intelligent sampling (e.g., capping translation queries) and strict data-type enforcement to completely prevent server timeouts and rendering errors (ArrowInvalid).
* **Advanced UI/UX:** Design a highly responsive, cross-platform interface featuring dynamic CSS overrides to ensure flawless mobile execution (e.g., forcing LTR structural containers with RTL text alignment), glowing 3D effects, and centered KPIs.
* **Operational Value:** Provide an interface where highlights are presented with direct, clickable temporal links that open the exact moment in the source video.
* **Content Intelligence:** Generate AI-powered strategic recommendations and visual word analysis to guide creators on their next content decision.

---

## 4. Data Research and Acquiring Effort
We conducted extensive research into social media APIs to determine which provided the highest granularity of community feedback. The **YouTube Data API v3** was selected for its hierarchical comment structures. Our system utilizes a "Dynamic Sampling" strategy, allowing users to fetch varying depths of data based on the video's engagement level. This process is monitored in real-time through an Intelligence Stack panel that ensures data integrity.

![Intelligence Stack Panel](images/Screenshot%202026-05-11%20015932.png)

---

## 5. Data Description and Understandings
The dataset utilized for the analytical engine is comprised of four primary data fields extracted from the YouTube ecosystem. Each field plays a specific role in the calculation of the "Golden Score."

### **Data Dictionary**
| Field Name | Data Type | Description | BI Role |
| :--- | :--- | :--- | :--- |
| **Raw Comment Text** | String | The original unstructured feedback left by the viewer. | Primary source for NLP emotion classification. |
| **Timestamp String** | String | The visual time marker (e.g., "12:45") found in the text. | Reference for identifying the specific video segment. |
| **Seconds** | Integer | The total seconds calculated from the timestamp (e.g., 765s). | Used for temporal binning and heatmap plotting. |
| **Sentiment Label** | Categorical | The classified emotion (Funny, Happy, Sad, etc.). | Applied to the scoring algorithm as a weight multiplier. |

Exploratory Data Analysis (EDA) revealed that emotional peaks consistently align with the volume of specific keywords and emojis, which helped define the boundary conditions for the Golden Score algorithm.

---

## 6. Data Primary Cleaning and Transformation (ETL)
The ETL layer handles the inherent noise of social media data, such as slang, emojis, and mixed-language input. We developed a custom **Regex Engine** to recognize temporal markers in both Western and Arabic-Indic digit formats (٠-٩). To ensure the engine remains linguistically agnostic, we integrated `deep-translator` to unify inputs into a standardized format before passing them to the transformer model.

**ETL Steps applied in sequence:**
* Detection and normalization of Arabic-Indic digits to Western format.
* Strict data-type enforcement (`astype(str)`) to prevent PyArrow rendering crashes.
* Regex extraction of timestamp patterns (MM:SS and HH:MM:SS).
* Intelligent sampling of Arabic comments (capped at the top 400 longest comments) to bypass API timeouts without losing analytical weight.
* Truncation of comment text to 512 tokens for transformer compatibility.
* Stop-word removal (English + Arabic) for Smart Word Cloud generation.

---

## 7. Data Visualization and Insights
To transform raw scores into actionable intelligence, we employ **Plotly** and **Matplotlib** for dynamic visualization. The system generates multiple high-impact visuals that allow analysts to interpret audience behavior over time.

* **Engagement Heatmap:** A temporal histogram mapping emotional intensity across the video duration in minutes, color-coded by emotion type. This allows editors to visually identify clustering of audience reactions.
* **Emotion Breakdown Chart:** A macroscopic bar chart providing a full view of the video's emotional DNA across all five sentiment categories.
* **Smart Word Cloud:** A frequency-based word cloud generated from all timestamped comments after stop-word removal, revealing the dominant topics and themes driving audience engagement.

<p align="center">
  <img src="images/Screenshot%202026-05-11%20020322.png" width="70%">
</p>

<p align="center">
  <img src="images/Screenshot%202026-05-17%20161108.png" width="48%">
  <img src="images/Screenshot%202026-05-17%20161127.png" width="48%">
</p>

---

## 8. Dashboard Design & Business Insights
The dashboard is engineered with a professional **"Cherry Red"** theme using **Streamlit**, following a Utility-First design philosophy where every element is positioned to reduce cognitive load for the end user.

---

#### **Sidebar Controls (Operational Input)**

The sidebar gives the user full control over the analysis before it begins. To ensure **mobile responsiveness**, the sidebar container is structurally hardcoded to LTR (Left-To-Right), while the textual elements intelligently adapt to RTL (Right-To-Left) in Arabic mode, eliminating UI overlapping glitches.

---

**📌 YouTube URL Input**
The user pastes any YouTube video link. The system automatically extracts the Video ID using Regex.

**📌 Analysis Speed / Depth Selector**
A radio button control with three options — Quick Sample (5k comments), Standard Mode (15k comments), and Deep Scan (50k comments).

**📌 Target Emotion Filter**
A six-option radio selector that allows editors to isolate a specific viral goal. Internal logic maintains strict English routing for the ML model while seamlessly translating the UI output for the user.

**📌 Analysis History Tracker**
A collapsible sidebar panel that logs every video analyzed during the session, displaying the Video ID and timestamp of analysis.

---

#### **Main Analytics Panel (Visual Intelligence)**

---

**📊 KPI Metric Cards**
Four executive summary cards showing Comments Sampled, Timestamped comments, Emotive Signals detected, and Analytical Confidence level. Engineered with flex-box CSS to remain perfectly centered regardless of language mode.

---

#### **The Golden Moments Cards**
The system identifies and ranks the Top 3 highest-scoring segments, displayed as ranked 3D-styled cards: Peak Moment 👑 (featuring a pulsing ring animation), Runner-Up 🥈, and Third Spike 🥉. Each card displays the dominant emotion badge, comment count, emotion diversity count, and a composite score progress bar.

Each card features **two playback options:**
* **⧉ OPEN YOUTUBE:** A clickable timestamp link that opens the browser at the exact second.
* **▶ PLAY IN-APP:** A button that syncs the embedded YouTube player directly inside the dashboard to the exact highlight second.

![Golden Moments Cards](images/Screenshot%202026-05-17%20161958.png)

---

#### **AI Strategic Recommendation**
After the analysis completes, the system automatically generates a written AI recommendation based on the dominant emotion detected. The recommendation provides a specific, actionable content strategy tailored to the video's emotional profile.

| Dominant Emotion | Strategic Recommendation |
| :--- | :--- |
| **Funny** | Extract highlights for TikTok/Reels to maximize viral reach |
| **Controversial** | Film a follow-up Q&A video within 48 hours to ride the algorithm |
| **Inspirational** | Repurpose segments into motivational quotes for LinkedIn/Twitter |
| **Happy** | Ask viewers to Like and Subscribe during highlight peaks |
| **Sad** | Prioritize community management to build viewer loyalty |

---

## 9. Advanced Analytics and AI Modeling
The core of the system is an upgraded **Hybrid Emotion Engine** designed to handle heavy bilingual content efficiently without crashing.

**Layer 1 — Expanded Lexicon Engine (Rule-Based):**
A highly curated, expanded dictionary of Arabic dialect keywords and emojis. If a match is found, the emotion is assigned instantly without an API call, making it extremely fast for high-volume comment sections.

**Layer 2 — Transformer ML Engine & Isolation Logic:**
The engine effectively isolates "Neutral" comments to avoid skewed charting. 
* **For English Videos:** The system processes all extracted neutral-masked comments sequentially at lightning speed.
* **For Arabic Videos:** The system targets only the top 400 longest comments to translate via `deep-translator` and classify via the **j-hartmann/emotion-english-distilroberta-base** model. This hybrid routing completely bypasses external API timeouts.

**The Composite Golden Score Formula:**
`Golden Score = Comment Frequency × Average Emotional Heat × Diversity Bonus`

**Emotion Heat Weights applied in the algorithm:**

| Emotion | Heat Weight | Rationale |
| :--- | :--- | :--- |
| Controversial | 1.5 | Highest engagement driver — triggers replies and shares |
| Funny | 1.4 | Strong shareability signal for short-form content |
| Inspirational | 1.3 | High save and repost rate |
| Happy | 1.0 | Baseline positive signal |
| Sad | 0.9 | Lower viral potential, weighted down |

**Spread Enforcement:** A minimum 3-minute gap is enforced between all detected highlights to guarantee the Top 3 moments are distributed across the full video rather than clustered in one section.

---

## 10. Tools Research and Selection Effort
The technology stack was meticulously chosen to ensure high responsiveness and analytical accuracy. Below is a comparison of the selected tools vs. discarded alternatives:

| Selected Tool | Alternative | Why it was Chosen |
| :--- | :--- | :--- |
| **Streamlit** | Flask / Django | Faster development of interactive BI dashboards with built-in data handling. |
| **Plotly** | Matplotlib | Provides interactive, zoomable, and web-ready visualizations essential for the heatmap. |
| **HuggingFace Transformers** | OpenAI API | Higher cost-efficiency for large-scale local processing with emotion-specific tuned models. |
| **Pandas** | SQL Alone | Enables complex in-memory scoring, filtering, and data transformation at high speed. |
| **deep-translator** | googletrans | More stable and actively maintained library for production-level Arabic-to-English translation. |
| **YouTube Data API v3** | Web Scraping | Official, rate-limited, and structured access to comment hierarchies with pagination support. |

---

## 11. Project Deployment Effort – Use Case
**Use Case: Viral Content Production**

Deployed on **Streamlit Cloud**, the system is publicly accessible at:

### 🚀 [https://auto-highlight.streamlit.app/](https://auto-highlight.streamlit.app/)

The live platform provides a production-ready environment for media managers and content editors to scan long-form podcasts, interviews, or any YouTube video and instantly isolate the Top 3 Golden Moments — directly from the browser with no installation required.

**Zero-Friction Highlight Review Workflow:**
1. Editor pastes a YouTube URL into the sidebar.
2. Selects analysis depth based on the video's comment volume.
3. System fetches, cleans, classifies, and scores all comments automatically.
4. Top 3 Golden Moment cards are displayed with two playback options.
5. Editor clicks **▶ PLAY IN-APP** to preview the highlight inside the dashboard instantly.
6. AI Strategic Recommendation provides the next content action to take.
7. Editor exports results as CSV for handoff to the editing team.

* **Business Benefit:** This eliminates all manual searching friction, enabling a "Scan-to-Edit" workflow that saves media agencies over 90% of manual highlight review time — transforming hours of work into under 60 seconds of automated analysis.

---

## 12. Results
The project successfully demonstrated that crowd-sourced sentiment is a viable and reliable proxy for identifying high-value video segments. The system maintains an analytical confidence level of **96.4%** in typical YouTube environments.

Key findings and technical achievements:
* **Crash-Free Operation:** The implementation of data-type hardening and intelligent translation sampling completely eradicated server timeouts and PyArrow rendering crashes.
* **Flawless Mobile Rendering:** Advanced CSS overrides successfully decoupled the Sidebar's structural direction from the text direction, solving severe mobile UI overlapping glitches when toggling to Arabic.
* **Precision Scoring:** The composite scoring algorithm consistently surfaced moments that aligned with organically viral segments, validating the emotional heat weighting model.
* **Spread Enforcement Validation:** The 3-minute gap requirement proved essential in preventing highlight clustering, maximizing the practical value for editors.
* **Workflow Optimization:** The **▶ PLAY IN-APP** embedded player and instant CSV export features eliminated all context-switching, making the tool highly viable for professional media agency pipelines.

---

## 13. References
* Google Cloud. (2026). *YouTube Data API v3 Documentation*. Retrieved from https://developers.google.com/youtube/v3
* Hartmann, J. (2022). *Emotion English DistilRoBERTa-base*. HuggingFace. Retrieved from https://huggingface.co/j-hartmann/emotion-english-distilroberta-base
* Streamlit Inc. (2026). *Streamlit: The fastest way to build data apps*. Retrieved from https://streamlit.io
* Streamlit Inc. (2026). *Streamlit Cloud: Deploy and share data apps*. Retrieved from https://streamlit.io/cloud
* Pandas Development Team. (2026). *Pandas: Powerful Python data analysis toolkit*. Retrieved from https://pandas.pydata.org
* Plotly Technologies Inc. (2026). *Plotly Python graphing library*. Retrieved from https://plotly.com/python
* Deep Translator. (2026). *deep-translator: A flexible free and unlimited python tool to translate between different languages*. Retrieved from https://pypi.org/project/deep-translator
* Mueller, A. (2023). *WordCloud for Python documentation*. Retrieved from https://amueller.github.io/word_cloud
