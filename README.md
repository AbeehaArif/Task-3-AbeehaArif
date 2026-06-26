# Task 3: AI Recommendation Logic
## Project Description
This project focuses on the implementation of a **Content-Based Filtering** recommendation engine utilizing **TF-IDF Weighting** and **Cosine Similarity** as its core mathematical logic. Using a custom-built Tech Stack dataset (`raw_skills.csv`), the system maps a user's raw skill inputs to a structured vector space and ranks job roles based on angular alignment, transforming qualitative career preferences into objective, ranked mathematical output.

The pipeline follows a strict **4-Step Assembly Line** (Ingestion -> Scoring -> Sorting -> Filtering) and includes a **Cold Start Detection** fallback to handle zero-profile edge cases.

## Key Technical Pillars
- **Vector Mapping (Bridging the Language Barrier):** Transformed raw text-based skill tags and job role attributes into numerical arrays using `TfidfVectorizer`, operating within a shared vocabulary space to ensure dimensional consistency between the user profile and item dataset.
- **TF-IDF Weighting (Upgrading Feature Extraction):** Applied Term Frequency-Inverse Document Frequency weighting to penalize generic, high-frequency skills and reward specific, descriptive ones - ensuring unique skills exert greater influence on the similarity math.
- **Cosine Similarity (The Industry Standard):** Measured the angular alignment between the user profile vector and each job role vector, rendering the scoring invariant to vector magnitude and focusing strictly on the orientation of preferences. Score of `1.0` indicates perfect alignment; `0.0` indicates no shared characteristics.
- **4-Step Ranking Pipeline:** Structured the recommendation flow as: **(1) Ingestion** - capturing minimum 3 user skill inputs to ensure sufficient data density; **(2) Scoring** - computing cosine similarity of the user vector against all 15 job role vectors; **(3) Sorting** - organizing results in descending order by similarity score; **(4) Filtering** - truncating output to the Top 3 highest-scoring matches to prevent choice overload.
- **Cold Start Handling:** Implemented a zero-vector detection check that activates a Trending Fallback, surfacing globally popular roles when no skill overlap is detected.

## Tools & Technologies
- **Language:** Python 3.x
- **Libraries:** NumPy, Pandas, Scikit-Learn
- **Dataset:** Custom-built `raw_skills.csv` (15 job roles, generated programmatically)
- **Environment:** Visual Studio Code (Jupyter Notebook environment)

## Evaluation Insights
The recommender outputs a ranked list of career paths with the following diagnostics per recommendation:
- **Match Score (%):** Cosine similarity expressed as a percentage alignment between user skills and job role requirements.
- **Required Skills Preview:** Top 5 skills associated with the recommended role.
- **Skill Gap Analysis:** Displays skills the user already possesses (`You have`) and priority skills to acquire next (`Learn next`).

## Sample Output
**Your Skills:** python, machine_learning, deep_learning
- **Rank 1:** AI Research Scientist      **Match Score:** 74.3%
- **Rank 2:** Machine Learning Engineer  **Match Score:** 68.1%
- **Rank 3:** NLP Engineer               **Match Score:** 51.7%

## How to Run
1. Open this project folder in Visual Studio Code.
2. Ensure you have the **Jupyter Extension** installed.
3. Open the `AI_Recommendation_logic.ipynb` notebook file.
4. Click **Run All** - the script will auto-generate `raw_skills.csv`, accept your skill inputs, and display the Top 3 recommended career paths.
