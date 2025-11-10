# 📉 LSTM vs Bi-LSTM Stock Price Prediction

This notebook compares the performance of **LSTM** and **Bidirectional LSTM** architectures for stock price forecasting using historical hourly data.  
It explores how model structure impacts accuracy when predicting short-term price movements.

---

## 🧠 Project Overview
The **LSTM** model learns from sequential dependencies in stock data, while the **Bi-LSTM** captures information from both past and future directions.  
Both were trained to predict future closing prices, using technical indicators as features.

---

## 🧩 Objectives
- Compare **LSTM** and **Bi-LSTM** for sequence prediction  
- Quantify differences in model accuracy using standard metrics  
- Visualize validation losses and predicted trends  

---

## ⚙️ Dataset
Hourly stock price data for Indian companies (ICICI Bank, Wipro, NTPC, Ambuja Cement).  
Features used:
- Open, High, Low, Close, Volume  
- EMA, RSI, SMA, ROC, Momentum  

Preprocessing steps:
- Feature scaling with `MinMaxScaler`  
- Sequence creation (60-timestep windows)  
- Train/test split (80/20)

---

## 🧮 Model Architectures
### 🔹 LSTM
- Two LSTM layers (64 units each)  
- Dropout 0.2  
- Dense(32, relu) → Dense(1)

### 🔹 Bi-LSTM
- Two Bidirectional LSTM layers (64 units each)  
- Dropout 0.2  
- Dense(32, relu) → Dense(1)

---

## 📊 Results
| Model | RMSE | MAE | R² |
|:--|:--:|:--:|:--:|
| LSTM | 20.85 | 18.25 | 0.78 |
| **Bi-LSTM** | **9.81** | **7.59** | **0.95** |

✅ The **Bi-LSTM** model outperformed the standard LSTM, demonstrating superior trend learning and lower prediction error.

---

## 📈 Visualization
- Validation loss curves  
- Actual vs Predicted price plots  
- 10-step future forecast  

---

## 🧠 Key Insights
- Bidirectional context captures stronger temporal dependencies  
- Multiple indicators improve forecast stability  
- Early stopping prevents overfitting and keeps loss low  

---

## 💻 Tech Stack
TensorFlow / Keras | Scikit-learn | Pandas | NumPy | Matplotlib | Google Colab  

---

## 🧑‍💻 Author
**Likitha Vankadoth**  
🔗 [LinkedIn](https://www.linkedin.com/in/likithaa07/)  
📘 [Notebook Link](https://github.com/Likithaa07/-Stock-Market-Analysis-Prediction-using-LSTM/blob/main/LSTM_vs_Bi_LSTM_%E2%80%93_Stock_Price_Prediction.ipynb)
