# TSLA Time Series Anomaly Detection with LSTM Autoencoder

This project implements an unsupervised anomaly detection pipeline using an **LSTM Autoencoder** to identify abnormal movements in Tesla’s stock price time series based on **reconstruction error** between 2015 and 2025. 
The system highlights market periods where price behavior deviates from learned historical patterns.

<img src="./images/stock_prices.png" width="" height="500">

---

## Overview
Financial time series frequently exhibit irregular behavior driven by macroeconomic events, firm-specific announcements, volatility spikes, or systemic shocks. Detecting these anomalies is valuable for risk management, early warning systems, and investment decision support. 

This project focuses on detecting abnormal price patterns in historical Tesla (TSLA) stock data without labeled anomalies. The solution uses an LSTM Autoencoder to learn baseline temporal dynamics and flag deviations via reconstruction error. The work demonstrates how data-driven modeling can surface market regime shifts and event-driven volatility.

---

## Skills Demonstrated
✔ **Time Series Modeling**

✔ Deep Learning (**LSTM Autoencoders**)

✔ **Machine Learning** Model Training & Evaluation

✔ Real-world Data Retrieval & API Usage (**Yahoo Finance**)

✔ Anomaly Detection & Reconstruction Error Thresholding

✔ Engineered preprocessing pipeline including scaling, windowing, and reconstruction thresholding

---

## Data
Historical daily price data for Tesla (TSLA) was retrieved via Yahoo Finance. The dataset includes open, high, low, close, adjusted close, and volume fields. The *closing price* was selected as the primary target series for anomaly detection due to its common use in financial modeling and price-based analysis.

Data pre-processing steps included:
- Scaling using *Min-Max normalization*
- Sliding window segmentation for sequence modeling
- Train-test splitting without label supervision
- Reconstruction error computation for anomaly scoring

This setup simulates realistic financial data workflows and preserves temporal ordering.

---

## Key Technical Decisions

**Unsupervised anomaly detection (LSTM Autoencoder) vs. supervised classification**: Supervised classification requires labeled anomalies, which are scarce and subjective in financial contexts.  Unsupervised learning enables detection of rare or previously unseen patterns without manual annotation.

**LSTM Autoencoder vs. classical statistical models (e.g., ARIMA)**: Autoregressive Integrated Moving Average (ARIMA) handles linear and stationary signals but struggles with nonlinear temporal dependencies.  LSTM Autoencoders capture nonlinear patterns and multi-step dependencies, improving anomaly sensitivity in financial series.

**Reconstruction-based detection vs. prediction-based detection**: Forecasting future values and measuring prediction error can infer anomalies. Reconstruction avoids forecasting noise and isolates structural deviations by measuring mismatch with known inputs.

**Sliding window sequence formation vs. single-point modeling**: Single-point modeling ignores temporal context. Window-based encoding captures richer micro-regime dynamics and enhances generalization.

---

## Key Insights & Impacts
- Reconstruction-based anomaly detection generalizes across industries including manufacturing (sensor faults), cybersecurity (intrusions), and healthcare (patient monitoring).
- From an analytical perspective, anomaly detection enhances risk surveillance, supports post-event attribution, and informs decision-making in time-sensitive environments.

---

## Model Evaluation

We evaluate the model by comparing the reconstruction errors of the training data and test data, with the latter showing a significantly higher **Mean Absolute Error (MAE)** due to the presence of anomalies. 

<img src="./images/MAE_train.png" width="" height="400">

<img src="./images/MAE_test.png" width="" height="400">

Additionally, the **training loss** (blue curve) remains low and steady showing the model is learning the training data well. The **validation loss curve** (orange curve) is bumpy and shows great oscillation, as the unusual price pattern (anomalies) are hard to reconstruct resulting to large reconstruction error.

<img src="./images/loss.png" width="" height="400">

---

## Results Summary
The anomaly detection pipeline identified periods where reconstruction error spiked, indicating deviations from learned baseline behavior. These anomalies aligned with major market events as follows.

- **Nov 2024**: Share prices surged on optimism of Donald Trump's election victory.

- **Dec 2024**: After TSLA shares reached its all-time high on 17th Decemeber 2024, the shares plunged, due to weak market sentiment on trade tariffs by the US as well as TESLA's declining sales data.

- **Mar 2025**: Shares extended further losses, amid market concerns over Elon Musk’s involvement with the Trump administration as well as the falling new vehicle sales.

- **Sep 2025**: Elon Musk buying back $1bn in Tesla Shares, a signal of confidence of the company

- **Oct-Dec 2025**: TSLA shares saw a strong recovery, thanks to strategic narrative shifts - positioning as an artificial intelligence (AI) and autonomy leader, not just an electric vehicle (EV) maker.

<img src="./images/stock_prices.png" width="" height="500">

---

## Author
Carmen Wong
