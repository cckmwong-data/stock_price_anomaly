# TSLA Time Series Anomaly Detection with LSTM Autoencoder

This project implements an unsupervised anomaly detection pipeline using an LSTM Autoencoder to identify abnormal movements in Tesla’s stock price time series based on reconstruction error. 
The system highlights market periods where price behavior deviates from learned historical patterns.

<img src="./images/stock_prices.png" width="" height="500">

---

## Overview
Financial time series frequently exhibit irregular behavior driven by macroeconomic events, firm-specific announcements, volatility spikes, or systemic shocks. Detecting these anomalies is valuable for risk management, early warning systems, and investment decision support. 

This project focuses on detecting abnormal price patterns in historical Tesla (TSLA) stock data without labeled anomalies. The solution uses an LSTM Autoencoder to learn baseline temporal dynamics and flag deviations via reconstruction error. The work demonstrates how data-driven modeling can surface market regime shifts and event-driven volatility.

---

## Skills Demonstrated
- Time Series Modeling
- Deep Learning (LSTM Autoencoders)
- Machine Learning Model Training & Evaluation
- Real-world Data Retrieval & API Usage (Yahoo Finance)
- Anomaly Detection & Reconstruction Error Thresholding
- Engineered preprocessing pipeline including scaling, windowing, and reconstruction thresholding

---

## Key Technical Decisions (with Alternatives and Rationale)

**Unsupervised anomaly detection vs. supervised classification**  
Alternative: Supervised classification requires labeled anomalies, which are scarce and subjective in financial contexts.  
Rationale: Unsupervised learning enables detection of rare or previously unseen patterns without manual annotation.

**LSTM Autoencoder vs. classical statistical models (e.g., ARIMA)**  
Alternative: ARIMA handles linear and stationary signals but struggles with nonlinear temporal dependencies.  
Rationale: LSTM Autoencoders capture nonlinear patterns and multi-step dependencies, improving anomaly sensitivity in financial series.

**Reconstruction-based detection vs. prediction-based detection**  
Alternative: Forecasting future values and measuring prediction error can infer anomalies.  
Rationale: Reconstruction avoids forecasting noise and isolates structural deviations by measuring mismatch with known inputs.

**Sliding window sequence formation vs. single-point modeling**  
Alternative: Single-point modeling ignores temporal context.  
Rationale: Window-based encoding captures richer micro-regime dynamics and enhances generalization.

**Statistical thresholding vs. manual rule-based flagging**  
Alternative: Rule-based detection depends on domain heuristics that do not generalize.  
Rationale: Statistical thresholding adapts to data distributions and allows tunable sensitivity across different time series.

---

## Key Insights & Impacts
- LSTM Autoencoders provide adaptive sequence-level anomaly detection without labeled training data.
- The architecture captures nonlinear dependencies and temporal context, which benefits financial markets where behaviors are regime-driven and rarely stationary.
- Reconstruction-based anomaly detection generalizes across industries including manufacturing (sensor faults), cybersecurity (intrusions), and healthcare (patient monitoring).
- From an analytical perspective, anomaly detection enhances risk surveillance, supports post-event attribution, and informs decision-making in time-sensitive environments.

---

## Business Value & Use Cases
This framework supports several analytics and risk-oriented applications:
- Market event detection and attribution
- Volatility surveillance and alerting
- Risk management and exposure monitoring
- Investment research and market diagnostics
- Data quality assurance for downstream modeling

Applicable across financial institutions, hedge funds, fintech platforms, and internal corporate analytics teams.

---

## Results Summary
The anomaly detection pipeline identified periods where reconstruction error spiked, indicating deviations from learned baseline behavior. These anomalies aligned with major market events including earnings announcements, notable corporate communications, and macroeconomic shocks that shifted volatility regimes. The alignment demonstrates that unsupervised deep learning can surface event-driven anomalies without labeled data, providing both analytical insight and monitoring value.

---

## Visual Outputs (Recommended for Portfolio)
Typical visual components that improve interpretability:
- Time series chart with anomaly overlays
- Reconstruction error curve over time
- Reconstruction loss distribution with threshold
- Zoomed event windows showing anomaly clusters

---

## Author
Carmen Wong
