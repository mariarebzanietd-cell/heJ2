# BI Pipeline for a Hajj & Umrah Agency (Algeria)

A small Business Intelligence project: from raw data to KPIs for a travel agency.

> **Important:** the pilgrim data is **simulated** (generated with Python), because no public dataset exists for an Algerian agency. Prices, costs and rates are assumptions, not real statistics. Flight numbers and airlines come from a Kaggle dataset (see "Data sources").

## Goal
Show how BI helps a tourism agency make more profit: forecast demand by season (Ramadan, Hajj), choose the best marketing channels, reduce cancellations and follow margins.

## Pipeline
```
generate_dataset.py  ->  etl.py (pandas)  ->  MongoDB Atlas  ->  Power BI dashboard
 (simulated data +        (clean + enrich)      (storage)          (KPIs)
  Kaggle flights)
```

## Data sources
- **Pilgrim reservations:** simulated with Python (numpy, pandas).
- **Flights (columns `airline` and `flight`):** Kaggle dataset "Airlines Flights Data" (author: rohitgrewal). Please check its license on the Kaggle page. The column `flight_source` says `Kaggle` or `Simulated`.
- The departure dates follow the seasons (Ramadan, Hajj, regular). The dates are approximate.

## Files
| File | Role |
|---|---|
| `generate_dataset.py` | Creates the dataset (50,000 reservations) and adds flights from Kaggle. |
| `etl.py` | **Extract** the CSV, **Transform** (duplicates, missing values, text, dates, new columns), **Load** into MongoDB and save a clean CSV. |
| `sample_hajj_umrah_data.csv` | Small sample (1,000 rows). |

## KPIs
Revenue, profit, profit margin %, reservations per month and season, cancellation rate, profit per channel, acquisition cost, average satisfaction, late-documents rate.

## How to run
1. Download the Kaggle flights file and put it in the same folder as the scripts.
2. Run:
```
pip install -r requirements.txt
python generate_dataset.py
python etl.py
```
To load data into MongoDB Atlas, set your connection string in an environment variable (never write it in the code):
```
set MONGO_URI=mongodb+srv://USER:PASSWORD@cluster0.xxxxx.mongodb.net/
```

## Tools
Python (pandas, numpy, pymongo), Kaggle, MongoDB Atlas, Power BI.

## Author
REBZANI - Master Data Management and Business Intelligence
