# 🎬 Netflix Content Catalog Data Analysis

An exploratory data analysis (EDA) of the Netflix content catalog as of **November 2019**, covering content type, country, genre, rating, release year, and duration.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Numerical-013243?logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557c)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Plots-4c72b0)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Problem Statement](#-problem-statement)
- [Objectives](#-objectives)
- [Dataset](#-dataset)
- [Business Questions](#-business-questions)
- [Tools & Technologies](#-tools--technologies)
- [Project Workflow](#-project-workflow)
- [Getting Started](#-getting-started)
- [Data Cleaning Summary](#-data-cleaning-summary)
- [Feature Engineering](#-feature-engineering)
- [Key Findings](#-key-findings)
- [Visualizations](#-visualizations)
- [Business Insights](#-business-insights)
- [Recommendations](#-recommendations)
- [Challenges Faced](#-challenges-faced)
- [Future Scope](#-future-scope)
- [Project Structure](#-project-structure)
- [References](#-references)
- [Author](#-author)

---

## 📖 Overview

This project analyses **5,195 Netflix titles**, each described by attributes such as title, director, cast, country, date added, release year, rating, duration, genre, and content type (Movie or TV Show).

The goal is to clean, explore, and analyse the dataset to understand:

- How Netflix's content library has grown over time
- Which countries and genres dominate the platform
- How content ratings are distributed
- What patterns exist in movie duration and TV show structure

The findings are useful for content strategy, regional expansion planning, licensing decisions, and content-rating policy.

---

## ❓ Problem Statement

Netflix operates in a highly competitive streaming market and must decide which genres to expand, which countries to prioritise for local production, and how to balance Movies versus TV Shows. Without structured analysis, these decisions rely on guesswork.

This project turns raw catalogue records into structured insights that can guide content acquisition budgets, regional strategy, and audience targeting.

---

## 🎯 Objectives

- Understand the structure, size, and content of the Netflix dataset
- Clean the data by handling missing values, duplicates, and inconsistent data types
- Explore statistical patterns in numerical columns such as release year and duration
- Perform univariate, bivariate, and multivariate EDA
- Create clear, well-labelled visualisations with Matplotlib and Seaborn
- Generate business insights supported directly by the data
- Provide practical, data-driven recommendations for content strategy

---

## 📂 Dataset

| Property | Details |
| --- | --- |
| **File** | `cleaned_netflix_titles_nov_2019.csv` |
| **Source** | Publicly shared Netflix Movies and TV Shows catalogue dataset |
| **Rows** | 5,195 |
| **Columns** | 12 |
| **Format** | CSV |

### Column Description

| Column | Type | Description |
| --- | --- | --- |
| `show_id` | Numerical (ID) | Unique identifier for each title |
| `title` | Text | Name of the movie or TV show |
| `director` | Categorical / Text | Director(s); `Unknown` where unavailable |
| `cast` | Categorical / Text | Main cast; `Unknown` where unavailable |
| `country` | Categorical | Country/countries of production; `Unknown` where unavailable |
| `date_added` | Date/Time | Date the title was added to Netflix |
| `release_year` | Numerical | Year the title was originally released |
| `rating` | Categorical | Content rating, e.g. TV-MA, PG-13, TV-Y |
| `duration` | Text | Minutes for Movies, number of seasons for TV Shows |
| `listed_in` | Categorical | Genre(s) / category tags |
| `description` | Text | Short plot summary |
| `type` | Categorical | `Movie` or `TV Show` |

> **Note:** The `duration` column holds two different kinds of values depending on content type (minutes vs. seasons), so Movies and TV Shows were analysed separately for duration-related questions.

---

## 🔍 Business Questions

- What is the split between Movies and TV Shows?
- Which countries contribute the most content?
- Which genres are most common?
- How has the number of titles added changed year over year?
- What ratings dominate, and what does that suggest about the target audience?
- What is the typical movie duration, and how does it vary?
- Which directors and cast members appear most frequently?
- Has the Movie vs TV Show mix changed over time?

> Questions about viewer ratings, watch-time, or revenue are intentionally excluded because the dataset has no such columns.

---

## 🛠 Tools & Technologies

| Tool | Purpose |
| --- | --- |
| **Python** | Core programming language |
| **Pandas** | Loading, cleaning, transforming, and summarising data |
| **NumPy** | Numerical operations and statistics |
| **Matplotlib** | Base charts (histograms, line plots) |
| **Seaborn** | Statistical visualisations (bar plots, count plots, heatmaps) |
| **Jupyter Notebook** | Interactive analysis environment |

---

## 🔄 Project Workflow

1. **Problem Statement**: define the business problem
2. **Dataset Collection**: obtain the Netflix titles CSV
3. **Import Libraries**: Pandas, NumPy, Matplotlib, Seaborn
4. **Load Dataset**: read the CSV into a DataFrame
5. **Data Exploration**: shape, columns, data types, summary statistics
6. **Data Cleaning**: missing values, duplicates, formatting issues
7. **Exploratory Data Analysis**: patterns and distributions
8. **Univariate Analysis**: individual columns
9. **Bivariate Analysis**: relationships between two variables
10. **Multivariate Analysis**: relationships across several variables
11. **Feature Engineering**: `year_added`, `duration_min`, `num_seasons`
12. **Data Visualisation**: charts communicating findings
13. **Business Insights**
14. **Recommendations**
15. **Conclusion**

---

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- Jupyter Notebook or VS Code

### Installation

```bash
# Clone the repository
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>

# (Optional) create a virtual environment
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate

# Install dependencies
pip install pandas numpy matplotlib seaborn jupyter
```

### Run the Analysis

```bash
jupyter notebook
```

Then open the analysis notebook and run all cells.

### Quick Start

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("cleaned_netflix_titles_nov_2019.csv")

print(df.shape)                    # (5195, 12)
print(df["type"].value_counts())   # Movie: 3938, TV Show: 1257
```

---

## 🧹 Data Cleaning Summary

| Issue | Rows Affected | Action Taken |
| --- | --- | --- |
| Missing `director` | 1,294 | Filled with `Unknown` |
| Missing `cast` | 511 | Filled with `Unknown` |
| Missing `country` | 396 | Filled with `Unknown` |
| Missing `rating` | 9 | Kept as missing / excluded from rating charts |
| Duplicate rows | 0 | Verified, no action needed |
| `date_added` stored as text | All rows | Converted to datetime |
| `duration` mixed units | All rows | Split into `duration_min` (Movies) and `num_seasons` (TV Shows) |

```python
# Fill missing categorical values
for col in ["director", "cast", "country"]:
    df[col] = df[col].fillna("Unknown")

# Convert date_added to datetime
df["date_added"] = pd.to_datetime(df["date_added"], errors="coerce")

# Remove exact duplicate rows
df = df.drop_duplicates()
```

---

## ⚙️ Feature Engineering

| New Column | Source | Purpose |
| --- | --- | --- |
| `year_added` | `date_added` | Year-over-year catalogue growth trends |
| `duration_min` | `duration` (Movies) | Movie length statistics and histograms |
| `num_seasons` | `duration` (TV Shows) | TV show length analysis |

```python
df["year_added"] = df["date_added"].dt.year

movies = df[df["type"] == "Movie"].copy()
movies["duration_min"] = movies["duration"].str.extract(r"(\d+)").astype(int)

tv_shows = df[df["type"] == "TV Show"].copy()
tv_shows["num_seasons"] = tv_shows["duration"].str.extract(r"(\d+)").astype(int)
```

> The exact code in your notebook may differ slightly; adjust as needed.

---

## 📊 Key Findings

### Content Type

| Type | Count | Share |
| --- | --- | --- |
| Movie | 3,938 | 75.8% |
| TV Show | 1,257 | 24.2% |

### Top 10 Countries

| Rank | Country | Titles |
| --- | --- | --- |
| 1 | United States | 2,093 |
| 2 | India | 748 |
| 3 | United Kingdom | 472 |
| 4 | France | 234 |
| 5 | Canada | 232 |
| 6 | Japan | 161 |
| 7 | Spain | 156 |
| 8 | South Korea | 133 |
| 9 | Germany | 127 |
| 10 | China | 113 |

### Top 10 Genres

| Rank | Genre | Titles |
| --- | --- | --- |
| 1 | International Movies | 1,797 |
| 2 | Dramas | 1,488 |
| 3 | Comedies | 992 |
| 4 | International TV Shows | 759 |
| 5 | Documentaries | 658 |
| 6 | Action & Adventure | 532 |
| 7 | Independent Movies | 516 |
| 8 | TV Dramas | 390 |
| 9 | Thrillers | 353 |
| 10 | Children & Family Movies | 340 |

> A title can carry multiple genre tags, so each tag is counted individually.

### Top Ratings

| Rating | Count |
| --- | --- |
| TV-MA | 1,722 |
| TV-14 | 1,406 |
| TV-PG | 602 |
| R | 439 |
| PG-13 | 227 |

### Numerical Summaries

| Metric | Release Year | Movie Duration (min) |
| --- | --- | --- |
| Mean | 2013.43 | 98.04 |
| Median | 2016 | 97 |
| Minimum | 1925 | 3 |
| Maximum | 2020 | 312 |
| Std. Deviation | 8.63 | 27.72 |

### Catalogue Growth

- Titles added grew from **74 in 2015** to **1,843 in 2019**
- In 2019 alone, Netflix added **1,367 movies** vs **476 TV shows**
- Correlation between release year and movie duration is very weak, so runtimes have stayed stable over time

---

## 🖼 Visualizations

| # | Chart | Type |
| --- | --- | --- |
| 1 | Content Type Distribution | Count / bar plot |
| 2 | Top 10 Countries by Titles | Horizontal bar chart |
| 3 | Distribution of Release Years | Histogram with density curve |
| 4 | Distribution of Content Ratings | Count plot |
| 5 | Distribution of Movie Durations | Histogram |
| 6 | Distribution of TV Show Seasons | Count plot |
| 7 | Top 10 Genres | Horizontal bar chart |
| 8 | Titles Added by Year | Line chart |
| 9 | Movies vs TV Shows Added Over Time | Multi-line chart |
| 10 | Release Year vs Movie Duration | Correlation heatmap |

<!-- Add your chart images below, for example:
![Content Type Distribution](images/content_type_distribution.png)
-->

---

## 💡 Business Insights

- **Movies dominate the catalogue:** 75.8% of all titles (3,938 of 5,195)
- **The US leads content sourcing:** 2,093 titles, roughly 40% of all country-tagged content, followed by India and the UK
- **Explosive recent growth:** additions rose from 74 titles in 2015 to 1,843 in 2019, reflecting global expansion
- **Mature-audience skew:** TV-MA and TV-14 together account for over 60% of rated content
- **Consistent movie runtime:** average of 98 minutes with a standard deviation of only about 28 minutes
- **International and drama content leads genres:** International Movies (1,797) and Dramas (1,488)
- **Movies grew faster than TV Shows:** about a 3:1 ratio in 2019

---

## ✅ Recommendations

1. **Continue balanced investment in international content**: India, the UK, and other markets already contribute a large share of the catalogue.
2. **Evaluate the Movie-to-TV-Show ratio**: TV Shows are only 24.2% of the catalogue, and series tend to drive retention.
3. **Expand content for younger and family audiences**: TV-Y, TV-Y7, TV-G, and G ratings make up a comparatively small share.
4. **Improve
