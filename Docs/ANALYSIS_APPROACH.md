 # Analysis Approach – International River-System Toxin Level Analysis
 
Author: Apollo Konstantinell
Project: International River-System Toxin Level Analysis
Dataset: National_River_Toxin_Dataset_1.csv

# 1. Objective
The goal of this analysis was to perform an exploratory data analysis (EDA) and a basic toxicological study on water quality and heavy metal concentrations across major global river systems. 

The focus was on understanding mercury (Mercury) pollution burdens and environmental parameters with primary focus on pH levels to map temporal and regional trends as well as evaluate statistical relationships for purposes of international environmental advocacy.

# 2. Dataset Overview
* Source File: National_River_Toxin_Dataset_1.csv
* Records: 1,305 observations
* Time Period: 2018 – 2022
* Key Variables:
    * Date 
    * River_System 
    * pH_Level
    * Temperature
    * Lead
    * Mercury
    * Arsenic
    * Nitrates
    * Phosphates
    * Dissolved_Oxygen

# 4. Analysis Workflow
   
#### Step 1. Environment Setup & Imports
Required libraries were imported for data cleaning, manipulation, visualisation and statistical analysis:
• pandas & numpy: Data manipulation and structural profiling
• matplotlib.pyplot & seaborn: visualization
• scipy.stats: hypothesis testing
• sklearn.linear_model: simple linear regression

#### Step 2. Data Loading
The dataset was ingested using pd.read_csv().

#### Step 3. Initial Data Exploration
• Exploration of the first and last 15 rows with .head(15) and .tail(15).
• Checked data types and basic statistics with .info() and .describe().T.
• Determined dataset shape with .shape().

#### Step 4. Missing Value Handling
• Evaluated missing values across all columns using .isna().sum() and .isna().mean(), discovering that variables had missing values ranging from 1.5% to 3.1% (well below the 5% threshold of scientific insignificance).
• Established that data loss occurred at random (human logging error) and implemented a loop over numeric features (pH_Level, Temperature, Lead, Mercury, Arsenic, Nitrates, Phosphates, Dissolved_Oxygen) to fill missing values using their respective attribute medians.

Medians were chosen explicitly to prevent outliers and heavy pollution spikes from distorting the baseline data distribution.

#### Step 5. Data Type Conversion
• Converted the Date column using pd.to_datetime() to enable temporal operations.

#### Step 6. Checking for Duplicates
• Executed a duplicate entry check using .duplicated(), verifying zero duplicate rows.

#### Step 7. Focus Toxin Decision Matrix
• Compared contaminant levels against official environmental safety standards (EU Groundwater Directive 2006/118/EC).
• Evaluated Nitrates (safe threshold 50 ppm; dataset max 16.55 ppm) and Phosphates (safe threshold 0.05 - 0.1 ppm; dataset max 0.87 ppm) to eliminate them as critical threats.
• Developed a Hazard Assessment Matrix evaluating Lead (threshold 1.2 ppb) and Mercury (threshold 0.07 ppb) to calculate total exceeded records, rate of exceedance, average hazard severity, and maximum spike hazard severity.

Key Observation(s): 
Mercury exceeded its legislative safety limit in 100% of all 1,305 observations across the dataset, maintaining the average hazard severity of 8.52x the legal threshold, with peak pollution spikes reaching 15.11x the safety limit. Mercury was then selected as the focus for the analysis.

#### Step 8. Ranking River-Systems
Grouped the dataframe by River_System and sorted it in descending order to identify the ranking of the river systems.

Key Observation(s): 
• The Yangtze River (0.79 ppb) and the Nile River (0.70 ppb) ranked highest with toxicity levels high above the 0.07 ppb safety threshold.

#### Step 9. Hypothesis Testing (Independent Two-Sample T-Test)
Conducted an independent two-sample t-test to check if the difference in the average Mercury contamination levels for Yangtze and Nile rivers was statistically significant.
    Results: 
    • T-statistic ≈ 8.8344 
    • p-value = near zero
    • Conclusion: There is a statistically significant difference in Mercury concentrations between the Yangtze and Nile river systems. The null hypothesis is rejected

#### Step 10. Correlation
Calculated the Spearman Rank Correlation across water pH and Mercury levels.
    Results: 
    • Correlation coefficient ≈ 0.14 
    • Conclusion: This suggesting that as water becomes more basic/alkaline, detected mercury levels increase. Because heavy metals naturally show a negative correlation with pH, this anomalous positive relationship suggests irregular, disorganized industrial dumping.

#### Step 11. Linear Regression Analysis
Fitted a  simple linear regression model for water pH_Level and Mercury, treating pH_Level as the independent predictor and Mercury as the dependent target.
    Results:
    • Regression coefficient of Mercury ≈ 0.0691
    • Regression intercept of Mercury ≈ 0.0884. 
    • Conclusion: This model predicts that for every unit increase in water pH, mercury contamination rises by 0.0691 ppb — a spike that almost single-handedly matches the entire safe legal threshold of 0.07 ppb.

#### Step 12. Time-Series and Seasonality Analysis (2018–2022)
• Aggregated data into a chronological Month-Year matrix, with both baseline medians and peak maximums to isolate baseline from acute events, in the form of Hazard Quotient (HQ).
• Extracted variables by Year-Month from the converted datetime column and generated a comprehensive visual line graph tracking global median-average Mercury concentration levels over time.
• Mapped the numerical months into seasonal bins onto a box graph, showing that peak exposure and toxicity surges occurred during the Winter and Spring months, though baseline toxicity remained high all year.

#### Step 13. Toxicological Correlation Heatmap for Water_pH and Contaminates Levels
Generated a heatmap for a comprehensive overview of correlation statistics for the various toxins and water pH. A clear and simple way to communicate the information to stakeholders.

#### Step 14. Visualization of Average Mercury Levels
Created a bar chart displaying the median-average Mercury levels across all five river systems, labeling each bar with its ppb value, clearly displaying pollution disparities for stakeholders.

#### Step 15. Conclusion & Interpretation
Synthesized findings into clear insights:
• Successfully mapped the baseline of heavy metal pollution, providing clear evidence that every monitored river system fails in safe levels of toxicity for Mercury.
• Documented a positive toxicological correlation between water pH increases and spikes in heavy metals, showing signs of industrial chemical waste.
• Demonstrated that while a global baseline exists, pollution levels vary significantly across geographic regions (Yangtze vs. Nile) and season (Winter/Spring surges), proving the necessity of targeted local regulations over broad, generalized frameworks.

# 6. Tools & Techniques Used

| Technique                     |	Purpose                                                                        |
|-------------------------------|--------------------------------------------------------------------------------|
| Descriptive statistics        |	Base understanding of data                                                     |
| Median Value Imputation       |	Treatment of missing values while preserving distribution shape                |
| Datetime Conversion           | Enabling timeseries analysis                                                   |
| Hazard Assessment (HA) Matrix |	Filtering and isolation of toxin to determine the focus of the analysis        |
| GroupBy Aggregation           |	Compress regional records into clear, ranked river-level metrics               |
| Bar Charts & Line Graphs      |	Visual communication of findings                                               |
| Two-Sample T-Test	            | Testing for statistical meaningful differences                                 |
| Simple Linear Regression	    | Relationship exploration between pH levels and Mercury                         |
| Spearman Correlation Heatmap  |	Investigation of statistical relationships between water pH levels and Mercury |

# 5. Key Takeaways from the Approach

• Data Quality First – Cleaning and handling missing values was performed early to ensure reliable results.
• Variable Filtering – selection of focus toxin for analysis though screening records against regulatory metrics.
• Progressive Analysis – Started with global averages, moved on to system-level comparisons and applied statistical tests.
• Visualization + Statistics – Combined visual storytelling with rigorous statistical testing.
• Actionable Insights – Focused on findings that support real-world environmental decision-making.

# 6. Files Related to This Analysis
• Full interactive analysis: Notebooks/International River Toxin  Analysis.ipynb
• PDF report: Docs/International River Toxin Analysis.pdf
• Visualization screenshots: Assets/

This document outlines the structured analytical approach followed throughout the project.
