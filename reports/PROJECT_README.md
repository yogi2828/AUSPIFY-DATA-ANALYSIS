# Data Analysis Using Python — Netflix Business Intelligence Portfolio

**Internship Program:** Data Analysis Using Python (4-Week Practical Learning Program)  
**Organization:** Auspify Technologies  
**Project Title:** Global Netflix Catalog Analytics, Demographic Segmentation & Strategic Business Intelligence  
**Author:** Data Analysis Intern  
**Date:** October 2026  

---

## 1. Project Overview & Directory Architecture

This project delivers an end-to-end data analysis and business intelligence portfolio based on Netflix's global streaming catalog. The analysis follows the official internship task specification (`DATA ANALYSIS USING PYTHON TASK LIST.pdf`) and produces **six modular, cumulative, and independently executable Jupyter notebooks**, accompanied by cleaned datasets, statistical summaries, publication-grade static figures, and interactive web dashboards.

### Directory Organization:
```
d:/AUSPIFY DATA ANALYSIS/
│
├── Dataset.csv                                    # Original immutable source dataset (8,790 records)
├── DATA ANALYSIS USING PYTHON TASK LIST.pdf       # Official internship task specifications
├── requirements.txt                              # Pinned Python package dependencies
├── README.md                                      # Quickstart documentation (root link)
│
├── notebooks/                                     # Six cumulative Jupyter notebooks
│   ├── Task_1_Netflix_Data_Cleaning.ipynb         # Task 1: Data Cleaning & Preparation
│   ├── Task_2_Content_Type_Analysis.ipynb         # Task 2: Content Type Analysis Dashboard
│   ├── Task_3_Country_Wise_Analysis.ipynb         # Task 3: Country-Wise Content Analysis
│   ├── Task_4_Release_Year_Trend_Analysis.ipynb   # Task 4: Trend Analysis by Release Year
│   ├── Task_5_Rating_and_Genre_Analysis.ipynb     # Task 5: Content Rating & Genre Analysis
│   └── Task_6_Netflix_Business_Insights_Report.ipynb # Task 6: Business Intelligence Capstone
│
├── data/
│   └── cleaned/
│       └── netflix_cleaned.csv                    # Validated cleaned catalog (8,787 records, 16 features)
│
├── outputs/                                       # Generated figures, tables, and dashboards
│   ├── task_1/                                    # Missing values audit chart & comparison CSV
│   ├── task_2/                                    # Bar, donut & duration distribution charts + CSVs
│   ├── task_3/                                    # Country rankings, format split charts + CSVs
│   ├── task_4/                                    # Historical trends, lag & decade charts + CSVs
│   ├── task_5/                                    # Static charts, CSVs + 2 Interactive Plotly HTMLs
│   └── task_6/                                    # Executive BI dashboard, cross-matrix + KPI CSV
│
└── reports/                                       # Executive reports and audit documentation
    ├── FINAL_PROJECT_REPORT.md                    # Comprehensive master internship report
    ├── DATA_CLEANING_LOG.md                       # Detailed data cleaning & transformation log
    └── PROJECT_README.md                          # Full project guide and execution instructions
```

---

## 2. Environment Setup & Dependency Installation

The project runs on Python 3.10+ (tested and validated on Python 3.14). All required packages are listed in `requirements.txt`.

### Step 1: Install Dependencies
```bash
pip install -r requirements.txt
```

### Required Packages:
- `pandas>=2.0.0`: Data manipulation, aggregation, and time series transformations
- `numpy>=1.26.0`: Numerical array operations and statistical indexing
- `matplotlib>=3.8.0`: Publication-grade static charting and multi-panel figures
- `seaborn>=0.13.0`: Statistical distributions, heatmaps, and styling themes
- `plotly>=6.0.0`: Interactive HTML dashboards and hierarchical treemaps
- `nbformat>=5.9.0`: Jupyter notebook structure generation and reading
- `nbconvert>=7.16.0`: Programmatic headless notebook execution and validation
- `ipykernel>=6.29.0`: Jupyter kernel execution backend

---

## 3. Cumulative Dependency Architecture & Execution Rules

### The Cumulative Rule (Strict Independence)
A central requirement of this project is that **no notebook relies on the memory state of another notebook's kernel**.

Whenever a downstream task requires data or features prepared in an earlier task:
1. Each notebook includes a robust **dynamic path resolver** (`get_project_root()`), ensuring that paths resolve properly whether Jupyter is launched from the project root or from inside `notebooks/`.
2. Each notebook attempts to load the pre-validated cleaned dataset (`data/cleaned/netflix_cleaned.csv`).
3. If the cleaned file is not found, the notebook **automatically executes the complete Task 1 cleaning pipeline internally as a self-contained fallback**.
4. Every notebook can be executed standalone from a **fresh Jupyter kernel** without manual prerequisites.

---

## 4. Notebook Descriptions & Deliverables

### Task 1: Netflix Data Cleaning & Preparation (`Task_1_Netflix_Data_Cleaning.ipynb`)
- **Objective:** Ingest, audit, clean, and standardize the raw Netflix catalog.
- **Key Actions:** Audits hidden string placeholders (`"Not Given"` in director and country); proves why titles should not be dropped; identifies and removes 3 metadata-identical duplicate title pairs (`15-Aug`, `22-Jul`, `9-Feb`); standardizes dates, ratings, and durations; exports cleaned dataset.
- **Key Deliverables:** `data/cleaned/netflix_cleaned.csv`, `outputs/task_1/data_cleaning_comparison_summary.csv`, `outputs/task_1/data_cleaning_missing_values_audit.png`.

### Task 2: Content Type Analysis Dashboard (`Task_2_Content_Type_Analysis.ipynb`)
- **Objective:** Analyze the distribution between Movies and TV Shows.
- **Key Actions:** Calculates exact volumes (6,124 Movies [69.69%] vs. 2,663 TV Shows [30.31%]); computes format ratios (2.30 : 1); plots high-contrast bar and donut charts; profiles Movie runtimes (median: 98 min) vs. TV Show season counts (67.2% have only 1 season).
- **Key Deliverables:** `outputs/task_2/content_type_bar_chart.png`, `outputs/task_2/content_type_donut_chart.png`, `outputs/task_2/content_duration_distribution.png`, `outputs/task_2/content_type_distribution_summary.csv`.

### Task 3: Country-Wise Netflix Content Analysis (`Task_3_Country_Wise_Analysis.ipynb`)
- **Objective:** Evaluate geographic distribution and national format specialization.
- **Key Actions:** Analyzes 8,500 known titles across 44 countries; tracks 287 unassigned titles; proves Pareto concentration (Top 3 hold 58.05%, Top 10 hold 79.07%); uncovers format specialization (India is 92.3% Movies, South Korea is 77.1% TV Shows, Pakistan is 83.1% TV Shows, US is 73.9% Movies).
- **Key Deliverables:** `outputs/task_3/top_15_countries_overall.png`, `outputs/task_3/top_10_countries_movies_vs_tv.png`, `outputs/task_3/country_content_ratio_analysis.png`, `outputs/task_3/country_wise_content_rankings.csv`.

### Task 4: Trend Analysis by Release Year (`Task_4_Release_Year_Trend_Analysis.ipynb`)
- **Objective:** Analyze historical catalog evolution from 1925 to 2021.
- **Key Actions:** Distinguishes original `release_year` (1925–2021) from platform ingestion `year_added` (2008–2021); identifies the all-time production peak in 2018 (1,144 titles); documents the 2021 milestone where TV Shows surpassed Movies for the first time (315 TV Shows [53.2%] vs. 277 Movies [46.8%]); measures catalog lag (55.0% added within 1 year).
- **Key Deliverables:** `outputs/task_4/yearly_content_releases_trend.png`, `outputs/task_4/movies_vs_tv_yearly_trend.png`, `outputs/task_4/release_year_vs_added_year.png`, `outputs/task_4/decade_wise_distribution.png`, `outputs/task_4/yearly_trends_summary.csv`.

### Task 5: Content Rating & Genre Analysis (`Task_5_Rating_and_Genre_Analysis.ipynb`)
- **Objective:** Examine regulatory certifications and genre clusters for audience positioning.
- **Key Actions:** Maps 14 ratings into 5 standardized audience maturity categories (75.69% Adult/Teen); explodes multi-value `listed_in` attributes across 42 distinct genres (Top: International Movies [2,752], Dramas [2,424], Comedies [1,673]); produces static figures and two interactive Plotly web dashboards.
- **Key Deliverables:** `outputs/task_5/rating_distribution_by_type.png`, `outputs/task_5/top_15_genres_overall.png`, `outputs/task_5/audience_maturity_breakdown.png`, `outputs/task_5/interactive_ratings_dashboard.html`, `outputs/task_5/interactive_genres_dashboard.html`.

### Task 6: Netflix Business Insights Report (`Task_6_Netflix_Business_Insights_Report.ipynb`)
- **Objective:** Synthesize all previous analyses into an executive business intelligence capstone.
- **Key Actions:** Integrates Tasks 1–5; develops a 4-panel executive dashboard; performs cross-market maturity and genre matrix analyses; delivers 4 data-grounded strategic recommendations; defines analytical boundaries.
- **Key Deliverables:** `outputs/task_6/netflix_executive_bi_dashboard.png`, `outputs/task_6/cross_market_genre_matrix.png`, `outputs/task_6/executive_kpi_summary.csv`, `outputs/task_6/cross_market_maturity_matrix.csv`.

---

## 5. Programmatic Execution & Verification Command

To execute and re-validate all six notebooks programmatically from the terminal:
```bash
# Execute each notebook in place
python -m jupyter nbconvert --to notebook --execute "notebooks/Task_1_Netflix_Data_Cleaning.ipynb" --inplace
python -m jupyter nbconvert --to notebook --execute "notebooks/Task_2_Content_Type_Analysis.ipynb" --inplace
python -m jupyter nbconvert --to notebook --execute "notebooks/Task_3_Country_Wise_Analysis.ipynb" --inplace
python -m jupyter nbconvert --to notebook --execute "notebooks/Task_4_Release_Year_Trend_Analysis.ipynb" --inplace
python -m jupyter nbconvert --to notebook --execute "notebooks/Task_5_Rating_and_Genre_Analysis.ipynb" --inplace
python -m jupyter nbconvert --to notebook --execute "notebooks/Task_6_Netflix_Business_Insights_Report.ipynb" --inplace
```

All six notebooks have been verified and confirmed to execute with **Exit Code 0** with zero errors.

---

## 6. Strategic Takeaways for Business Stakeholders

1. **Invest in Indian Original Series:** Shift acquisition capital in India away from second-window Bollywood theatricals (92.3% film share) toward multi-season serialized web series to lower monthly churn.
2. **Expand Asian Serialized Franchises:** Capitalize on the world-class export efficiency of South Korea (77.1% TV) and Japan (66.4% TV) by locking in multi-year global distribution rights for K-Dramas and Anime.
3. **Curb the 1-Season Cancellation Cliff:** Establish a renewal bridge for promising series to counter the fact that 67.2% of shows end after Season 1.
4. **Anchor Family Subscribers:** Protect the 23.4% family/children's catalog segment to maintain lower household churn rates during macroeconomic downturns.
