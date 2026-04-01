# ETL Pipeline - NYC Airbnb Data Analysis

Simple ETL pipeline untuk membersihkan dan menganalisis dataset Airbnb New York City 2019.

## Overview

Project ini dibuat sebagai studi kasus Data Engineer internship. Fokus utama adalah membangun pipeline ETL sederhana yang dapat:
- Membaca raw data dari CSV
- Melakukan data cleaning (handling missing values, formatting, filtering)
- Menyimpan cleaned data untuk analisis lanjutan
- Membuat visualisasi dasar untuk eksplorasi data

## Tech Stack

- Python 3.12
- Pandas, NumPy
- Matplotlib, Seaborn
- Jupyter Notebook

## Project Structure

```
├── notebooks/
│   └── etl_airbnb.ipynb       # Main ETL notebook
├── tugas-etl-airbnb/
│   └── data/
│       ├── raw/               # Raw dataset
│       └── clean/             # Cleaned output
├── requirements.txt
└── README.md
```

## Quick Start

```bash
# Install dependencies
pip install -r requirements.txt

# Run notebook
jupyter notebook notebooks/etl_airbnb.ipynb
```

## ETL Process

### Extract
Baca dataset `AB_NYC_2019.csv` (~49K rows, 16 columns).

### Transform
1. Fill missing `reviews_per_month` dengan 0
2. Drop rows dengan `name` atau `host_name` kosong
3. Convert `last_review` ke datetime
4. Drop kolom `id` dan `host_name`
5. Filter out listings dengan `price = 0`

### Load
Export cleaned data ke `data/clean/airbnb_cleaned.csv`

## Key Findings

**Harga per Wilayah:**
| Borough | Avg Price |
|---------|-----------|
| Manhattan | ~$196 |
| Brooklyn | ~$124 |
| Queens | ~$99 |
| Staten Island | ~$115 |
| Bronx | ~$87 |

**Distribusi Listing:**
- Manhattan & Brooklyn mendominasi (~85% total listings)
- Entire home/apt punya harga tertinggi (~$211/night)
- Private room jadi opsi budget-friendly (~$89/night)

## Dataset

Source: [Kaggle - NYC Airbnb Open Data](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data)

| Metric | Value |
|--------|-------|
| Total Records | 48,895 |
| After Cleaning | ~48,800 |
| Features | 14 columns |
| Period | 2019 |

## Notes

- Dataset sudah cukup bersih, hanya ~2% data yang perlu di-drop
- Missing values mostly ada di kolom review-related
- Beberapa listing punya price=0 (kemungkinan inactive/error)

---

*Dibuat untuk Studi Kasus Magang - Data Engineer*
