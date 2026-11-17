# ⚽ FIFA 21 Data Analysis Project

An end-to-end data analysis project using **Python** and **Power BI** to explore, clean, transform, and visualize FIFA 21 player data. The project covers data preprocessing, dimensional modeling using a Star Schema, and the development of an interactive Power BI dashboard.

---

## 📌 Table of Contents

1. [Project Overview](#-project-overview)
2. [Dataset](#-dataset)
3. [Python – Data Cleaning & Star Schema](#1-python--data-cleaning--star-schema)
4. [Power BI – Interactive Dashboard](#2-power-bi--interactive-dashboard)
5. [How to Use the Power BI Report](#3-how-to-use-the-power-bi-report)
6. [Project Structure](#-project-structure)
7. [Technologies Used](#-technologies-used)
8. [Key Features](#-key-features)

---

## 📊 Project Overview

This project performs an end-to-end analysis of the FIFA 21 player dataset, combining Python-based data preparation with interactive business intelligence reporting in Power BI.

The main objectives are:

- Explore and understand the FIFA 21 player dataset.
- Clean missing, inconsistent, and incorrectly formatted data.
- Convert columns into appropriate data types.
- Transform the dataset into a relational Star Schema.
- Build an interactive Power BI dashboard to analyze players, performance, and clubs.
- Present meaningful insights through KPIs, charts, slicers, and interactive visualizations.

**Final Deliverables:**
- Cleaned and transformed CSV files.
- A dimensional data model consisting of one fact table and six dimension tables.
- An interactive Power BI report (`.pbix`).

---

## 📁 Dataset

**Source Dataset:** `fifa21 raw data v2.csv`

| Attribute | Description |
|---|---|
| Dataset | FIFA 21 Player Dataset |
| Number of Records | Approximately 18,979 players |
| Number of Columns | 77 |
| Format | CSV |
| Main Entity | Football Players |

The dataset contains information about players, including their age, nationality, club, position, physical attributes, technical abilities, market value, wages, and performance ratings.

---

## 1. Python – Data Cleaning & Star Schema

Python was used for data exploration, preprocessing, cleaning, type conversion, and dimensional modeling.

### 🔍 1.1 Data Exploration

The initial dataset was examined to understand its structure and identify data quality issues.

Key activities included:

- Loading the raw CSV dataset using Pandas.
- Inspecting the dataset's shape and column names.
- Reviewing data types and sample records.
- Identifying missing and null values.
- Detecting mixed data types, particularly in the `Hits` column.
- Identifying formatting inconsistencies, including whitespace and star symbols in rating columns.

### 🧹 1.2 Handling Missing & Invalid Values

Several preprocessing techniques were applied to improve data consistency.

- Filled or standardized missing values.
- Handled missing values in columns such as `Hits` and loan dates.
- Replaced empty or unknown values with consistent placeholders.
- Used appropriate default values such as `Unknown` and `0` where applicable.
- Ensured consistent formatting across categorical columns.

### 🔄 1.3 Data Type Conversion & Cleaning

The dataset was transformed into a more analysis-friendly structure.

Key transformations included:

- Converting height and weight into numeric values.
- Cleaning player market value and wage columns.
- Converting contract dates into usable datetime formats.
- Cleaning star ratings:
  - Weak Foot
  - Skill Moves
  - International Reputation
- Extracting `Joined Year` and `Joined Month` from the `Joined` column.
- Standardizing club names and nationality values.
- Handling inconsistent and invalid data entries.

### 🏗️ 1.4 Dimensional Modeling – Star Schema

After cleaning the dataset, it was divided into a Star Schema consisting of one central fact table and six dimension tables.

#### Database Schema

| Table Name | Description | Key Columns |
|---|---|---|
| `fact_player` | Central fact table containing player metrics and foreign keys | ID, PlayerID, ClubID, NationalityID, Position_ID, Contract_ID, Date_ID, Age, Overall, Potential, Hits, Pace, Shooting, etc. |
| `dim_player` | Player descriptive attributes | PlayerID, PlayerName, Preferred Foot, Work Rates |
| `dim_club` | Club information | ClubID, Club |
| `dim_nationality` | Nationality information | NationalityID, Nationality |
| `dim_position` | Player position information | Position_ID, Best Position, Positions |
| `dim_contract` | Contract and loan information | Contract_ID, Contract, Loan Date End |
| `dim_date` | Player joining date information | Date_ID, Joined, Joined Year, Joined Month |

#### ⭐ Star Schema Structure

The `fact_player` table acts as the central table and connects to the six dimension tables through foreign keys.

This structure improves data organization, simplifies relationships, and supports efficient analytical reporting in Power BI.

### 💾 1.5 Exporting the Cleaned Data

All fact and dimension tables were exported as UTF-8 CSV files into the following directory:

`fifa21_star_schema/`

**Exported Files:**

- `fact_player.csv`
- `dim_player.csv`
- `dim_club.csv`
- `dim_nationality.csv`
- `dim_position.csv`
- `dim_contract.csv`
- `dim_date.csv`

### ▶️ 1.6 How to Reproduce the Python Part

**Install the required dependencies:**

```bash
pip install pandas numpy matplotlib seaborn
```

**Launch Jupyter Notebook:**

```bash
jupyter notebook DataCleaningandSplittingPart.ipynb
```

Run the notebook cells sequentially to reproduce the data cleaning, transformation, and Star Schema creation process.

---

## 2. Power BI – Interactive Dashboard

The cleaned data was imported into Power BI to build an interactive, multi-page analytical dashboard.

The report consists of four pages:

- Home / Navigation Page
- Players Report
- Performance Report
- Club Report

### 🏠 2.1 Home / Navigation Page

The home page serves as the main navigation interface for the dashboard.

**Features:**

- FIFA 21-inspired branding and design.
- Interactive navigation buttons.
- Navigation to:
  - Club Report
  - Player Report
  - Performance Report
- Tooltips and navigation functionality.

### 👤 2.2 Players Report

This page focuses on player demographics, market value, ratings, and individual performance.

**Key Performance Indicators (KPIs):**

- Number of Players
- Average Best Overall
- Average Hits
- Average Power Total

**Filters / Slicers:**

- Nationality
- Joined Year
- Club

**Visualizations:**

| Visualization | Purpose |
|---|---|
| Top 5 Players by Hits | Identifies the most popular players based on hits |
| Positions by Value | Compares market value across player positions |
| Average Rating vs. Potential by Age | Analyzes the relationship between player age, current rating, and potential |
| Detailed Player Table | Displays player information ordered by Average Value |

### 📈 2.3 Performance Report

This page analyzes players' technical, physical, and overall performance attributes.

**Key Performance Indicators (KPIs):**

- Average Attacking
- Average Defending
- Average Dribbling
- Average Movement
- Average Goalkeeping
- Average Mentality

**Filters / Slicers:**

- Nationality
- Joined Year
- Club

**Visualizations:**

| Visualization | Purpose |
|---|---|
| Technical Skill vs. Physical Movement | Explores the relationship between technical abilities and physical movement |
| Overall Performance Per Age | Analyzes player overall ratings across different age groups |
| Player Counts by Best Position and Overall Rating | Compares player distribution by position and rating using a treemap |
| Does Skill Play a Role in Market Value? | Examines the relationship between player skills and market value |

### 🏆 2.4 Club Report

This page provides insights into clubs, player distribution, and financial aspects of football teams.

**Key Performance Indicators (KPIs):**

- Number of Clubs
- Cost per Overall Rating
- Annual Wage-to-Value Ratio
- Number of Players

**Filters / Slicers:**

- Joined Year
- Club

**Visualizations:**

| Visualization | Purpose |
|---|---|
| Top 5 Clubs by Overall Rating | Highlights clubs with the highest overall player ratings |
| Value vs. Wage Across Ages | Explores the relationship between player market value, wages, and age |
| Top 10 Nationalities in Overall Clubs | Shows the most represented nationalities across clubs |
| Market Value Breakdown by Best Positions | Compares market value across player positions using a waterfall or stacked bar chart |

---

## 3. How to Use the Power BI Report

Follow these steps to explore the dashboard:

1. Open `FIFA21Project.pbix` using **Power BI Desktop**.
2. Ensure the exported Star Schema CSV files or the original data model are correctly connected.
3. Navigate to the desired report page using the home navigation buttons.
4. Use the slicers on the left side of each page to filter data by:
   - Nationality
   - Joined Year
   - Club
5. Explore the charts, KPIs, and visualizations.
6. Hover over visual elements to view additional tooltip information.
7. Use the navigation or back buttons to move between report pages.

All visuals and KPIs respond dynamically to the selected filters.

---

## 📂 Project Structure

The repository is organized as follows:

```text
FIFA21-Data-Analysis/
│
├── DataCleaningandSplittingPart.ipynb
│
├── fifa21 raw data v2.csv
│
├── fifa21_star_schema/
│   ├── fact_player.csv
│   ├── dim_player.csv
│   ├── dim_club.csv
│   ├── dim_nationality.csv
│   ├── dim_position.csv
│   ├── dim_contract.csv
│   └── dim_date.csv
│
├── FIFA21Project.pbix
│
└── README.md
```

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Data cleaning, preprocessing, and transformation |
| Pandas | Data manipulation and analysis |
| NumPy | Numerical operations |
| Matplotlib | Data visualization and exploration |
| Seaborn | Statistical data visualization |
| Jupyter Notebook | Interactive Python development environment |
| Power BI Desktop | Interactive dashboard development and reporting |
| DAX | Measures and analytical calculations |
| Star Schema | Dimensional data modeling |

---

## ✨ Key Features

- End-to-end data analysis workflow.
- Data cleaning and preprocessing using Python.
- Handling missing values and inconsistent data types.
- Data transformation and feature extraction.
- Star Schema dimensional modeling.
- Fact and dimension table separation.
- Interactive Power BI dashboard with multiple report pages.
- Dynamic KPIs and slicers.
- Cross-filtering between visualizations.
- Interactive tooltips and navigation buttons.
- Professional and consistent dashboard design.

---

## 🎯 Project Outcome

This project demonstrates the complete process of transforming raw football player data into a structured analytical solution.

By combining Python for data preparation and dimensional modeling with Power BI for interactive reporting, the project provides an organized and insightful way to explore FIFA 21 player statistics, performance attributes, club information, and market values.

**The project showcases practical skills in:**

- Data Analysis
- Data Cleaning & Transformation
- Python Programming
- Dimensional Data Modeling
- Star Schema Design
- Business Intelligence
- Power BI Dashboard Development
- Data Visualization

---

⭐ **If you find this project useful, feel free to star the repository!**
