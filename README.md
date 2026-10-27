# Netflix Global Content Analytics & Business Intelligence

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.0+-green.svg)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-3.8+-yellow.svg)](https://matplotlib.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-0.13+-brightgreen.svg)](https://seaborn.pydata.org/)
[![Plotly](https://img.shields.io/badge/Plotly-6.0+-purple.svg)](https://plotly.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Internship Program:** Data Analysis Using Python (4-Week Practical Learning Program)  
**Organization:** Auspify Technologies  
**Repository:** [https://github.com/yogi2828/AUSPIFY-DATA-ANALYSIS](https://github.com/yogi2828/AUSPIFY-DATA-ANALYSIS)  
**Author:** Data Analysis Intern  
**Date of Completion:** October 2026  

---

## 1. Project Overview & Internship Objectives
This project presents an end-to-end data analysis and business intelligence portfolio examining Netflix's global streaming catalog. Following the curriculum specified in [`DATA ANALYSIS USING PYTHON TASK LIST.pdf`](DATA%20ANALYSIS%20USING%20PYTHON%20TASK%20LIST.pdf), the project investigates:
1. **Catalog Integrity & Preparation:** Ingestion, string placeholder auditing, and deduplication.
2. **Content Format Dynamics:** Proportional distribution between feature films and television series, including runtime and season profiles.
3. **Geographical Footprint & Specialization:** Country-level production volumes, Pareto library concentration, and national format specialization.
4. **Historical Trajectories:** Catalog evolution across release years (1925–2021), platform ingestion lags, and the historic 2021 serialized crossover.
5. **Regulatory Maturity & Genre Clusters:** Mapping 14 ratings into 5 standardized audience maturity segments, exploding multi-value genre classifications, and deploying interactive Plotly dashboards.
6. **Executive Business Intelligence:** Multi-dimensional cross-market synthesis, a 4-panel executive dashboard, and actionable strategic recommendations.

---

## 2. Dataset Architecture

- **Source Dataset:** [`Dataset.csv`](Dataset.csv) — 8,790 raw rows, 10 columns.
- **Cleaned Dataset:** [`data/cleaned/netflix_cleaned.csv`](data/cleaned/netflix_cleaned.csv) — 8,787 verified unique titles, 16 standardized features.

### Feature Dictionary:
| Feature Name | Cleaned Data Type | Description |
| :--- | :--- | :--- |
| `show_id` | `str` | Unique system identifier (e.g., `s1`, `s2`) |
| `type` | `str` | Content classification: `'Movie'` or `'TV Show'` |
| `title` | `str` | Cleaned title of the film or television series |
| `director` | `str` | Director name(s) (missing values standardized as `'Not Given'`) |
| `country` | `str` | Primary producing country (missing values standardized as `'Not Given'`) |
| `date_added` | `datetime64[ns]` | Standardized timestamp of ingestion to Netflix (2008–2021) |
| `year_added` | `Int64` | Calendar year when title was added to Netflix |
| `month_added` | `Int64` | Calendar month when title was added to Netflix |
| `month_name_added`| `str` | Full month name of ingestion (e.g., `'September'`) |
| `release_year` | `int64` | Original theatrical or broadcast release year (1925–2021) |
| `rating` | `str` | Official rating certification (e.g., `TV-MA`, `TV-14`, `R`, `PG-13`) |
| `target_audience` | `str` | Regulatory audience segment (Mature 18+, Teens 14+, Older Kids PG, Kids 7+, Little Kids, Unrated) |
| `duration` | `str` | Raw duration string (e.g., `'90 min'`, `'1 Season'`) |
| `duration_int` | `int64` | Parsed numerical magnitude of runtime or seasons |
| `duration_unit` | `str` | Parsed duration unit (`'min'`, `'Season'`, `'Seasons'`) |
| `listed_in` | `str` | Comma-separated genre classifications |

---

## 3. Repository Organization

```
AUSPIFY-DATA-ANALYSIS/
│
├── Dataset.csv                                    # Original immutable source dataset (8,790 records)
├── DATA ANALYSIS USING PYTHON TASK LIST.pdf       # Official internship task specification
├── requirements.txt                              # Pinned Python package dependencies
├── README.md                                      # Project overview & documentation
├── .gitignore                                     # Git exclusion rules for clean version control
│
├── notebooks/                                     # Six cumulative, executable Jupyter notebooks
│   ├── Task_1_Netflix_Data_Cleaning.ipynb         # Task 1: Complete cleaning & preparation workflow
│   ├── Task_2_Content_Type_Analysis.ipynb         # Task 2: Content type shares, ratios & runtimes
│   ├── Task_3_Country_Wise_Analysis.ipynb         # Task 3: Global production hubs & format specialization
│   ├── Task_4_Release_Year_Trend_Analysis.ipynb   # Task 4: Historical evolution & the 2021 format pivot
│   ├── Task_5_Rating_and_Genre_Analysis.ipynb     # Task 5: Ratings, genres & interactive Plotly dashboards
│   └── Task_6_Netflix_Business_Insights_Report.ipynb # Task 6: Executive BI synthesis & strategic matrix
│
├── data/
│   └── cleaned/
│       └── netflix_cleaned.csv                    # Cleaned catalog (8,787 rows x 16 standardized features)
│
├── outputs/                                       # Generated artifacts organized by task
│   ├── task_1/                                    # Missing values audit chart & comparison CSV
│   ├── task_2/                                    # Bar chart, donut chart, runtime profiles, summary CSVs
│   ├── task_3/                                    # Top countries chart, stacked format chart, rankings CSV
│   ├── task_4/                                    # Trend charts, catalog lag, decade chart, trend CSVs
│   ├── task_5/                                    # Static charts, genre rankings, 2 interactive HTML dashboards
│   └── task_6/                                    # Multi-panel executive BI dashboard, matrix heatmap, KPI CSV
│
└── reports/                                       # Formal documentation and analytical deliverables
    ├── FINAL_PROJECT_REPORT.md                    # Master comprehensive analytical report
    ├── DATA_CLEANING_LOG.md                       # Complete audit log of all data cleaning transformations
    └── PROJECT_README.md                          # Full architectural guide and setup instructions
```

---

## 4. Key Empirical Findings (Verified from Calculations)

```
========================================================================================
                      NETFLIX GLOBAL CATALOG KEY METRICS
========================================================================================
 Total Cleaned Titles:        8,787 titles (after deduplicating 3 metadata-identical pairs)
 Content Type Split:          6,124 Movies (69.69%)  |  2,663 TV Shows (30.31%)
 Format Ratio:                2.30 Movies per 1 TV Show
 Median Movie Runtime:        98.0 minutes (Mean: 99.6 minutes)
 Single-Season TV Share:      67.2% of all TV shows (1,791 series have only 1 season)
 Top 3 Production Hubs:       United States (3,240), India (1,056), United Kingdom (638)
 Geographic Concentration:    Top 3 hold 58.05% of known titles; Top 10 hold 79.07%
 Format Specialization:       India (92.3% Movies) vs. Pakistan (83.1% TV), South Korea (77.1% TV)
 Peak Production Year:        2018 (1,144 titles released)
 2021 Format Pivot:           TV Shows (315 titles, 53.2%) > Movies (277 titles, 46.8%)
 Core Target Audience:        75.69% of catalog certified for Mature Adults (18+) or Teens (14+)
 Top Atomic Genre:            International Movies (2,752 titles / 31.32% catalog coverage)
========================================================================================
```

---

## 5. Summary of the Six Internship Tasks

### Task 1: Netflix Data Cleaning & Preparation
- **Notebook:** [`notebooks/Task_1_Netflix_Data_Cleaning.ipynb`](notebooks/Task_1_Netflix_Data_Cleaning.ipynb)
- **Methodology:** Discovered that standard null checks missed **2,588 `"Not Given"` directors** (29.44%) and **287 `"Not Given"` countries** (3.26%). Proved why deleting these records would introduce severe survivor bias against television series. Preserved unassigned records, verified the legitimate film title `"Unknown"` (Jaume Collet-Serra, 2011), deduplicated 3 duplicate title pairs (`15-Aug`, `22-Jul`, `9-Feb`), standardized dates, ratings, and durations.
- **Key Artifacts:** [`data/cleaned/netflix_cleaned.csv`](data/cleaned/netflix_cleaned.csv), [`outputs/task_1/data_cleaning_missing_values_audit.png`](outputs/task_1/data_cleaning_missing_values_audit.png), [`outputs/task_1/data_cleaning_comparison_summary.csv`](outputs/task_1/data_cleaning_comparison_summary.csv).

### Task 2: Content Type Analysis Dashboard
- **Notebook:** [`notebooks/Task_2_Content_Type_Analysis.ipynb`](notebooks/Task_2_Content_Type_Analysis.ipynb)
- **Methodology:** Evaluated catalog composition, showing Movies dominate total volume (**6,124 titles, 69.69%**) vs. TV Shows (**2,663 titles, 30.31%**). Profiled movie runtimes (median: 98 minutes) and uncovered that **67.2% of TV shows end after Season 1**.
- **Key Artifacts:** [`outputs/task_2/content_type_bar_chart.png`](outputs/task_2/content_type_bar_chart.png), [`outputs/task_2/content_type_donut_chart.png`](outputs/task_2/content_type_donut_chart.png), [`outputs/task_2/content_duration_distribution.png`](outputs/task_2/content_duration_distribution.png), [`outputs/task_2/content_type_distribution_summary.csv`](outputs/task_2/content_type_distribution_summary.csv).

### Task 3: Country-Wise Netflix Content Analysis
- **Notebook:** [`notebooks/Task_3_Country_Wise_Analysis.ipynb`](notebooks/Task_3_Country_Wise_Analysis.ipynb)
- **Methodology:** Analyzed 8,500 known titles across 44 countries. Demonstrated Pareto concentration where the Top 10 countries account for **79.07%** of known titles. Uncovered distinct national production models: Western and Bollywood markets are film-heavy (India: 92.3% Movies, US: 73.9% Movies), whereas Asian production hubs are episodic-heavy (Pakistan: 83.1% TV, South Korea: 77.1% TV, Japan: 66.4% TV).
- **Key Artifacts:** [`outputs/task_3/top_15_countries_overall.png`](outputs/task_3/top_15_countries_overall.png), [`outputs/task_3/top_10_countries_movies_vs_tv.png`](outputs/task_3/top_10_countries_movies_vs_tv.png), [`outputs/task_3/country_content_ratio_analysis.png`](outputs/task_3/country_content_ratio_analysis.png), [`outputs/task_3/country_wise_content_rankings.csv`](outputs/task_3/country_wise_content_rankings.csv).

### Task 4: Trend Analysis by Release Year
- **Notebook:** [`notebooks/Task_4_Release_Year_Trend_Analysis.ipynb`](notebooks/Task_4_Release_Year_Trend_Analysis.ipynb)
- **Methodology:** Established the distinction between original production year (`release_year`, 1925–2021) and platform ingestion year (`year_added`, 2008–2021). Documented the 2013–2018 streaming boom peaking in **2018 with 1,144 releases**, and revealed that in **2021, TV Shows surpassed Movies for the first time in catalog history (315 TV Shows vs. 277 Movies)**.
- **Key Artifacts:** [`outputs/task_4/yearly_content_releases_trend.png`](outputs/task_4/yearly_content_releases_trend.png), [`outputs/task_4/movies_vs_tv_yearly_trend.png`](outputs/task_4/movies_vs_tv_yearly_trend.png), [`outputs/task_4/release_year_vs_added_year.png`](outputs/task_4/release_year_vs_added_year.png), [`outputs/task_4/decade_wise_distribution.png`](outputs/task_4/decade_wise_distribution.png), [`outputs/task_4/yearly_trends_summary.csv`](outputs/task_4/yearly_trends_summary.csv).

### Task 5: Content Rating & Genre Analysis
- **Notebook:** [`notebooks/Task_5_Rating_and_Genre_Analysis.ipynb`](notebooks/Task_5_Rating_and_Genre_Analysis.ipynb)
- **Methodology:** Standardized 14 ratings into 5 audience maturity categories (**75.69% Mature/Teen**). Exploded multi-value `listed_in` attributes across 42 distinct genres, led by *International Movies* (2,752), *Dramas* (2,424), and *Comedies* (1,673). Built both publication static figures and interactive Plotly HTML dashboards.
- **Key Artifacts:** [`outputs/task_5/rating_distribution_by_type.png`](outputs/task_5/rating_distribution_by_type.png), [`outputs/task_5/top_15_genres_overall.png`](outputs/task_5/top_15_genres_overall.png), [`outputs/task_5/audience_maturity_breakdown.png`](outputs/task_5/audience_maturity_breakdown.png), [`outputs/task_5/interactive_ratings_dashboard.html`](outputs/task_5/interactive_ratings_dashboard.html), [`outputs/task_5/interactive_genres_dashboard.html`](outputs/task_5/interactive_genres_dashboard.html).

### Task 6: Netflix Business Insights Report
- **Notebook:** [`notebooks/Task_6_Netflix_Business_Insights_Report.ipynb`](notebooks/Task_6_Netflix_Business_Insights_Report.ipynb)
- **Methodology:** Synthesized Tasks 1–5 into an executive business intelligence capstone. Developed a consolidated 4-panel executive dashboard, constructed cross-market maturity and genre matrices, and delivered 4 qualified strategic recommendations.
- **Key Artifacts:** [`outputs/task_6/netflix_executive_bi_dashboard.png`](outputs/task_6/netflix_executive_bi_dashboard.png), [`outputs/task_6/cross_market_genre_matrix.png`](outputs/task_6/cross_market_genre_matrix.png), [`outputs/task_6/executive_kpi_summary.csv`](outputs/task_6/executive_kpi_summary.csv), [`outputs/task_6/cross_market_maturity_matrix.csv`](outputs/task_6/cross_market_maturity_matrix.csv).

---

## 6. Strategic Business Recommendations

1. **Shift Capital from Film Licensing to Multi-Season Series in India:**  
   India's catalog is **92.3% Movies and only 7.7% TV Shows**. Transitioning capital toward indigenous multi-season web series will convert casual movie watchers into recurring weekly subscribers, reducing churn in Netflix's fastest-growing market.
2. **Expand Global Distribution Pacts for Asian Serialized IP:**  
   South Korea (**77.1% TV**) and Japan (**66.4% TV**) produce highly engaging serialized IP (*Squid Game*, *Alice in Borderland*, *Demon Slayer*) that achieves massive worldwide crossover appeal at 60–75% lower cost-per-minute than domestic Hollywood productions.
3. **Institute a "Season 2 Continuity Bridge" to Halt the 1-Season Cliff:**  
   With **67.2% of TV series terminating after Season 1**, subscribers face franchise fatigue. Guaranteeing second-season renewals for titles meeting target sub-audience completion criteria will enhance library depth and perceived value.
4. **Anchor Family Subscribers with High-Replay Animated Content:**  
   Children and family programming (**23.38% of catalog**) generates the highest re-watchability and lowest household churn across the streaming industry, providing revenue stability during economic downturns.

---

## 7. Methodological Boundaries & Limitations

1. **Catalog Telemetry Boundary:** Content ratings (`TV-MA`, `TV-14`, `PG`, etc.) represent regulatory suitability certifications assigned by advisory boards. **They do not measure actual user age demographics, viewing hours, or audience popularity.**
2. **Temporal Window:** The dataset captures content available on Netflix through **September 25, 2021**. Additions, renewals, or removals after this date are not represented.
3. **Consolidated Country Tagging:** In this dataset, titles carry a single consolidated country assignment; multi-national co-productions are represented by their primary producing entity.

---

## 8. Installation & Reproducibility Guide

### Step 1: Clone the Repository
```bash
git clone https://github.com/yogi2828/AUSPIFY-DATA-ANALYSIS.git
cd AUSPIFY-DATA-ANALYSIS
```

### Step 2: Install Required Dependencies
```bash
pip install -r requirements.txt
```

### Step 3: Launch Jupyter Notebooks
```bash
jupyter notebook
```
Navigate to the `notebooks/` directory and open any task notebook. Each notebook runs independently in a fresh kernel.

### Step 4: Re-execute All Notebooks Programmatically (Optional)
```bash
python -m jupyter nbconvert --to notebook --execute "notebooks/Task_1_Netflix_Data_Cleaning.ipynb" --inplace
python -m jupyter nbconvert --to notebook --execute "notebooks/Task_2_Content_Type_Analysis.ipynb" --inplace
python -m jupyter nbconvert --to notebook --execute "notebooks/Task_3_Country_Wise_Analysis.ipynb" --inplace
python -m jupyter nbconvert --to notebook --execute "notebooks/Task_4_Release_Year_Trend_Analysis.ipynb" --inplace
python -m jupyter nbconvert --to notebook --execute "notebooks/Task_5_Rating_and_Genre_Analysis.ipynb" --inplace
python -m jupyter nbconvert --to notebook --execute "notebooks/Task_6_Netflix_Business_Insights_Report.ipynb" --inplace
```

---

## 9. Primary Project Reports & Audit Documentation

- **[Master Final Project Report](reports/FINAL_PROJECT_REPORT.md)** — Detailed analytical findings, statistical tables, and strategic recommendations.
- **[Data Cleaning Log](reports/DATA_CLEANING_LOG.md)** — Complete step-by-step audit log of all data cleaning, deduplication, and feature engineering decisions.
- **[Project Setup & Architecture README](reports/PROJECT_README.md)** — Detailed technical architecture and cumulative dependency documentation.
