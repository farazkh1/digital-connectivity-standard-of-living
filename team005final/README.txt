README.txt - Digital Connectivity and Standard of Living Project

DESCRIPTION
-----------
This project investigates the impact of digital connectivity, specifically fixed broadband access and internet usage, on global standards of living. Focusing on indicators like poverty rates and adult literacy levels, the analysis uses country-year panel data from the World Bank (covering 2013-2023), supplemented by historical fixed telephone subscription data used as an instrumental variable.

The project employs a multifaceted analytical approach to explore these relationships beyond simple correlations. Key methodologies include:
*   Data Loading and Preparation: Loads the main panel dataset (`finalCleanedByDevelopmentStatus.csv`) and historical telephone data (`54bd87ba-fe26-4ae0-9380-0cae854d4233_Data.csv`). Performs data cleaning, numeric conversions, log transformation of GDP per capita, selects a historical year (e.g., 2005) from the telephone data as an instrument, and merges it into the main dataset.
*   Descriptive Analysis: Includes summary statistics, correlation matrices, and visualizations (scatter plots for Broadband vs. Internet Use, Literacy, and Poverty; boxplots; heatmaps) to explore initial patterns.
*   Econometric Modeling: Utilizes Ordinary Least Squares (OLS), Fixed Effects (FE) panel models (controlling for country and time effects), Seemingly Unrelated Regressions (SUR), Quantile Regression (to assess effects across different outcome levels), and Two-Stage Least Squares (2SLS/IV) using historical telephone subscriptions as an instrument to address potential endogeneity.
*   Machine Learning: Employs Random Forest regressors to capture non-linear relationships and assess the relative importance of predictors for poverty.
*   Structural Equation Modeling (SEM): Explores potential mediating pathways, specifically the influence of connectivity on poverty operating indirectly through literacy.

The analysis reveals a complex picture. Fixed Effects models show a significant negative association between within-country increases in broadband subscriptions and poverty levels. However, OLS/SUR show mixed direct correlations, and the 2SLS analysis aimed at isolating a causal effect yielded a contradictory significant *positive* coefficient for broadband's impact on poverty, raising questions about model specification or instrument validity despite statistical relevance in the first stage. Random Forest indicates broadband is less important than life expectancy or literacy in predicting poverty. SEM suggests a plausible, though weak, indirect pathway via literacy. Internet *usage* consistently shows a negative correlation with poverty across several models. The overall goal is to provide empirical insights into these complex dynamics to inform discussions on digital development policy.

INSTALLATION
------------
To run the analysis presented in the Jupyter Notebook, you will need a Python environment with several libraries installed.

1.  **Prerequisites:**
    *   Python 3.x installed.
    *   `pip` (Python package installer) available.
    *   It is recommended to use a virtual environment (like `venv` or `conda`).

2.  **Install Required Libraries:**
    Create a file named `requirements.txt` in your project directory with the following content:
    ```
    pandas
    numpy
    matplotlib
    seaborn
    statsmodels
    scikit-learn
    linearmodels
    semopy
    jupyter
    ```
    Then, open your terminal or command prompt, navigate to the project directory, and run:
    ```bash
    pip install -r requirements.txt
    ```
    Alternatively, if using Google Colab, run the `!pip install ...` commands provided in the first code cell of the notebook at the start of each session.

3.  **Get the Data:**
    *   Ensure the following two CSV files are present in the same directory as the Jupyter Notebook:
        *   `finalCleanedByDevelopmentStatus.csv` (the main panel data)
        *   `54bd87ba-fe26-4ae0-9380-0cae854d4233_Data.csv` (containing historical fixed telephone subscription data)
    *   *Note:* The code currently expects the historical data file to have headers starting on the first line (header=0) after potential manual cleaning, and it uses the '2005' column by default as an instrument – modify the configuration variables in Block 1 of the notebook if your file structure or chosen instrument year differs.

4.  **Setup Complete:** Once the libraries are installed and the data files are in place, the setup is complete.

EXECUTION
---------
The primary analysis code and results are contained within the Jupyter Notebook file (`Final Project Code.ipynb`).

1.  **Launch Jupyter:**
    *   Open your terminal or command prompt, navigate to the project directory containing the notebook and the data files.
    *   Launch Jupyter Notebook or Jupyter Lab by typing:
        ```bash
        jupyter notebook
        ```
        or
        ```bash
        jupyter lab
        ```
    *   If using Google Colab, upload the notebook and the two CSV files.

2.  **Open the Notebook:**
    *   In the Jupyter interface, open the `Final Project Code.ipynb` file.

3.  **Run the Analysis:**
    *   Execute the cells sequentially, starting from the top. In Colab or Jupyter, you can select a cell and press Shift+Enter to run it and move to the next. Alternatively, use the "Run" menu options (e.g., "Run All").
    *   Ensure Block 1 (Setup and Data Preparation) completes successfully, including loading both datasets and merging the instrument variable, before running subsequent analysis blocks.

4.  **Expected Output:**
    *   Running the notebook will execute the data loading, preprocessing, merging, and various statistical models.
    *   Outputs will include:
        *   Printed status messages during data loading and preparation.
        *   Summary statistics and correlation matrix values.
        *   Generated plots (Boxplot, Scatter plots, Correlation Heatmap) saved as PNG files and displayed inline.
        *   Regression summary tables for OLS, FE Panel (Poverty), Quantile Regression, SUR, and 2SLS (including parameter estimates, p-values, R-squared, etc.).
        *   First-stage diagnostics for the 2SLS model.
        *   Random Forest feature importances and R-squared score.
        *   SEM standardized parameter estimates table.

5.  **Interpreting IV/2SLS:** Pay close attention to the output and interpretation notes for the 2SLS analysis in Block 9. While the first-stage F-statistic might indicate relevance, the validity (exogeneity) of the `historicalphonesper100_2005` instrument should be critically assessed based on theory, and the contradictory second-stage result should be noted.