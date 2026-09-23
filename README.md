# 🌌 Universal Game Nexus

A content-based recommendation system that bridges **video games** and **board games** into a single similarity space, letting you discover a board game because you liked a video game (or vice versa) — built with Streamlit and TF-IDF/cosine similarity.

## How it works

- **Video game data** (`merged_data.csv`) and **board game data** (`BGG_Data_Set.csv`) are merged into one dataframe with unified `Title`, `Tags`, `Description`, and `Type` columns.
- Tags + descriptions are combined into a single text field per game and vectorized with **TF-IDF**.
- Recommendations are generated via **cosine similarity** (`linear_kernel`) between the selected game and every other title in the combined space, then optionally filtered by type (video game / board game / both).

## Data source

The datasets are too large to commit to this repo, so they're hosted on Hugging Face and downloaded automatically at runtime (and cached locally after the first run):

🤗 [`karthikkkkl/game_recommendation`](https://huggingface.co/datasets/karthikkkkl/game_recommendation)

You don't need to manually download anything — `app.py` pulls both CSVs via `huggingface_hub.hf_hub_download()` the first time the app runs.

> If the dataset repo is private, set an `HF_TOKEN` environment variable (or Streamlit secret) with a Hugging Face access token before running.

## Running locally

```bash
pip install -r requirements.txt
streamlit run app.py
```

## Tech stack

- **Streamlit** — UI
- **pandas** — data wrangling
- **scikit-learn** — TF-IDF vectorization + cosine similarity
- **huggingface_hub** — dataset hosting/retrieval

## Project structure

```
.
├── app.py              # Streamlit app (UI + recommendation logic)
├── requirements.txt    # Python dependencies
└── README.md
```
