# Digital Connectivity and Standard of Living: Investigating the Impact of Broadband Access

**Team 5 | Georgia Institute of Technology | Data Visualization and Analytics**

## Overview

This project investigates the complex relationship between digital connectivity (specifically fixed broadband access and internet usage) and key standard-of-living indicators (poverty rates, adult literacy) across the globe. Using a comprehensive panel dataset from the World Bank (2013-2023) combined with historical instrumental variable data, we employ a multi-method analytical strategy in Python alongside interactive visualizations in Tableau to move beyond simple correlations and explore potential causal links and nuances.

Our motivation stems from the persistent "digital divide" and the need for robust evidence to guide policies aimed at leveraging connectivity for equitable socioeconomic progress.

## Approaches

We utilized a combination of modern econometric and machine learning techniques within a Python environment, complemented by data exploration via Tableau:

*   **Data Handling:** Two-tiered imputation for missing panel data; merging of historical (2005) fixed telephone data as an instrumental variable.
*   **Descriptive Analysis & Visualization (Python & Tableau):** Correlations, Scatter Plots, Maps, Trends generated using Matplotlib/Seaborn and interactively explored via a Tableau Dashboard.
*   **Econometric Models (Python - statsmodels, linearmodels):** OLS, Fixed Effects (FE) Panel (Country + Time), SUR, Quantile Regression (QR), 2SLS (IV).
*   **Machine Learning (Python - scikit-learn):** Random Forests (RF) for non-linearity & variable importance.
*   **Structural Modeling (Python - semopy):** SEM for pathway analysis (e.g., Broadband → Literacy → Poverty).

This multi-tool approach allows for robustness checks (FE, 2SLS), exploration of complex relationships (RF, QR, SEM), and effective communication of findings through static (Python) and interactive (Tableau) visualizations.

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

The analysis yielded complex results, highlighting the difficulty in isolating causal impacts:

*   **Within-Country Association (FE):** Fixed Effects models consistently show a significant **negative association** between increases in broadband subscriptions *within* countries and **poverty rates** over time (Coef: -0.1270, p<0.001). A significant **positive association** was found with **literacy rates** (Coef: +0.0790, p<0.001).
*   **Conflicting Causal Estimate (2SLS):** Using historical (2005) telephone lines as an instrument for broadband yielded a statistically significant but **contradictory *positive* effect** on poverty (Coef: +0.1113, p=0.0001), suggesting potential issues with endogeneity or instrument validity despite first-stage relevance.
*   **Predictive Importance (RF):** Broadband subscriptions ranked lower than life expectancy and literacy in predicting poverty levels.
*   **Other Models:** OLS/SUR correlations were mixed/counter-intuitive for subscriptions. Quantile Regression showed puzzling positive coefficients for broadband's effect on poverty. SEM suggested only a weak indirect link via literacy. Internet *usage* showed more consistent expected correlations (negative with poverty).

## Limitations

*   **Endogeneity:** Remains a concern despite FE/IV attempts, as highlighted by conflicting 2SLS results.
*   **Instrument Validity:** The exogeneity of the historical telephone instrument might be questionable.
*   **Data:** Country-level aggregation, potential measurement errors, reliance on imputation for some data.
*   **Scope:** Focus on fixed broadband access metrics.

## Conclusion

Fixed Effects analysis supports a link between within-country broadband expansion and improvements in poverty and literacy. However, the contradictory 2SLS results prevent strong causal claims based on subscriptions alone. The findings emphasize the complexity of the digital divide and suggest policies should focus on both infrastructure *and* promoting effective, affordable internet *usage* and skills. Visualizations in Tableau aid in exploring geographic disparities and trends.

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
