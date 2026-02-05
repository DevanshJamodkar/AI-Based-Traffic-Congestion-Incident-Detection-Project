# 🚦 AI-Based Traffic Congestion & Incident Detection

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange)
![Status](https://img.shields.io/badge/Status-Completed-green)

> **A Decision-Layer Machine Learning Pipeline for Aerial Traffic Analytics.** > *Developed as part of the AIML + Drone Tech Program (IIT Hyderabad TiHAN / Masai School).*

---

## 📖 Project Overview

This project addresses the challenge of **real-time traffic management** using aerial (drone) data. Unlike traditional Computer Vision approaches that process raw video feeds (which are bandwidth-heavy and privacy-intrusive), this project operates at the **Decision Layer**.

It builds an intelligent classification pipeline that takes extracted feature data—such as vehicle density, speed, and lane occupancy—to instantly determine if a road segment is **"Normal"** or **"Congested/Incident"**.

### 🎯 Key Objectives
* **Classify Road State:** Distinguish between free-flow traffic (0) and congestion/incidents (1).
* **Analyze Traffic Physics:** Prove that `Density ≠ Congestion` (e.g., a fast-moving highway has high density but is not congested).
* **Spatial Visualization:** Simulate a traffic control dashboard using prediction heatmaps.
* **Explainability:** Use tabular data to provide transparent reasons for alerts.

---

## 📊 The Dataset

The model is trained on a feature-level dataset extracted from aerial imagery. It does **not** use raw images, focusing instead on the physics of traffic flow.

| Feature | Description | Traffic Context |
| :--- | :--- | :--- |
| **`vehicle_density`** | Vehicles per unit area | High density alone doesn't mean traffic; it must be paired with speed. |
| **`avg_vehicle_speed`** | Mean velocity of objects | The strongest inverse indicator of congestion. |
| **`speed_std`** | Standard Deviation of speed | High variance implies stop-and-go turbulence. |
| **`lane_occupancy`** | % of road capacity used | Accounts for vehicle size (trucks vs. bikes). |
| **`queue_length`** | Length of stopped line | Direct proxy for bottlenecks/intersections. |
| **`time_of_day_norm`** | Normalized time (0-1) | Helps distinguish routine rush hour vs. off-hour incidents. |

---

## ⚙️ Approach & Methodology

### 1. Exploratory Data Analysis (EDA)
We analyzed the correlation between features to understand traffic behavior.
* **Insight:** "High Density + High Speed" = Free Flow (Normal).
* **Insight:** "High Density + Low Speed" = Congestion (Incident).

### 2. Model Selection
We implemented and compared two models:
* **Logistic Regression (Baseline):** Provides linear coefficients to understand feature impact.
* **Random Forest Classifier (Ensemble):** The final model. It captures non-linear relationships (e.g., how road width affects the density threshold for congestion).

### 3. Evaluation Metrics
We prioritized **Recall** over Accuracy. In safety systems, missing an incident (False Negative) is worse than a false alarm.
* **ROC-AUC Score:** ~0.93 (Excellent separability)
* **Recall (Congestion):** ~80%
* **Accuracy:** ~85%

---

## 📈 Results & Visualization

### Spatial Congestion Heatmap
*The model's predictions are aggregated to visualize congestion hotspots across the monitored zone.*

![Spatial Heatmap](assets/spatial_heatmap.png)
*(Note: Red tiles indicate high probability of congestion/incidents)*

### Feature Importance
*Top drivers of congestion:*
1.  **Average Vehicle Speed**
2.  **Vehicle Density**
3.  **Queue Length**

---

## 🚀 How to Run

### Option 1: Google Colab (Recommended)
**[Click Here to Open Notebook]** (INSERT_YOUR_COLAB_LINK_HERE)

### Option 2: Local Installation
1.  Clone the repo:
    ```bash
    git clone [https://github.com/your-username/traffic-congestion-ai.git](https://github.com/your-username/traffic-congestion-ai.git)
    ```
2.  Install dependencies:
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn
    ```
3.  Run the notebook:
    ```bash
    jupyter notebook Traffic_Congestion_Project.ipynb
    ```

---

## 📂 Repository Structure
