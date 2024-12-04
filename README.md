# Predicting-Oil-Spot-Prices-Using-Time-Series-Data

Oil prices have a profound impact on global economies, influencing everything from
transportation costs to inflation rates. Accurate predictions of oil spot prices are
invaluable for investors, policymakers, and industries reliant on oil. By anticipating price fluctuations, stakeholders can make informed decisions to hedge risks, optimize supply chains, and implement appropriate fiscal policies. This project aims to explore an unique approach to forecasting using factors such as financial market indicators (e.g., S&P 500 Index, VIX), macroeconomic factors (e.g., interest rates, DXY Index), and daily headline sentiment scores, which are less explored in combination.


\section{Methodology}

\subsection{Proposed Methods}
\begin{enumerate}
    \item \textbf{Data Collection and Preprocessing:}
    \begin{itemize}
        \item Gather historical oil spot prices and potential predictor variables:
        \begin{itemize}
            \item Asset Classes: S\&P 500, Gold, Metals.
            \item Macroeconomics: Interest Rates, EV Sales, Carbon Pricing, Sustainability Indexes.
            \item Volatility Index (VIX).
            \item Middle East/OPEC Sentiment Analysis.
        \end{itemize}
        \item Clean and normalize data to ensure consistency.
    \end{itemize}
    
    \item \textbf{Exploratory Data Analysis (EDA):}
    \begin{itemize}
        \item Visualize time series data to identify trends, seasonality, and anomalies.
        \item Correlation analysis between oil prices and predictor variables.
    \end{itemize}

    \item \textbf{Feature Engineering:}
    \begin{itemize}
        \item Creating new features from our original proposed set that correlate better with our hypothesis. These will help us better map variables that contribute to oil prices.
        \begin{itemize}
            \item Feature to benchmark tensions in the Middle East as an example.
            \item Sentiment analysis using Natural Language Processing (NLP) on news articles related to OPEC and Middle East geopolitical events.
        \end{itemize}
    \end{itemize}

    \item \textbf{Feature Selection:}
    \begin{itemize}
        \item Selecting which features we want to include from our original set.
    \end{itemize}

    \item \textbf{Model Selection:}
    \begin{itemize}
        \item \textit{Time Series Models for Benchmarking:}
        \begin{itemize}
            \item ARIMA (AutoRegressive Integrated Moving Average).
            \item SARIMA (Seasonal ARIMA).
        \end{itemize}
        \item \textit{Machine Learning Models:}
        \begin{itemize}
            \item Temporal Fusion Transformers (Multi-variate).
            \item PatchTST (Autoregressive).
        \end{itemize}
        \item \textit{Hybrid Models:}
        \begin{itemize}
            \item Potential Ensembling.
        \end{itemize}
    \end{itemize}

    \item \textbf{Evaluation Metrics:}
    \begin{itemize}
        \item Mean Absolute Error (MAE).
        \item Root Mean Squared Error (RMSE).
        \item Mean Absolute Percentage Error (MAPE).
        \item Symmetric Mean Absolute Percentage Error (SMAPE).
        \item Weighted MAPE and SMAPE (WMAPE).
        \item Time and Space Complexity.
    \end{itemize}

    \item \textbf{Model Interpretation:}
    \begin{itemize}
        \item Feature Importances.
        \item Attention Weight Study.
        \item Training Plots on TensorBoard.
    \end{itemize}

    \item \textbf{Model Deployment:}
    \begin{itemize}
        \item Rolling Predictions (Predicting off Predictions).
        \item Drift Detection.
        \item Twitter Integration for Prediction Tweets.
    \end{itemize}
\end{enumerate}

\subsection{Data Sources:}

\begin{itemize}
    \item \textbf{Oil Spot Prices:} U.S. Energy Information Administration (EIA)
    
    \item \textbf{Asset Classes:}
    \begin{itemize}
        \item S\&P 500 Index Data.
        \item Gold Prices.
        \item Metal Commodity Prices.
    \end{itemize}
    
    \item \textbf{Macroeconomic Indicators:}
    \begin{itemize}
        \item Interest Rates from Federal Reserve Economic Data (FRED).
        \item EV Sales Statistics from International Energy Agency (IEA).
        \item Carbon Pricing Data from World Bank.
    \end{itemize}
    
    \item \textbf{Volatility Index:} VIX data from CBOE.
    
    \item \textbf{Sentiment Data:} News articles and press releases related to OPEC and Middle East events.
\end{itemize}
