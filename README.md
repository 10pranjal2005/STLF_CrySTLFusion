# ⚡ CrySTLFusion
## Grid-Aware, Probabilistic Five-Minute Short-Term Load Forecasting for the Indian Power Grid

---

## 📘 Project Overview

**CrySTLFusion** is a high-resolution **Short-Term Load Forecasting (STLF)** framework designed for **modern, renewable-rich, and spatially interconnected power systems**, with a specific focus on **India’s five-minute scheduling regime**.

The system delivers **rolling 5-minute ahead forecasts** by fusing:
- Temporal deep learning
- Spatial graph-based grid modeling
- Attention-driven interpretability
- Probabilistic uncertainty estimation

CrySTLFusion is built to support **real-time dispatch, reserve planning, congestion management, and renewable integration** in operational grid environments such as **DISCOMs, SLDCs, and RLDCs**.

---

## ❓ Why CrySTLFusion?

Modern power grids face unprecedented challenges:
- High solar and wind penetration
- Weather-driven demand volatility
- Festival and socio-cultural load spikes
- Inter-regional power flow coupling
- Transition from 15-minute to **5-minute scheduling**

Traditional forecasting models:
- Assume isolated regions
- Ignore grid topology
- Produce deterministic forecasts
- Fail during extreme events

CrySTLFusion addresses these gaps by making forecasting:
- **Grid-aware**
- **Uncertainty-aware**
- **Operationally explainable**

---

## 🧠 Core Concept

Instead of predicting a single load value, CrySTLFusion:
- Learns **how demand propagates across regions**
- Identifies **which time steps matter most**
- Quantifies **how confident the forecast is**

This transforms forecasting from a numeric task into a **decision-support system**.

---

## 🏗️ System Architecture

Multi-Source Inputs
(Load, Weather, Market, Time, Events)
↓
Data Cleaning & Quality Assurance
↓
Feature Engineering & Encoding
↓
CNN (Short-Term Local Patterns)
↓
LSTM (Long-Term Dependencies)
↓
Attention (Critical Time Focus)
↓
Graph Neural Network (Grid Coupling)
↓
Probabilistic Forecast Head (μ, σ)
↓
ADMS / SCADA-Ready Outputs

---

## 🧩 Model Components

### 1️⃣ Convolutional Neural Network (CNN)
- Captures short-term load ramps
- Detects sudden spikes and micro-patterns
- Improves responsiveness at 5-minute scale

### 2️⃣ Long Short-Term Memory (LSTM)
- Learns daily, weekly, and seasonal trends
- Stabilizes short-term forecasts
- Handles long-range temporal dependencies

### 3️⃣ Attention Mechanism
- Assigns importance to historical time steps
- Highlights heatwaves, festivals, ramping periods
- Improves peak tracking and interpretability

### 4️⃣ Graph Neural Network (GNN)
- Represents electrical connectivity between regions
- Models demand propagation across utilities
- Mirrors real transmission-level power flow

### 5️⃣ Probabilistic Forecasting Head
- Outputs mean (μ) and variance (σ)
- Provides confidence intervals
- Enables risk-aware dispatch and reserve planning

---

## 📊 Dataset Description

### 🔹 Source
- ERLDC archives
- SLDC dashboards (Eastern Region)

### 🔹 Regions Covered
- WBSEB (West Bengal)
- BSEB (Bihar)
- JSEB (Jharkhand)
- Sikkim
- DVC (Industrial belt)

### 🔹 Time Span
- January 2019 – December 2024

### 🔹 Resolution
- Original: 15 minutes  
- Final: **5 minutes**

### 🔹 Record Count
- Raw: ~175,000
- Final: ~105,100

---

## 🧾 Features Used

### Load & Grid
- Total demand (MW)
- Regional demand
- Grid frequency

### Weather (IMD)
- Temperature
- Humidity
- Rainfall
- Solar radiation

### Market Signals
- IEX / PXIL clearing prices
- Market trend indicators

### Temporal
- Hour-of-day (sin/cos encoding)
- Day-of-week
- Seasonal indicators

### Socio-Cultural
- Festivals
- Public events

---

## 🧹 Data Preprocessing

- Timestamp normalization (IST)
- Duplicate removal
- Missing values (<3%) handled using:
  - Linear interpolation
  - Seasonal median imputation
- Outlier removal via rolling ±3σ Z-score
- Resampling from 15-min → 5-min intervals

---

## ⚙️ Training Configuration

| Parameter | Value |
|--------|------|
| Optimizer | Adam |
| Loss | MSE + Gaussian NLL |
| Epochs | ~15 (Early stopping) |
| Batch Size | 64 |
| Train/Test Split | 80/20 (chronological) |
| Regularization | Dropout, BatchNorm |
| LR Scheduling | Enabled |

---

## 📈 Performance Results

| Metric | Value |
|------|------|
| **MAPE** | **1.1% – 1.3%** |
| **RMSE** | ~1376 MW |
| **R²** | > 0.99 |
| Training Time | ~23 minutes |
| Forecast Horizon | Rolling 5-minute |

### Baseline Comparison
CrySTLFusion outperforms:
- ARIMA
- SVR
- Standalone CNN
- Standalone LSTM

---

## 🔍 Interpretability & Explainability

- Attention weights highlight influential time steps
- Feature attribution identifies key drivers
- Spatial graphs explain regional interactions
- Uncertainty bands provide confidence-aware decisions

This makes the model **transparent, auditable, and trustworthy**.

---

## 🚀 Deployment & Operations

- Autoregressive rolling inference
- Secure API-based outputs
- ADMS & SCADA integration
- Drift detection and automated retraining
- Suitable for real-time grid operations

---

## 🧪 Reproducibility

- Fixed random seeds
- Chronological splits
- Versioned preprocessing pipeline
- Deterministic training configuration

---

## 🔮 Future Extensions

- EV charging load modeling
- Rooftop solar forecasting
- Nationwide grid scaling
- Edge inference at SLDCs
- Transformer-based temporal modules

---

## 👤 Author

**Pranjal Kundu**  
SRM Institute of Science and Technology (SRMIST), KTR Chennai  

---

## 📜 License

For academic, research, and hackathon use.  
Commercial deployment requires author permission.

---

⭐ If you find this project useful, please star the repository.
