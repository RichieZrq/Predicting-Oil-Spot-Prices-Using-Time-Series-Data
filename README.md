# Predicting-Oil-Spot-Prices-Using-Time-Series-Data

By Richie Zhang, Rohan Sanghrajka, and Uday Sapra

## **Project Overview**  
Oil prices are highly volatile, driven by complex, interdependent factors like macroeconomic shifts, market sentiment, and geopolitical events. Traditional forecasting methods fail to capture this complexity, leading to suboptimal decisions and increased risks for industries, investors, and policymakers. 

Our research aims to predict **crude oil spot prices** using advanced transformer-based models such as **PatchTST** and **Temporal Fusion Transformer (TFT)**, integrating time series analysis, economic indicators, and sentiment data to improve oil price predictions.  By utilizing external data sources and optimizing hyperparameters, we address the limitations of traditional forecasting methods.

---

## **Objectives**  
- Develop models to predict oil prices across short-term (16 steps), medium-term (48 steps), and long-term (96 steps) horizons.  
- Integrate historical prices, economic variables, and sentiment data to enhance model predictions.

---

## **Dataset**  

We extracted and utilized the data specified below for modeling. The data **ranges from 1/4/2021 to 10/12/2024**.
### **Historical Crude Oil Data**: 
Historical spot
prices provide
essential data for
identifying
trends and
forecasting

### **Economic Indicators**:

  - **S&P 500**: Reflects overall
economic health
and investor
sentiment.
  - **Interest Rates**: Influence on
economic
growth and
capital
investments
  - **VIX/OVX**: Indicators of
market volatility
and
expectations of
oil price
fluctuations.
  - **USO**: Tracks daily
WTI crude oil
prices and
market
sentiment.
  - **DXY**: Strength of
USD inversely
affects global
oil pricing.

### **Sentiment Data**
We generated a list of 20 news sources to encapsulate a diverse range of oil-related sentiments across different perspectives. Out of the 20 sources, we used Selenium to web-scrape all oil-related headlines. Sentiment scores are generated from a [pre-trained BERT model](https://huggingface.co/cardiffnlp/twitter-roberta-base-sentiment-latest?text=Covid+cases+are+increasing+fast%21) trained on X data for sentiment analysis.

**List of 20 Initially Considered News Sources**:

- Reuters - www.reuters.com
- Bloomberg - www.bloomberg.com
- **Financial Times - www.ft.com**
- Wall Street Journal - www.wsj.com
- Al Jazeera - www.aljazeera.comE
- **CNBC - www.cnbc.com**
- **OilPrice.com - www.oilprice.com**
- Platts - www.spglobal.com/platts
- **Middle East Economic Survey (MEES) - www.mees.com**
- **Arab News - www.arabnews.com**
- Gulf News - www.gulfnews.com
- The National - www.thenationalnews.com
- Asharq Al-Awsat - english.aawsat.com
- Rigzone - www.rigzone.com
- Petroleum Economist - www.petroleum-economist.com
- **Energy Intelligence - www.energyintel.com**
- International Energy Agency (IEA) - www.iea.org
- **OPEC - www.opec.org**
- Middle East Monitor - www.middleeastmonitor.com
- Brookings Institution - www.brookings.edu

*Bolded sources are the final sources used for modeling*

---

## **Models**  
- **PatchTST**: Autoregressive transformer model for univariate time-series forecasting.
- **Temporal Fusion Transformer (TFT)**: Multivariate model incorporating exogenous variables.  
- **Benchmarks**: ARIMA and SARIMAX models.

---

## **Usage**  
- **Benchmarking** contains notebooks for benchmarking using ARIMA and SARIMAX
- **Data** containing all final features used to train models
- **Modeling** contains notebooks for modeling using both PatchTST and TFT
- **Sentiment Analysis** contains code for sentiment analysis experimentation, code + raw data for scraping, code + raw data for outputting sentiment scores, and code for analysis of sentiment scores

---

## **Results**  

### Model Performance Comparison

| **Horizon**   | **Model**     | **SMAPE (%)** | **MAE (USD)** |
|---------------|----------------|----------------|----------------|
| **16 Steps**  | ARIMA          | 8.99           | 6.90           |
|               | SARIMAX        | 6.82           | 5.30           |
|               | **PatchTST**   | **3.15**       | **2.47**       |
|               | TFT            | 3.56           | 2.80           |
| **48 Steps**  | ARIMA          | 9.72           | 7.48           |
|               | SARIMAX        | 6.722          | 5.26           |
|               | **PatchTST**   | **4.86**       | **3.84**       |
|               | TFT            | 7.36           | 6.96           |
| **96 Steps**  | ARIMA          | 10.45          | 8.07           |
|               | **SARIMAX**    | **6.4**        | **5.23**       |
|               | PatchTST       | 6.65           | 5.24           |
|               | TFT            | 10.37          | 8.55           |

### PatchTST Prediction Across the Last Test Set Window 
<img src="https://github.com/user-attachments/assets/3af837dd-82ee-440f-a49b-d84fa16095de" alt="image" width="70%" />

### PatchTST Prediction Across the Last Test Set Window
<img src="https://github.com/user-attachments/assets/31c2ea7a-d8ef-4f33-a4a1-376a9eeb868c" alt="image" width="70%" />

---

## **Conclusions**  
Even with high-model complexity and feature sets, our multivariate transformer could not outperform autoregressive models. This could be due to poor sentiment scores or an overly noisy and complex feature set. Therefore, the next steps would be to reduce the feature set through improved feature engineering. The TFT also showed a very high degree of variance. Every model, even with similar hyperparameters, converged to different solutions. The problem persisted even when we reduced the model complexity and feature set. This could also indicate a lack of data, which was 800 samples for training. Hence, in the future, we also want to expand on data size by including a longer time period of data. We were also impressed by PatchTST's ability to outperform SARIMAX with a reduced feature set. While SARIMAX used exogenous variables of lags and seasonality, PatchTST was solely autoregressive. Hence, we plan to further analyze model performance to understand what contributes to better performance. 

Another major area to improve on is sentiment analysis. We could only scrape 6 out of the 20 sources we selected due to scraping difficulties and time limitations. This could potentially cause selection bias in news headlines. Another consideration is that when concatenating all headlines from the same day, the overall sentiment of each headline is mixed with others, potentially confusing the model with more noise. Instead of generating scores for a long text with all headlines concatenated together, the next step could be to generate sentiment scores for each headline, and then aggregate all headlines for a day by finding the average sentiment score.

In sum, we conclude that oil is best predicted autoregressively with low model complexity. Economic factors and sentiments add more noise to the modeling process, leading to models with extremely high variance. 
