# Airbnb Singapore — Exploratory Data Analysis

A comprehensive EDA of Airbnb listings in Singapore, including data cleaning, visualisation, statistical analysis, and sentiment analysis on guest reviews.

**Course:** Python for Data Analysis I - IE Master in Business Analytics and Data Science 
**Dataset:** [Inside Airbnb — Singapore](https://insideairbnb.com/get-the-data/)

---

## What this project covers

- **Data quality & cleaning** — type coercion, missing value handling, outlier detection
- **Univariate & bivariate analysis** — price distributions, room types, availability, host behaviour
- **Geospatial analysis** — listing density and pricing by neighbourhood
- **Correlation & statistical tests** — Pearson/Spearman correlations, ANOVA, Tukey HSD
- **Sentiment analysis** — TextBlob polarity scoring and word clouds on guest reviews
- **Business questions** — host performance, pricing strategy, demand patterns

---

## Tech stack

| Category | Libraries |
|----------|-----------|
| Data manipulation | `pandas`, `numpy` |
| Visualisation | `plotly`, `matplotlib`, `seaborn` |
| NLP / Sentiment | `textblob`, `nltk`, `langdetect`, `wordcloud` |
| Statistics | `scipy`, `statsmodels` |
| Runtime | Python 3.10+ |

---

## Getting started

### 1. Clone the repo

```bash
git clone <repo-url>
cd <repo-folder>
```

### 2. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn plotly textblob nltk langdetect wordcloud scipy statsmodels
```

Download the required NLTK data once inside Python:

```python
import nltk
nltk.download('stopwords')
nltk.download('punkt')
```

### 3. Download the data

The data files are **not included** in this repo (too large). Download the following files for **Singapore** from [Inside Airbnb](https://insideairbnb.com/get-the-data/) and place them in a `data/` folder:

```
data/
  listings - singapore.csv.gz
  neighbourhoods - singapore.csv
  reviews - singapore.csv.gz
```

### 4. Run the notebook

```bash
jupyter notebook "airbnb_singapore_eda.ipynb"
```

---

## Project structure

```
.
├── airbnb_singapore_eda.ipynb
├── README.md
├── .gitignore
└── data/               ← not tracked; download separately
```
