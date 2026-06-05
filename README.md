# 🛡️ Network Attack Detection using Synthetic Data Generation

![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat&logo=python&logoColor=white)
![ML](https://img.shields.io/badge/ML-XGBoost%20%7C%20LightGBM%20%7C%20RF%20%7C%20SVM-orange?style=flat)
![GAN](https://img.shields.io/badge/GAN-CTGAN-blueviolet?style=flat)
![Streamlit](https://img.shields.io/badge/App-Streamlit-FF4B4B?style=flat&logo=streamlit&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=flat)

> An advanced anomaly detection system for cybersecurity that leverages **CTGAN (Conditional Tabular GAN)** to generate realistic synthetic attack logs and trains multiple machine learning models for real-time network intrusion detection.

---

## 📝 Description

Network intrusion detection is a critical challenge in modern cybersecurity — real-world attack data is often scarce, imbalanced, or sensitive to share. This project tackles that problem head-on by using **generative AI (CTGAN)** to synthesize high-fidelity attack logs that preserve the statistical distributions and feature correlations of real network traffic.

The synthesized data is then used to train and benchmark four anomaly detection models — **Random Forest, XGBoost, LightGBM, and SVM** — evaluated against real-world security metrics like false positive rate and detection latency. The entire pipeline is wrapped in a **Streamlit web application** that enables real-time traffic analysis, attack classification, and confidence scoring — making it usable by security teams without deep ML expertise.

This project covers the full ML lifecycle: exploratory data analysis → synthetic data generation → model training → evaluation → deployment-ready web interface.

---

## 🖥️ App Preview
![Streamlit App](https://github.com/igpriyanshunegi/network-attack-detection-using-ctgan/blob/main/App%20Screenshot.png)

## 🖥️ Live App
💡[Deployed Streamlit App Link](https://network-attack-detection-system.onrender.com/)

---

## 📁 Project Structure

```
📁 Network-Attack-Detection/
│
├── 📓 Notebooks/
│   ├── 1_EDA.ipynb                    # Exploratory Data Analysis
│   ├── 2_CTGAN_Training.ipynb         # Synthetic Attack Log Generation
│   ├── 3_Model_Training.ipynb         # Anomaly Detection Model Training
│   └── 4_Visualization.ipynb          # Attack Pattern Analysis & Plots
│
├── 📁 Data/
│   ├── Train_data.csv                 # Training dataset
│   └── Test_data.csv                  # Testing dataset
│
├── 📁 models/
│   ├── best_cybersecurity_model.pkl   # Best performing detection model
│   ├── cybersecurity_ctgan_model.pkl  # Trained CTGAN generator
│   ├── cybersecurity_scaler.pkl       # Feature scaler
│   ├── lightgbm_cybersecurity.pkl     # LightGBM model
│   ├── preprocessing_objects.pkl      # Preprocessing pipeline
│   ├── random_forest_cybersecurity.pkl
│   ├── svm_cybersecurity.pkl
│   ├── training_metadata.pkl
│   └── xgboost_cybersecurity.pkl
│
├── 📁 results/
│   ├── model_performance_comparison.csv
│   └── synthetic_cybersecurity_data.csv
│
├── app.py                             # Streamlit web application
├── GNCIPL Project ppt.pptx           # Project presentation
├── GNCIPL Project report file.pdf    # Project report
├── requirements.txt
└── README.md
```

---

## ✨ Features

- **Synthetic Data Generation** — CTGAN produces realistic network attack logs, solving the data scarcity and class imbalance problem
- **Multi-Model Benchmarking** — four classifiers trained and compared on security-specific metrics
- **End-to-End Pipeline** — raw data → EDA → synthesis → training → deployment, all in structured notebooks
- **Real-Time Detection App** — Streamlit interface for live traffic scoring with no ML background required
- **Interpretable Results** — confidence scores and attack type classification designed for security team readability

---

## 📊 Dataset Description

The project uses a **Network Attack Dataset** containing real network traffic records with the following feature groups:

| Feature Group | Examples |
|---|---|
| Network Traffic | Packet size, flow duration, bytes per second |
| Protocol Information | TCP/UDP/ICMP flags, port numbers |
| Attack Type & Pattern | Attack category, sub-type labels |
| Temporal Information | Timestamps, inter-arrival times |
| Attack Severity | Severity level, threat score |

The dataset is split into `Train_data.csv` for model training and `Test_data.csv` for final evaluation.

---

## 🤖 Models Implemented

### 1. CTGAN — Synthetic Data Generation

CTGAN (Conditional Tabular GAN) is used to generate synthetic attack logs that:
- Faithfully reproduce real attack distributions
- Preserve feature correlations across categorical and continuous variables
- Augment minority attack classes to address class imbalance

### 2. Anomaly Detection Models

| Model | Strengths in Security Context |
|---|---|
| **Random Forest** | Robust to noise, strong baseline, interpretable feature importance |
| **XGBoost** | High accuracy on imbalanced data, fast inference |
| **LightGBM** | Efficient on large traffic logs, excellent with categorical features |
| **SVM** | Effective for high-dimensional feature spaces, strong boundary detection |

---

## 📈 Performance Metrics

Models are evaluated using security-context metrics:

| Metric | Description |
|---|---|
| Detection Accuracy | Overall correct classification rate |
| False Positive Rate | Legitimate traffic incorrectly flagged as attacks |
| False Negative Rate | Attacks that slipped through undetected (critical to minimize) |
| Detection Latency | Time taken to classify a single traffic sample |
| Model Confidence Score | Probability output per prediction |

Full comparison results are saved in `results/model_performance_comparison.csv`.

---

## 🗂️ Notebook Workflow

Run the notebooks **in order** for the complete pipeline:

| Step | Notebook | Description |
|---|---|---|
| 1️⃣ | `1_EDA.ipynb` | Understand data distributions, attack class balance, feature correlations |
| 2️⃣ | `2_CTGAN_Training.ipynb` | Train CTGAN and generate synthetic attack logs |
| 3️⃣ | `3_Model_Training.ipynb` | Train and evaluate all four detection models |
| 4️⃣ | `4_Visualization.ipynb` | Attack pattern analysis and visual summaries |

---

## 🌐 Web Application

The Streamlit app (`app.py`) provides a real-time detection interface for security teams:

- 📡 **Real-Time Traffic Analysis** — submit network traffic features and get instant predictions
- 🎯 **Attack Probability Scoring** — probability score output for each attack class
- 🏷️ **Attack Type Classification** — identifies the specific type of intrusion
- 📊 **Confidence Metrics** — model certainty displayed per prediction
- 📉 **Interactive Visualizations** — Plotly-based charts for traffic pattern exploration

---

## ⚙️ Setup & Installation

### Prerequisites

- Python 3.8+
- pip

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/igpriyanshunegi/network-attack-detection-using-ctgan.git
cd network-attack-detection

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run notebooks in sequence (1 → 4)
jupyter notebook

# 4. Launch the detection web app
streamlit run app.py
```

### Key Dependencies

```
pandas
numpy
scikit-learn
sdv
streamlit
plotly
xgboost
lightgbm
```

---

## 🔐 Security Considerations

- **Model Interpretability** — feature importance scores help analysts understand why a traffic sample was flagged
- **False Positive/Negative Tuning** — adjustable thresholds to balance detection sensitivity vs. alert noise
- **Attack Pattern Evolution** — modular retraining pipeline to adapt to new and emerging attack vectors
- **Audit Trail** — saved models and metadata ensure full reproducibility for security audits

---

## 🚀 Deployment Guidelines

1. **Regular Model Updates** — retrain on new traffic data quarterly or after a significant attack event
2. **Performance Monitoring** — track detection accuracy and false positive rate continuously in production
3. **Alert Threshold Configuration** — tune confidence score thresholds to match your team's risk tolerance
4. **SIEM Integration** — connect the app or model API to your existing Security Information and Event Management system

---

## 👥 Contributors

| Name | Role |
|---|---|
| **Priyanshu** | Project Lead — Data Analysis, Model Training, App Development |

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

<p align="center">Built with 🔐 to make networks safer</p>
