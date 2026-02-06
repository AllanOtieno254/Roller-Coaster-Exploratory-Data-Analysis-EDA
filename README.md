# 🎢 Roller Coaster Exploratory Data Analysis (EDA)

This project performs a comprehensive Exploratory Data Analysis (EDA) on a dataset of roller coasters worldwide. Using **Python**, **Pandas**, and **Seaborn**, we clean raw historical data and visualize the relationships between speed, height, and year of introduction.

## 📌 Project Overview
The goal of this analysis is to understand the evolution of roller coasters over time and identify correlations between technical specifications like G-Force, Speed, and Height.

## 🛠️ Technologies & Setup
- **Language:** Python 3.12
- **Environment:** Google Colab
- **Libraries:** 
    - [Pandas](https://pandas.pydata.org): Data manipulation and cleaning.
    - [Matplotlib](https://matplotlib.org): Foundation for plotting.
    - [Seaborn](https://seaborn.pydata.org): Statistical data visualization.

### Initial Configuration
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

plt.style.use('ggplot')
pd.set_option('display.max_columns', 200)
## 📖 Data Pipeline

### 1. Data Ingestion & Subsetting
*   **Source:** `coaster_db.csv` (Accessed via [Google Drive](https://www.google.com) mount).
*   **Feature Selection:** Dropped redundant columns (e.g., website, manufacturer details) to focus on 13 key features including `Coaster_Name`, `Speed_mph`, `Height_ft`, and `Opening_Date`.

### 2. Data Cleaning
This stage was critical for ensuring data integrity:
*   **Type Casting:** Converted `opening_date_clean` to a proper [datetime](https://pandas.pydata.org) object.
*   **Renaming:** Standardized column names to **CamelCase** (e.g., `speed_mph` → `Speed_mph`) for better readability.
*   **Deduplication:** 
    *   Analyzed duplicates using subsets of `Coaster_Name`, `Location`, and `Opening_Date`.
    *   Used the inverse locator `~df.duplicated()` to keep only unique records.
    *   **Reset Index:** Performed a clean index reset after dropping rows.

### 3. Visual Analysis (Exploratory)
*   **Univariate:** Used Histograms and [KDE plots](https://seaborn.pydata.org) to analyze the distribution of `Speed_mph`.
*   **Bivariate:** Created Scatter Plots to visualize the relationship between `Speed_mph` and `Height_ft`.
*   **Multivariate:** Implemented Seaborn [pairplot](https://seaborn.pydata.org) to compare multiple numeric variables, segmented by `Type_Main` (e.g., Steel vs. Wood).

### 4. Correlation & Grouping
*   **Correlation Matrix:** Generated a [correlation matrix](https://pandas.pydata.org) using `df.corr()` to find hidden relationships between year, speed, and height.
*   **Location Analysis:** Grouped data by `Location` to find the average speed, filtering for locations with at least 10 coasters to ensure statistical relevance.

## 📊 Key Findings
*   **Positive Correlation:** As expected, height and speed are highly correlated; the taller the coaster, the faster it tends to be.
*   **Evolution:** Modern coasters (visualized by `Year_Introduced`) show a trend toward higher speeds and more inversions compared to historical models.
*   **Regional Trends:** Certain locations consistently host "faster" coasters on average, as highlighted in the horizontal bar chart analysis.

## 🚀 How to Use
1.  **Mount** your Google Drive in Colab.
2.  **Ensure** your dataset is located at `/content/EDA/MyDrive/Colab Notebooks/.../coaster_db.csv`.
3.  **Run** the cells sequentially to reproduce the visualizations and cleaning steps.
