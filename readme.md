# Li-Ion Battery RUL & SOH Prediction (LSTM + TCN)

An enhanced implementation for **Lithium-Ion Battery Remaining Useful Life (RUL)**, **State of Health (SOH)**, and **Raw Capacity** prediction using deep learning. This repository extends the original LSTM-based implementation by introducing **Temporal Convolutional Networks (TCN)** as an alternative sequence modeling architecture, enabling direct benchmarking between the two approaches.

> **Original Repository:** https://github.com/MoHoss007/Li-Ion-Battery-RUL-SOH-Prediction  
> **Enhanced Repository:** https://github.com/aahad699/Li-Ion-Battery-RUL-SOH-Prediction-main  
> **Author of Enhancements:** Abdul Ahad

---

## Overview

Accurate estimation of battery health is essential for electric vehicles, renewable energy storage, and battery management systems (BMS). This repository provides deep learning models for predicting:

- **Raw Battery Capacity**
- **State of Health (SOH)**
- **Remaining Useful Life (RUL)**

The original implementation relied exclusively on Long Short-Term Memory (LSTM) networks. This enhanced version extends the framework by incorporating **Temporal Convolutional Networks (TCN)** while preserving the same preprocessing pipeline and evaluation methodology.

---

## Improvements over the Original Repository

This repository introduces several enhancements over the original implementation:

- Added **Temporal Convolutional Network (TCN)** architecture.
- Maintained support for the original **LSTM** implementation.
- Added configurable model selection through the `MODEL_ARCHITECTURE` variable (`LSTM` or `TCN`).
- Trained and provided models for:
  - Raw Capacity Prediction
  - State of Health (SOH) Prediction
  - Remaining Useful Life (RUL) Prediction
- Enabled fair comparison between LSTM and TCN using:
  - identical preprocessing
  - identical train/validation/test split
  - identical training configuration
  - identical evaluation metrics
- Improved project structure for easier experimentation with multiple sequence-learning architectures.

---

## Dataset

The repository uses the **NASA Lithium-Ion Battery Aging Dataset**.

The dataset contains multiple charge/discharge cycles recorded from commercial lithium-ion batteries until end-of-life, making it suitable for:

- Capacity estimation
- SOH prediction
- RUL prediction

---

## Model Architectures

### LSTM

Long Short-Term Memory (LSTM) networks are designed to model long-term temporal dependencies and have been widely adopted for battery degradation prediction.

### TCN

Temporal Convolutional Networks (TCN) employ causal and dilated convolutions to capture long-range temporal relationships while allowing parallel computation.

This repository enables direct comparison between both architectures under identical experimental settings.

---

## Training Configuration

Both LSTM and TCN models were trained using:

- Same preprocessing pipeline
- Same train/validation/test split
- Same input sequences
- Same optimizer
- Same training epochs
- Same evaluation metrics

This ensures a fair comparison between both architectures.

---

## Evaluation Metrics

Performance is evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- Coefficient of Determination (R²)

Lower MAE/RMSE values indicate better prediction accuracy, while higher R² values indicate better model fit.

---

# Experimental Results

## Raw Capacity Prediction

| Model | MAE | RMSE | R² |
|------|------:|------:|------:|
| LSTM | **0.08923** | **0.11244** | **0.64541** |
| TCN | 0.12976 | 0.15483 | 0.32764 |

---

## State of Health (SOH)

| Model | MAE | RMSE | R² |
|------|------:|------:|------:|
| LSTM | **0.07742** | **0.09527** | **0.19310** |
| TCN | 0.08973 | 0.10452 | 0.02873 |

---

## Remaining Useful Life (RUL)

| Model | MAE | RMSE | R² |
|------|------:|------:|------:|
| LSTM | **0.07648** | **0.09823** | **0.85719** |
| TCN | 0.12171 | 0.14691 | 0.68060 |

---

## Discussion

The primary objective of this work was to extend the original repository by incorporating **Temporal Convolutional Networks (TCN)** and providing a unified framework for evaluating multiple sequence modeling architectures.

Under the current experimental configuration, the **LSTM architecture consistently achieved lower prediction errors (MAE and RMSE) and higher R² values across all three prediction tasks (Raw Capacity, SOH, and RUL)**.

These findings indicate that, for the current dataset and training configuration, the LSTM implementation produced more accurate predictions than the implemented TCN model. Nevertheless, the addition of TCN significantly broadens the repository by enabling comparative experimentation and providing a foundation for future architectural improvements and hyperparameter optimization.

---

## Repository Structure

```
.
├── Models/
│   ├── Raw_Capacity_LSTM.keras
│   ├── Raw_Capacity_TCN.keras
│   ├── SOH_LSTM.keras
│   ├── SOH_TCN.keras
│   ├── RUL_LSTM.keras
│   └── RUL_TCN.keras
│
├── Notebook.ipynb
├── README.md
└── requirements.txt
```

---

## How to Run

1. Clone the repository.

```bash
git clone https://github.com/aahad699/Li-Ion-Battery-RUL-SOH-Prediction-main.git
```

2. Install dependencies.

```bash
pip install -r requirements.txt
```

3. Open the notebook.

4. Select the desired architecture:

```python
MODEL_ARCHITECTURE = "LSTM"
```

or

```python
MODEL_ARCHITECTURE = "TCN"
```

5. Run all notebook cells.

---

## Acknowledgements

This work is based on the original repository:

**MoHoss007**
https://github.com/MoHoss007/Li-Ion-Battery-RUL-SOH-Prediction

The original implementation served as the foundation for this enhanced version.

---

## Citation

If you use this repository in your research, please consider citing both the original work and this enhanced implementation.

---

## License

Please refer to the original repository's license before redistribution or commercial use.
