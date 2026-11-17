# International River System Toxin Level Analysis

**Author:** Apollinaria Konstantinell
**License:** MIT  

An in-depth exploratory data analysis (EDA) focusing on examining Mercury concentration levels, water chemistry parameters, and toxin variations across major global river systems (Amazon, Nile, Yangtze, Mississippi, Danube) for the period of 2018 to 2022 
This project was conducted using Python and Jupyter Notebook.

# Project Overview

This analysis investigates global water quality and toxin levels using the Dataset/Raw/National_River_Toxin_Dataset_1.csv dataset, covering 1305 records across 10 attributes covering  distribution and characteristics of key ecological indicators. 

# What this project covers

- Loading, profiling, cleaning data
- Documenting median imputation for missing values.
- Referencing against **EU Directive 2006/118/EC** for safety thresholds and creating Hazard Quotients (HQ)
- Calculation of average toxin levels per river system
- Identification of the most polluted river system by Mercury contamination levels
- Time-series and seasonal visualizations (2018–2022)
- Statistical hypothesis testing (two-sample t-test)
- Simple linear regression exploring the relationship between pH and Mercury concentrations
- Clear visual summaries (bar charts, line graphs) stored in the Assets folder
- A full PDF report of the analysis available in the Docs folder
- Detailed documentation of the full analysis approach and methodology
  
# Analysis Approach

A complete step-by-step breakdown of the analytical methodology used in this project is available here:
**[Docs/ANALYSIS_APPROACH.md](https://github.com/ApolloKonstantinell/International-River-System-Toxin-Level-Analysis/blob/main/Docs/ANALYSIS_APPROACH.md)**

This document covers:
- Data loading & cleaning process
- Missing value handeling strategy
- EU regulatory threshold screening
- Descriptive statistics and ranking of polluted river systems
- Time-series visualization approach
- Statistical t-test
- Simple linear regression modelling
- Key takeaways and interpretation of findings

# Dataset Information

**File:** Dataset/Raw/National_River_Toxin_Dataset_1.csv

| Column              | Description                                      |
|---------------------|--------------------------------------------------|
| Date                | Sampling date (2018-01-01 to 2022-12-26)         |
| River_System        | Name of the river system                         |
| pH_Level            | Acidity / alkalinity of the water                |
| Temperature         | Water temperature                                |
| Lead                | Lead concentration                               |
| Mercury             | Mercury concentration                            |
| Arsenic             | Arsenic concentration                            |
| Nitrates            | Nitrate levels                                   |
| Phosphates          | Phosphate levels                                 |
| Dissolved_Oxygen    | Dissolved oxygen concentration                   |

# Key Findings from the Analysis

#### Regulatory Thresholds

Nitrates and phosphates remained within EU limits, whereas Lead and Mercury consistently exceeded safety thresholds.
* Mercury exceeded 100%, with an average severity of 8.52x.
* Lead exceeded 98.5%, with average severity of 2.51x.

#### Most Polluted Systems (Mercury)

* Yangtze recorded the highest median (~0.79 ppb)
* Nile followng (~0.70 ppb)
* Mississippi (~0.60 ppb)
  
#### Statistical Insights

* Two-sample t-test between the Yangtze and Nile (t-test ~ 8.8344, p < 0.0001) confirmed statistically significant distinction between the two river systems.
* Regression analysis showed positive relationship between alkalinity (Water_pH) and heavy metal concentrations (Mercury).
    * Linear Regression **Coeffitient** of Mercury based on pH levels: ~0.0691
    * Linear Regression **Intercept** of Mercury Based on pH levels: ~0.0884

# Implications

By looking over the base contamination levels of the systemns we can see that overal toxicity levels are of a large scale, with all monitored rivers systems (Yangtze: 0.79 ppb, Nile: 0.70 ppb, Mississippi: 0.60 ppb, Amazon: 0.49 ppb, Danube 0.40 ppb) far above the safety threshold of 0.07 ppb. These levels combined with the low correlation of high pH and elevation of Mercury we **can constitute that the likelyhood of large scale systematic chemical dumping is low - however investigation of industrial activity is be advisable**.
With clear uptake of toxin levels in the winter (December, January, Febriary) and spring (March, April, May) months, close monitoring should take place during these period of time.
Looking at Toxicological Correlation Heatmap with correlation between 0.56 to 0.7 there is a strong statistical certainty that Lead and Arsenic will be found in the water as well. A study of industries using these chemicals in the reagion(s) should be conducted and if local legislature allows, audited.
The effects of toxin exposure in the local wild life and population should be documented and compiled to strengthen the case for stronger regulatory restrictions on industrial waste disposal.
A deep look into national and local legislature should to be conducted in order to navigate and pin-point strategy for regulatory change.

# How to Run the Analysis

1. **Clone the repository:**

   git clone https://github.com
   cd International River System Toxin Level Analysis
  
2. **Install dependencies:**
   
   pip install -r requirements.txt
   
3. **Run the Jupyter Notebook:**

   jupyter notebook "Notebooks/International River Toxin  Analysis.ipynb"

   *(Ensure path points to Dataset/Raw/National_River_Toxin_Dataset_1.csv)* 

# Technologies Used

* Python
* Pandas – data loading and manipulation
* NumPy – numerical operations
* Matplotlib & Seaborn – data visualization
* SciPy (stats) – statistical tests (t-test)
* Sklearn.linnear_model (LinearRegression) – linear regression
* Jupyter Notebook – interactive analysis and documentation

# Visual Output
Graph screenshots and key visualizations from the notebook are stored in the [Assets/](https://github.com/ApolloKonstantinell/International-River-System-Toxin-Level-Analysis/tree/main/Assets) folder.
A complete written report (including both code explanations and visuals) is available as a PDF in the [Docs/](https://github.com/ApolloKonstantinell/International-River-System-Toxin-Level-Analysis/tree/main/Docs) folder.
A detailed explanation of the full analysis methodology can be found in [Docs/ANALYSIS_APPROACH.md](https://github.com/ApolloKonstantinell/International-River-System-Toxin-Level-Analysis/blob/main/Docs/ANALYSIS_APPROACH.md).

# License

This project is released under the MIT License. See the [LICENSE](LICENSE) file for full details.
#  Author

**Apollinaria Konstantinell** ([GitHub Profile](https://github.com/ApolloKonstantinell))
