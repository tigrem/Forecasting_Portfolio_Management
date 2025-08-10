# Time Series Forecasting for Portfolio Management

This project aims to apply time series forecasting to historical financial data to enhance portfolio management strategies for **Guide Me in Finance (GMF) Investments**. The goal is to provide data-driven insights for optimizing asset allocation, minimizing risks, and capitalizing on market opportunities.

## Project Structure

The project follows a structured approach, with a clear separation of code, data, and documentation.

Time-Series-Portfolio-Management/
├── data/
│   ├── processed/          # For cleaned and preprocessed data
│   └── row_data/           # For raw, downloaded data
├── notebooks/
│   ├── Preprocess_and_EDA.ipynb  # Jupyter notebook for data preprocessing and exploration
│   └── .ipynb_checkpoints/
├── reports/                # For final reports and visualizations
├── src/                    # For reusable Python scripts
├── venv/                   # Python virtual environment
├── .gitignore
├── LICENSE
├── README.md               # This file
└── requirements.txt        # Project dependencies


## Business Objective

The core business objective is to leverage advanced time series forecasting to:
- Predict market trends.
- Optimize asset allocation.
- Enhance portfolio performance for GMF's clients.

The focus is not on direct price prediction, but on understanding volatility, identifying momentum, and generating actionable insights for a broader decision-making framework.

## Data

The project utilizes historical financial data for three key assets, sourced from **YFinance** for the period from July 1, 2015, to July 31, 2025.

- **Tesla (TSLA):** A high-growth, high-risk stock.
- **Vanguard Total Bond Market ETF (BND):** A bond ETF for stability and income.
- **S&P 500 ETF (SPY):** A broad market index for diversified exposure.

The data includes daily metrics such as `Open`, `High`, `Low`, `Close` (adjusted for splits and dividends), and `Volume`.

## Task 1: Preprocessing and Exploratory Data Analysis (EDA)

This task focuses on loading, cleaning, and understanding the financial data to prepare it for subsequent modeling. The process is documented in the `notebooks/Preprocess_and_EDA.ipynb` file.

### Key Steps:

1.  **Data Extraction:** Used the `yfinance` library to download historical data for TSLA, BND, and SPY.
2.  **Data Cleaning:** Handled potential missing values (though YFinance data is generally clean) and ensured correct data types.
3.  **Exploratory Data Analysis (EDA):**
    -   **Visualization:** Plotted the adjusted closing prices and daily returns over time to visualize trends and volatility.
    -   **Rolling Statistics:** Calculated and plotted rolling means and standard deviations to understand short-term trends and fluctuations.
    -   **Outlier Detection:** Identified days with unusually high or low returns.
4.  **Stationarity Analysis:** Performed the **Augmented Dickey-Fuller (ADF) test** on both prices and returns to check for stationarity, a crucial prerequisite for many time series models.
5.  **Risk Metrics:** Calculated foundational risk metrics such as **Value at Risk (VaR)** and the **Sharpe Ratio** to assess potential losses and historical risk-adjusted returns for each asset.

## How to Run the Project

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/](https://github.com/)[tigrem/Time-Series-Portfolio-Management.git
    cd Time-Series-Portfolio-Management
    ```

2.  **Set up the virtual environment:**
    ```bash
    python -m venv venv
    # On Windows
    venv\Scripts\activate
    # On macOS/Linux
    source venv/bin/activate
    ```

3.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Run the Jupyter Notebook:**
    ```bash
    jupyter notebook notebooks/Preprocess_and_EDA.ipynb
    ```
    You can then execute the cells in the notebook to reproduce the data fetching, preprocessing, and analysis steps.

---

**Next Steps:** The insights from this EDA will inform the selection