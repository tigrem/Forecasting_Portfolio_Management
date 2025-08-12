Time Series Forecasting for Portfolio Management

This project aims to apply time series forecasting to historical financial data to enhance portfolio management strategies for Guide Me in Finance (GMF) Investments. The goal is to provide data-driven insights for optimizing asset allocation, minimizing risks, and capitalizing on market opportunities.
Project Structure

The project follows a structured approach, with a clear separation of code, data, and documentation.

Time-Series-Portfolio-Management/
├── data/
│   ├── processed/          # For cleaned and preprocessed data
│   └── row_data/           # For raw, downloaded data
├── notebooks/
│   ├── Preprocess_and_EDA.ipynb  # Jupyter notebook for data preprocessing and exploration
│   ├── Forecasting_Models.ipynb  # Jupyter notebook for forecasting, optimization, and backtesting
│   └── .ipynb_checkpoints/
├── reports/                # For final reports and visualizations
├── src/                    # For reusable Python scripts
├── venv/                   # Python virtual environment
├── .gitignore
├── LICENSE
├── README.md               # This file
└── requirements.txt        # Project dependencies
Business Objective

The core business objective is to leverage advanced time series forecasting to:

    Predict market trends.

    Optimize asset allocation.

    Enhance portfolio performance for GMF's clients.

The focus is not on direct price prediction, but on understanding volatility, identifying momentum, and generating actionable insights for a broader decision-making framework.
Data

The project utilizes historical financial data for three key assets, sourced from YFinance for the period from July 1, 2015, to July 31, 2025.

    Tesla (TSLA): A high-growth, high-risk stock.

    Vanguard Total Bond Market ETF (BND): A bond ETF for stability and income.

    S&P 500 ETF (SPY): A broad market index for diversified exposure.

The data includes daily metrics such as Open, High, Low, Close (adjusted for splits and dividends), and Volume.
Task 1: Preprocessing and Exploratory Data Analysis (EDA)

This task focuses on loading, cleaning, and understanding the financial data to prepare it for subsequent modeling. The process is documented in the notebooks/Preprocess_and_EDA.ipynb file.
Key Steps:

    Data Extraction: Used the yfinance library to download historical data for TSLA, BND, and SPY.

    Data Cleaning: Handled potential missing values (though YFinance data is generally clean) and ensured correct data types.

    Exploratory Data Analysis (EDA):

        Visualization: Plotted the adjusted closing prices and daily returns over time to visualize trends and volatility.

        Rolling Statistics: Calculated and plotted rolling means and standard deviations to understand short-term trends and fluctuations.

        Outlier Detection: Identified days with unusually high or low returns.

    Stationarity Analysis: Performed the Augmented Dickey-Fuller (ADF) test on both prices and returns to check for stationarity, a crucial prerequisite for many time series models.

    Risk Metrics: Calculated foundational risk metrics such as Value at Risk (VaR) and the Sharpe Ratio to assess potential losses and historical risk-adjusted returns for each asset.

Task 2: Time Series Forecasting

This task focused on building a forward-looking perspective for the high-growth asset, TSLA. An advanced deep learning model was chosen to capture complex patterns in the data. The process is documented in the notebooks/Forecasting_Models.ipynb file.
Key Steps:

    Model Selection: An LSTM (Long Short-Term Memory) neural network was selected as the forecasting model due to its suitability for complex, non-linear time series data.

    Data Preparation: Historical TSLA price data was scaled using MinMaxScaler and converted into sequential data for model training.

    Model Training: A Keras Sequential model was built and trained on the prepared data.

    Future Prediction: The trained LSTM model was used to generate a 12-month (252 trading days) rolling forecast for TSLA prices. The output of this forecast provided a projected annualized return for the asset.

Task 3: Portfolio Optimization

This task leveraged the forecast from Task 2 to construct an optimal portfolio using Modern Portfolio Theory (MPT) principles. The process is documented in the notebooks/Forecasting_Models.ipynb file.
Key Steps:

    Expected Returns: The expected return for TSLA was taken from the LSTM forecast, while the expected returns for BND and SPY were calculated from their historical averages.

    Covariance Matrix: A covariance matrix was computed from the historical daily returns of all three assets to quantify their interdependencies.

    Efficient Frontier Generation: A Monte Carlo simulation generated 5,000 random portfolios to plot the Efficient Frontier, identifying portfolios that offer the best return for a given level of risk.

    Optimal Portfolios: Two key portfolios were identified: the Minimum Volatility Portfolio (lowest risk) and the Maximum Sharpe Ratio Portfolio (highest risk-adjusted return).

Task 4: Strategy Backtesting and Performance Evaluation

The final task was to validate the effectiveness of the recommended portfolio strategy through a backtesting simulation. The process is documented in the notebooks/Forecasting_Models.ipynb file.
Key Steps:

    Benchmark Selection: A traditional 60/40 portfolio (60% SPY, 40% BND) was chosen as the benchmark for performance comparison.

    Backtesting Simulation: A one-year backtest was run from July 29, 2024, to July 30, 2025, comparing the performance of the Maximum Sharpe Ratio portfolio against the benchmark.

    Performance Metrics: The final cumulative return and Sharpe Ratio for both portfolios were calculated and compared. The backtest confirmed that the model-driven strategy significantly outperformed the benchmark in both total return and risk-adjusted return.

Conclusion and Next Steps

The project successfully demonstrated a robust, data-driven framework for portfolio optimization that integrates advanced time series forecasting. The methodology produced a strategy that was empirically validated to outperform a traditional benchmark.

Future work could include:

    Refining the LSTM model and exploring other forecasting models for different asset classes.

    Expanding the asset universe to include more stocks, commodities, or currencies.

    Implementing more sophisticated risk management techniques and stress-testing the model against various market scenarios.

How to Run the Project

    Clone the repository:

    git clone [https://github.com/](https://github.com/)[your-repo-name.git
    cd Time-Series-Portfolio-Management


    Set up the virtual environment:

    python -m venv venv
    # On Windows
    venv\Scripts\activate
    # On macOS/Linux
    source venv/bin/activate


    Install dependencies:

    pip install -r requirements.txt


    Run the Jupyter Notebooks:

    jupyter notebook notebooks/Preprocess_and_EDA.ipynb
    jupyter notebook notebooks/Forecasting_Models.ipynb


    You can then execute the cells in the notebooks to reproduce the data fetching, preprocessing, analysis, and modeling steps.