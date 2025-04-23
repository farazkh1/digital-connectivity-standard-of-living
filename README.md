# Digital Connectivity and Standard of Living: Investigating the Impact of Broadband Access

**Team 5 | Georgia Institute of Technology | Data Visualization and Analytics**

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


## Setup and Installation

1.  **Clone Repository:**
    ```bash
    git clone https://github.com/farazkh1/digital-connectivity-standard-of-living.git
    ```
2.  **Create Environment (Recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```
3.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
4.  **Add Data:** Download the required CSV files (see Data section and `data/README_DATA.md`) and place them inside the `data/` folder.

## Usage and Execution

1.  **Launch Jupyter:** Activate your environment and run:
    ```bash
    jupyter lab
    # or jupyter notebook
    ```
2.  **Open Notebook:** Navigate to the `notebooks/` directory and open `Final Project Code.ipynb`.
3.  **Run Analysis:** Execute the cells sequentially (e.g., using Shift+Enter or "Run All Cells"). Ensure Block 1 (Data Loading/Prep/Merge) completes successfully before proceeding.
4.  **Outputs:** The notebook will print model summaries and display/save plots (e.g., in the `results/` directory if configured).

## Key Findings Summary

The analysis revealed complex and sometimes conflicting results:
*   **Fixed Effects (FE):** Showed a significant *negative* association between within-country broadband subscription growth and poverty rates over time (Coef: -0.1270, p<0.001). The association with literacy was `[Insert Your Finding: e.g., positive and significant / insignificant]`.
*   **Instrumental Variable (2SLS):** Attempting to isolate causality using historical (2005) telephone data as an instrument yielded a contradictory significant *positive* effect of broadband on poverty (Coef: +0.1113, p=0.0001).
*   **Other Methods:** OLS/SUR correlations for subscriptions were mixed. Random Forest ranked broadband's predictive importance below core development indicators. Quantile Regression showed puzzling positive effects on poverty. SEM suggested only a weak indirect pathway via literacy. Internet *usage* showed more consistent expected correlations.

## Limitations

*   **Endogeneity:** Remains a concern despite FE/IV attempts, as highlighted by conflicting 2SLS results.
*   **Instrument Validity:** The exogeneity of the historical telephone instrument might be questionable.
*   **Data:** Country-level aggregation, potential measurement errors, reliance on imputation for some data.
*   **Scope:** Focus on fixed broadband access metrics.

## Conclusion

While FE models suggest a beneficial within-country link between broadband expansion and poverty reduction, establishing a clear causal effect is challenging. The contradictory IV result underscores this difficulty. Policies should likely focus not just on infrastructure access (subscriptions) but critically on promoting affordable and effective *usage* and digital literacy.

## Team

*   Dominique Rever
*   Faraz Khojasteh Far
*   Justin Siegel
*   Jonathan Meystrik
*   Braden Thorne
*   Dhruv Modi

## Acknowledgements

*   Georgia Institute of Technology - Data Visualization and Analytics Course
*   The World Bank - World Development Indicators Data
