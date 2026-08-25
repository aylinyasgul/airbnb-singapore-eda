# Airbnb Singapore — Exploratory Data Analysis

A comprehensive EDA of Airbnb listings in Singapore, including data cleaning, visualisation, statistical analysis, and sentiment analysis on guest reviews.

**Course:** Python for Data Analysis I — IE Master in Business Analytics & Data Science (group assignment)
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

## Key Findings

**Pricing is driven by room type and location — not by size or ratings.**

- **Room type is the strongest price differentiator.** Entire homes/apartments command the
  highest median prices, followed by hotel rooms, then private rooms, then shared rooms. This
  hierarchy holds in every region.
- **Location shifts the tier up or down.** The Central Region is the most expensive across
  every room type; the North, East and North-East are consistently more affordable. Analysed at
  the individual-neighbourhood level the signal is noisy (uneven sample sizes); aggregating to
  neighbourhood groups gives a far more interpretable picture.
- **Size barely matters.** Bedrooms correlate with price at only 0.18 and bathrooms at −0.08.
  Capacity (`accommodates`) has a moderate positive relationship, but with wide overlap.
- **Review scores do not predict price (r = −0.03).** Ratings are heavily inflated — most
  listings cluster between 4.5 and 5.0 — so they carry almost no pricing information.
- **Superhost status, not host tenure, predicts performance.** Superhosts charge more, score
  higher, and accumulate over three times as many reviews. Host tenure correlates *negatively*
  with price (−0.14).
- **Demand is unevenly distributed.** Central-region entire homes show the lowest availability
  (strongest demand); private rooms in the North and East sit unbooked far more often.

**Sentiment analysis** — 29,831 English-language reviews spanning May 2011 to September 2025
(~21% non-English reviews were removed, since TextBlob's polarity model is English-only).
Sentiment has been consistently positive throughout, volatile in the sparse early years
(2011–2013) and stable from 2014 onward, with a slight rise into 2020–2021 and a small
softening after. No major downturns.

---

## Business Recommendations

1. **Price on room type and region first.** Those two variables explain most of the observed
   variation; square-footage proxies like bedroom count add little.
2. **Do not use review scores as a pricing signal.** Rating inflation makes them nearly
   uninformative — a 4.9 is the market norm, not a differentiator.
3. **For hosts: pursue Superhost status rather than simply staying on the platform longer.**
   Tenure alone shows no pricing benefit; Superhost status tracks with higher prices, better
   ratings and materially more booking activity.
4. **Target availability, not price, in low-demand regions.** High year-round availability in
   the North and East points to a demand problem that discounting alone is unlikely to fix.

---

## Limitations

- Single snapshot (scraped 2025-09-28) — no seasonality or trend in the listings data.
- Inside Airbnb data is scraped, not official; `price` reflects the advertised nightly rate,
  not realised booking revenue.
- 8.2% of listings were removed as price outliers by the IQR method, so the luxury segment is
  under-represented by design.
- TextBlob's lexicon-based polarity is a coarse sentiment measure and does not handle sarcasm
  or domain-specific phrasing.
- Non-English reviews (~21%) were excluded, so sentiment reflects English-speaking guests only.

---

## Project structure

```
.
├── airbnb_singapore_eda.ipynb
├── README.md
├── .gitignore
└── data/               ← not tracked; download separately
```
