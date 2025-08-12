# 📘 Machine Learning for Turbulence Risk Prediction in U.S. Airspace Using Open Flight and Weather Data

**Graduate Capstone Project by [Godha Naravara](https://github.com/godhanaravara)**  
**Repository:** `aviation-turbulence-risk-predictor-ML`

---

## Problem Statement

Turbulence, especially clear-air turbulence (CAT), remains a serious challenge for aviation safety — often arising unexpectedly and outside the reach of radar-based forecasting systems. This project aims to **predict high-risk turbulence events** using open datasets from aviation reports and atmospheric reanalysis sources, providing a data-driven alternative to traditional physics-based forecasting.

---

## 🌍 Data Sources

- **PIREPs** (Pilot Reports)  
  From the Iowa Environmental Mesonet — real-time turbulence observations from pilots.

- **ERA5 Reanalysis**  
  Hourly pressure-level atmospheric data (28 levels) from Copernicus CDS, with 300+ GB downloaded for 2024.  
  Variables included: wind speed, shear, cloud content, vorticity, geopotential, humidity, and more.

---

## ML Pipeline Overview

- **Data Cleaning & Merging**
  - Matched PIREPs with ERA5 based on location, time, and altitude (hPa)
- **Feature Engineering**
  - Derived features like wind shear, vertical velocity, cloud water content, etc.
- **Class Balancing**
  - Isolation Forest: Downsampled the majority "NEG" turbulence class based on anomaly scores  
  - SMOTE: Oversampled the critical "SEV–EXTRM" turbulence cases
- **Dimensionality Reduction + Clustering**
  - Applied **PCA** (99% variance) and **KMeans** to discover latent risk zones
- **Model Training**
  - **XGBoost** (main model)
  - Comparisons with: Random Forest, LightGBM, CatBoost, TabNet, KNN, Naive Bayes

---

## Evaluation

- **Stratified 10-Fold Cross Validation**
- **Ablation Studies**:
  - Evaluated the impact of PCA, clustering, SMOTE, and anomaly-based downsampling
- **Unseen Data Testing**:
  - 2025 case study (e.g., Feb 16) used for generalization check
  - Strong performance shown on new seasonal patterns

---

## Results

- **XGBoost**:
  - F1-score: **0.88**
  - Accuracy: **91.97%**
- **PCA + KMeans**:
  - Discovered a high-risk cluster with **82.35%** SEV–EXTRM sample concentration
- **Visualizations**:
  - Confusion matrices, feature deviation plots
  - 3D PCA visualizations
  - U.S. turbulence heatmaps and high-risk cluster overlays

---

## Skills Demonstrated

| Area | Techniques Used |
|------|------------------|
| **Data Collection** | API-based and scripted retrieval from IEM and CDS |
| **Data Engineering** | Time/altitude matching, 35+ weather features |
| **Class Imbalance** | Isolation Forest + SMOTE (applied only to training set) |
| **Unsupervised ML** | PCA + KMeans |
| **Supervised ML** | XGBoost, CatBoost, LightGBM, TabNet, KNN, Naive Bayes |
| **Model Evaluation** | Cross-validation, unseen test evaluation, ablation |
| **Visualization** | Matplotlib, Plotly, PCA plots, U.S. map overlays |

---

## Disclaimer

To protect research originality and ensure academic integrity:
- **Full dataset and raw code are not shared publicly**
- This repository showcases selected techniques, workflows, and outputs
- For collaboration or more information, feel free to [reach out](mailto:godhanaravara@outlook.com)

---

## 📎 Author

**Godha Naravara**  
GitHub: [@godhanaravara](https://github.com/godhanaravara)  
Master’s in Computer Science, Ohio University  
Project Repo: [`aviation-turbulence-risk-predictor-ML`](https://github.com/godhanaravara/aviation-turbulence-risk-predictor-ML)
