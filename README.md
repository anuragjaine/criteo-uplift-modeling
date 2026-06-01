# 🎯 Industrial-Scale Uplift Modeling for Ad Spend Optimization

> **Causal inference applied to Criteo's 13.9M user production dataset to identify "persuadable" customers and optimize digital advertising ROI.**

[![Python](https://img.shields.io/badge/Python-3.10-blue.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.1-red.svg)](https://pytorch.org/)
[![EconML](https://img.shields.io/badge/EconML-Microsoft-purple.svg)](https://econml.azurewebsites.net/)
[![CausalML](https://img.shields.io/badge/CausalML-Uber-black.svg)](https://github.com/uber/causalml)
[![Status](https://img.shields.io/badge/Status-In%20Progress-orange.svg)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> ⚠️ **Project Status:** Active development. See Progress Tracker below.

---

## 📌 Project Overview

Standard machine learning predicts **who will convert** — but this targets customers who would have converted *anyway*, wasting ad spend. 

This project applies **Causal Machine Learning** to answer the more valuable question:

> **"Which users convert BECAUSE of the ad?"**

By identifying the **persuadable segment** and detecting **"do-not-disturb"** users (where ads may *reduce* conversion), this system aims to deliver smarter ad budget allocation through rigorous causal inference rather than naive correlational predictions.

---

## 🎯 Business Problem

Digital advertisers waste billions targeting customers who fall into four behavioral categories:

|  | **Convert WITH Ad** | **Don't Convert WITH Ad** |
|---|:---:|:---:|
| **Convert WITHOUT Ad** | ✅ Sure Things *(wasted spend)* | ⚠️ Do-Not-Disturb *(harmful)* |
| **Don't Convert WITHOUT Ad** | 🎯 **Persuadables** *(TARGET)* | ❌ Lost Causes *(skip)* |

This project **identifies each segment** using causal inference techniques and recommends optimal targeting strategies.

---

## 📊 Dataset

- **Source:** [Criteo AI Lab Uplift Modeling Dataset v2.1](https://ailab.criteo.com/criteo-uplift-prediction-dataset/)
- **Size:** 13.9M users × 12 anonymized features
- **Treatment:** Binary (ad exposed vs. control group)
- **Outcomes:** `visit`, `conversion`
- **Conversion Rate:** ~0.23% (rare event problem)
- **Treatment Imbalance:** ~85% treated, ~15% control

---

## 🛠️ Planned Methodology

### Phase 1: Data Engineering
- Stratified sampling of 13.9M users → memory-efficient subset
- Memory optimization via Parquet format + numerical downcasting
- Preservation of treatment-outcome distributions

### Phase 2: Baseline Analysis
- Naive correlational ML (XGBoost classifier)
- Demonstration of why standard ML fails for causal targeting

### Phase 3: Meta-Learners (CausalML library)
- S-Learner (Single Model with treatment as feature)
- T-Learner (Two separate outcome models)
- X-Learner (Robust to treatment imbalance)
- R-Learner (Robust to model misspecification)

### Phase 4: Modern Causal ML (EconML library)
- Double Machine Learning (DML)
- Causal Forests with confidence intervals
- Heterogeneous treatment effect estimation

### Phase 5: Deep Learning Approach (PyTorch)
- DragonNet architecture for treatment effect estimation
- Custom loss function combining outcome + propensity prediction

### Phase 6: Specialized Evaluation
- Qini Coefficient & Qini Curves
- AUUC (Area Under Uplift Curve)
- Decile Analysis & Profit/ROI Curves
- Comparative analysis across all methods

### Phase 7: Business Strategy & Deployment
- Customer segment-based targeting strategy
- ROI projections under different policies
- Interactive Streamlit dashboard for real-time uplift scoring

---

## 📁 Repository Structure

criteo-uplift-modeling/
├── notebooks/ # Jupyter notebooks (Kaggle-developed)
│ ├── 01-data-exploration-and-sampling.ipynb
│ ├── 02-eda-and-visualization.ipynb
│ ├── 03-baseline-correlational-ml.ipynb
│ ├── 04-uplift-meta-learners.ipynb
│ ├── 05-causal-forests-and-dml.ipynb
│ ├── 06-deep-learning-dragonnet.ipynb
│ ├── 07-evaluation-qini-auuc.ipynb
│ └── 08-business-strategy-and-roi.ipynb
│
├── src/ # Reusable Python modules
│ ├── data_loader.py # Data loading & sampling utilities
│ ├── models.py # Model implementations
│ ├── evaluation.py # Causal evaluation metrics
│ └── business.py # ROI & strategy calculations
│
├── streamlit_app/ # Interactive deployment
│ └── app.py # Live targeting recommendation engine
│
├── models/ # Trained model artifacts
├── reports/ # Analysis reports & figures
├── docs/ # Documentation & methodology notes
│
├── requirements.txt # Python dependencies
├── LICENSE # MIT License
└── README.md # You are here


---

## 📈 Project Progress

| Phase | Status | Notebook |
|-------|--------|----------|
| 1. Data Sampling & Preparation | ✅ Complete | `01-data-exploration-and-sampling` |
| 2. Exploratory Data Analysis | 🔄 In Progress | `02-eda-and-visualization` |
| 3. Baseline Correlational ML | ⏳ Planned | `03-baseline-correlational-ml` |
| 4. Uplift Meta-Learners | ⏳ Planned | `04-uplift-meta-learners` |
| 5. Causal Forests & DML | ⏳ Planned | `05-causal-forests-and-dml` |
| 6. Deep Learning (DragonNet) | ⏳ Planned | `06-deep-learning-dragonnet` |
| 7. Evaluation (Qini, AUUC) | ⏳ Planned | `07-evaluation-qini-auuc` |
| 8. Business Strategy & Deployment | ⏳ Planned | `08-business-strategy-and-roi` |

**Legend:** ✅ Complete | 🔄 In Progress | ⏳ Planned

---

## 💻 Tech Stack

**Languages:** Python  
**ML Frameworks:** Scikit-learn, XGBoost, PyTorch  
**Causal Inference:** EconML, CausalML, DoWhy  
**Data Processing:** Pandas, NumPy, PyArrow  
**Visualization:** Matplotlib, Seaborn, Plotly  
**Deployment:** Streamlit  
**Compute:** Kaggle Notebooks (P100 GPU)

---

## 🎓 Skills Demonstrated

- **Large-scale data engineering** — handling 13.9M-row dataset with memory constraints
- **Causal inference** — distinguishing correlation from causation
- **Modern Causal ML** — Meta-Learners, DML, Causal Forests
- **Deep learning** — custom neural architectures for treatment effects
- **Specialized evaluation** — uplift-specific metrics (Qini, AUUC)
- **Business translation** — converting ML outputs into ROI strategy
- **End-to-end deployment** — from notebook to live web application

---

## 📖 Key References

1. Diemert, E., Betlei, A., Renaudin, C., & Amini, M. (2018). *A Large Scale Benchmark for Uplift Modeling*. AdKDD Workshop, KDD.
2. Künzel, S. R., Sekhon, J. S., Bickel, P. J., & Yu, B. (2019). *Metalearners for estimating heterogeneous treatment effects using machine learning*. PNAS, 116(10), 4156-4165.
3. Athey, S., Tibshirani, J., & Wager, S. (2019). *Generalized Random Forests*. Annals of Statistics, 47(2), 1148-1178.
4. Shi, C., Blei, D. M., & Veitch, V. (2019). *Adapting Neural Networks for the Estimation of Treatment Effects*. NeurIPS.

---

## 👤 Author

**Anurag Jain**  
M.Sc. Economics, Indira Gandhi Institute of Development Research (IGIDR), Mumbai

- 📧 Email: 25msceco021@igidr.ac.in
- 💼 LinkedIn: [Anurag Jain](https://www.linkedin.com/in/anurag-jain-6b831b255/)
- 📊 Kaggle: [LINK](https://www.kaggle.com/anuragjaine)
- 📁 GitHub: [LINK](https://github.com/anuragjaine)

---

## 📜 License

This project is licensed under the MIT License — see the LICENSE file for details.

---

⭐ **If you find this project interesting, please star the repository!**  
🔔 **Watch this repo for updates as the project progresses.**
