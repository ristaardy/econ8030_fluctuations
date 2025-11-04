# Business Cycle & Crises: Macro-Micro Analysis

## Project Objective
This project analyzes business cycle dynamics across multiple countries and investigates the transmission mechanisms of economic crises—specifically the Global Financial Crisis (GFC) and the COVID-19 Recession—by comparing macro-level indicators with micro-level firm responses using Compustat data.


## Project Structure

```
econ8030_fluctuations/
├── ECON8030_Group_Project_2_Fluctuations.ipynb     # Main Python Notebook containing all data cleaning, analysis, and visualization.
└── README.md                                       # Project documentation.

```

## Data Sources and Processing
The analysis utilizes a combination of macroeconomic and microeconomic data, integrating time-series and panel data analysis.

- **Data Source**:
  - Macroeconomic Data (Task 1 & 2): OECD.
  - Firm-Level Data (Task 3): WRDS Compustat (Annual Data).

- **Countries Selected**:
  - Cross-Country Analysis (Task 1): United States (`USA`), United Kingdom (`UK`), and Canada (`CAN`).
  - Event Study (Task 2): United States (USA) during the GFC (2007–2009) and the COVID-19 Recession (2020).
  - Firm-Level Analysis (Task 3): U.S. Public Firms (Focusing on GFC).

- **Variables Used and Treatment**:
  | Variable Set | Variables (Code) | Treatment Method | Purpose in Analysis |
  | :--- | :--- | :--- | :--- |
  | **Macro (Output/Demand)** | `GDP_NC`, `GFCF_NC`, `CONS_NC`, `SHARE_PRICE` | Detrending via HP Filter ($\lambda=1600$) | To isolate the cyclical component (business cycle). |
  | **Macro (Rates/Labor)** | `UNEMPLOY`, `L/S_INTEREST_RT`, `Inflation_QoQ` | Direct Use | Inherently cyclical/stationary variables used for volatility and correlation analysis. |
  | **Firm-Level (Ratios)** | `npm_WINS`, `roce_WINS`, `sale_invcap_WINS` | Winsorizing (1st & 99th percentile) | Measures of profitability, return, and capital efficiency. |
  | **Firm-Level (Classifiers)** | `AT`, `GSECTOR` | Used for cross-sectional grouping (Size vs. Sector). | To analyze differential firm responses. |

- **Data Cleaning and Transformation**:
  - Macro Time Series: All level variables (GDP, Investment, Consumption, Share Price) were transformed using natural logarithms prior to detrending. The final dataset was indexed using a Quarterly PeriodIndex (freq='Q') for accurate time-series operations.
  - Firm-Level Panel (Task 3): The Compustat panel was initially constructed using quarterly frequency but was aggregated to annual frequency to match the available fundamental financial data (AT, GSECTOR).
  - Outlier Mitigation (Task 3): To prevent extreme values from distorting the median performance analysis, all key firm-level ratios (NPM, ROCE, Sale/InvCap) were subjected to winsorizing. This involved capping the values at the 1st and 99th percentiles of their distribution. This cleaning step ensures that the median accurately reflects the typical firm's performance rather than isolated outliers.

- **Analytical Methodology**:
  | Task | Core Methodologies Used | Key Findings Demonstrated |
  | :--- | :--- | :--- |
  | **Task 1** | HP Filter, Relative Volatility, Correlation Coefficient | Confirmed Investment is highly volatile; Consumption is procyclical and smooth. |
  | **Task 2** | Event Study, Peak-to-Trough Analysis | COVID-19 was shorter (3 quarters) but more severe than the GFC (7 quarters), highlighting different impulse shocks. |
  | **Task 3** | Compustat Panel Analysis (Annual), Cross-Sectional Comparison (Size/Sector) | Large Firms suffered a greater relative collapse in margins, but Industrials and Small Firms demonstrated signs of quicker operational cost-cutting resilience. |


## Instructions for Replicating the Work
1. Clone this repository:
   ```
   git clone https://github.com/ristaardy/econ8030_fluctuations.git
   cd business_cycle_firm_response
   ```

2. Make sure the required Python libraries are installed:
   ```
   pip install pandas matplotlib seaborn numpy statsmodels
   ```
3. Open the notebook in Jupyter or Google Colab:
   ```
   jupyter notebook group_project_2_fluctuations.ipynb
   ```
4. Crucial Step: Due to large data sizes, ensure all Google Sheet import links within the notebook are accessible or replaced with local CSV files containing the required data.
5. Run all cells sequentially to reproduce the entire data cleaning, analysis, and visualization workflow.

## Contributors
- [@ristaardy](https://github.com/ristaardy)  
- [@EleanorM3](https://github.com/EleanorM3)

   ---
