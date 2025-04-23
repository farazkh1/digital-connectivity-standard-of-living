# Digital Connectivity and Standard of Living: Investigating the Impact of Broadband Access

**Team 5 | Georgia Institute of Technology | Data Visualization and Analytics**

Dominique Rever | Faraz Far | Justin Siegel | Jonathan Meystrik | Braden Thorne | Dhruv Modi

## Overview

This project investigates the complex relationship between digital connectivity (specifically fixed broadband access and internet usage) and key standard-of-living indicators (poverty rates, adult literacy) across the globe. Using a comprehensive panel dataset from the World Bank (2013-2023) combined with historical instrumental variable data, we employ a multi-method analytical strategy to move beyond simple correlations and explore potential causal links and nuances.

Our motivation stems from the persistent "digital divide" and the need for robust evidence to guide policies aimed at leveraging connectivity for equitable socioeconomic progress.

## Approaches

We utilized a combination of modern econometric and machine learning techniques:

*   **Data Handling:** Two-tiered imputation for missing panel data; merging of historical (2005) fixed telephone data as an instrumental variable.
*   **Descriptive Analysis:** Correlations, Scatter Plots, Maps, Trends via Matplotlib/Seaborn.
*   **Econometric Models:** OLS, Fixed Effects (FE) Panel (Country + Time), SUR, Quantile Regression (QR), 2SLS (IV).
*   **Machine Learning:** Random Forests (RF) for non-linearity & variable importance.
*   **Structural Modeling:** SEM for pathway analysis (e.g., Broadband → Literacy → Poverty).

This multi-method approach allows for robustness checks and provides a more nuanced understanding than single-model analyses, particularly when dealing with potential endogeneity using FE and 2SLS.

## Data

*   **Source:** Primarily downloaded from the World Bank's World Development Indicators (WDI) database.
*   **Files Required:**
    1.  `finalCleanedByDevelopmentStatus.csv`: Main country-year panel (2013-2023). Contains connectivity, economic, demographic, education, health indicators. (~217 entities, ~11 years each, ~2387 observations).
    2.  `54bd87ba-fe26-4ae0-9380-0cae854d4233_Data.csv` (or similar WDI download): Contains historical data for "Fixed telephone subscriptions (per 100 people)" (`IT.MLT.MAIN.P2`). The analysis uses the value from **2005** as the instrumental variable.
*   **Note:** These data files should be placed in the `data/` directory. See `data/README_DATA.md` for details.

## Repository Structure
