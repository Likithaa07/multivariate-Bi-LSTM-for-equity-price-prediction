# Multivariate Bi-LSTM for Equity Price Prediction

This project investigates deep-learning time-series modelling in equity/stock markets using a **multivariate Bidirectional LSTM (Bi-LSTM)** framework. The goal is to forecast future stock prices by leveraging multiple correlated features (not just closing price) and to compare performance across architectures.

---

## 🧠 Project Overview  
Financial markets are characterised by sequential, volatile, and often nonlinear behaviour. Traditional univariate models (using only closing price) may miss rich dependencies.  
In this work, we build an advanced sequence-model that uses multivariate inputs (e.g., OHLCV + technical indicators) and a bidirectional architecture (learning forward + backward time dependencies) to improve forecasting accuracy.

---

## 🧩 Objectives  
- Develop a **Bidirectional Multivariate LSTM** model for short-term equity price forecasting.  
- Compare univariate vs multivariate input configurations.  
- Engineer technical indicators (moving averages, RSI, etc.) as model inputs.  
- Evaluate model performance using key metrics: MSE, RMSE, MAE, R².  
- Visualise the results: loss curves, actual vs predicted prices, future forecasts.

---

## ⚙️ Dataset & Feature Engineering  
The dataset consists of historical hourly (or suitably aggregated) stock prices for select equities (e.g., companies from key sectors).  
Main features:  
| Feature | Description |
|--------|-------------|
| `Open`, `High`, `Low`, `Close` | Standard OHLC price data |
| `Volume` | Trading volume |
| Technical indicators (e.g., `SMA`, `EMA`, `RSI`, `ROC`, etc.) | Derived metrics capturing momentum, trend and relative strength |

**Preprocessing steps include:**  
- Handling missing values / cleaning  
- Feature scaling (e.g., `MinMaxScaler`)  
- Generating time-window sequences (e.g., 60 time-steps)  
- Splitting into train/validation/test sets  

---

## 🧮 Model Architecture & Training  
### 🔹 Bidirectional Multivariate LSTM  
- Input shape: (seq_length × num_features)  
- Layers: Two stacked Bidirectional LSTM (64 units each)  
- Regularisation: Dropout (e.g., 0.2)  
- Output: Dense(32) → Dense(1) for regression (next step price)  
- Loss: Mean Squared Error (MSE)  
- Optimiser: Adam  
- Early-stopping on validation loss + restore best weights  

### 🔹 Baseline (Univariate) Model  
- Input: single feature (e.g., closing price)  
- Similar architecture but with standard LSTM (non-bidirectional)  
- Same training regime for fair comparison  

---

## 📊 Results Summary  
| Model | Input Type | RMSE | MAE | R² |
|-------|------------|------|------|------|
| Baseline Univariate LSTM | Single feature | ~18-20 | ~16-18 | ~0.78 |
| Multivariate Bi-LSTM | Multiple features | ~9-10 | ~7-8 | ~0.95 |

✅ The multivariate Bi-LSTM shows significantly improved performance, demonstrating the value in expanding input feature space and using bidirectional temporal modelling.

---

## 📈 Visualisations  
- **Validation Loss Curves**: Show convergence behaviour and compare architectures.  
- **Actual vs Predicted Price Plots**: Show how closely predictions track live price movements.  
- **Future Forecasting (Next N Steps)**: Projecting short-term future prices based on recent window input.
  
## 🏁 Conclusion

The **Bidirectional LSTM (Bi-LSTM)** model clearly outperformed the traditional LSTM in forecasting equity prices.  
By learning from data in both **forward and backward directions**, Bi-LSTM was able to capture a deeper understanding of market behavior and temporal dependencies that a unidirectional model often misses.

Through the inclusion of **multivariate inputs** — such as OHLC data, trading volume, and technical indicators like EMA, RSI, and SMA — the model achieved:
- Significantly **lower RMSE and MAE**,  
- A **higher R² score**, and  
- **Smoother, more realistic forecasts** even during volatile market conditions.

While the standard LSTM could identify general trends, it often lagged at turning points and sharp fluctuations. The Bi-LSTM’s bidirectional architecture enabled it to recognize context from both the past and the near future within each time window, resulting in more accurate and stable predictions.

Overall, this study demonstrates that combining **rich feature engineering** with **bidirectional temporal learning** substantially enhances predictive performance in financial time-series forecasting, making the Bi-LSTM model a superior choice for short-term equity price prediction.

