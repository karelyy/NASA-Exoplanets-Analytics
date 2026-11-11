# 🌌 NASA Exoplanetary Systems Analytics

### Exploring planetary properties, orbital patterns, and machine learning predictions

An exploratory data analysis and machine learning project focused on **NASA's confirmed exoplanet records**. Using Python, statistical methods, and data visualization, this project investigates planetary characteristics, their relationships with host stars, and the factors associated with exoplanet equilibrium temperature.

---

## 🎯 Project Objectives

- 🔭 Explore the physical and orbital characteristics of discovered exoplanets.
- 📊 Identify statistical relationships between planetary properties and their host stars.
- 🪐 Analyze the distribution of exoplanets across stellar systems.
- 🤖 Develop a Machine Learning model to predict planetary equilibrium temperature.

## 📁 Dataset

**Source:** [Exoplanetary Systems Discovered by NASA – Kaggle](https://www.kaggle.com/datasets/sathyanarayanrao89/nasa-exoplanetary-system/data)  
**Original data source:** [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/)

The original dataset contains **32,552 records and 93 variables**, covering exoplanet discoveries from 1989 to 2022.

After selecting the default published and confirmed parameter set (`default_flag = 1`), the analytical dataset contains:

| Dataset characteristic | Records |
|---|---:|
| Confirmed exoplanets | 5,044 |
| Unique host systems (star) | 3,781 |
| Selected variables | 19 |
| Discovery period | 1989–2022 |

Each row in the master dataset represents one exoplanet, identified by `pl_name`, with associated host-system information (`hostname`).

## 🧹 Data Preparation

The data preparation process included:

- Selecting relevant variables for the research questions.
- Filtering records using `default_flag = 1`.
- Reviewing data types, missing values, and categorical consistency.
- Checking identifiers, relationships between variables, and duplicate records.
- Identifying extreme values and evaluating their potential astronomical relevance.

**Important:** Missing values were preserved in the master dataset. Analytical subsets were created according to the variables required for each analysis.

## 🔎 Exploratory Data Analysis

The analysis focuses on four main areas:

**1. 🪐 Planetary Characteristics**
- Planetary radius (`pl_rade`)
- Planetary mass (`pl_bmasse`)
- Equilibrium temperature (`pl_eqt`)
- Orbital period (`pl_orbper`)
- Orbital eccentricity (`pl_orbeccen`)

**2. ⭐ Planet–Star Relationships**
- Stellar mass (`st_mass`)
- Stellar radius (`st_rad`)
- Stellar effective temperature (`st_teff`)
- Relationships between planetary and stellar properties.

**3. 🛰️ Orbital Dynamics**
- Orbital period versus semi-major axis.
- Orbital distance versus equilibrium temperature.
- Orbital eccentricity versus semi-major axis.

**4. 🌠 Planetary Systems**
- Number of planets per host system (`sy_pnum`).
- Number of stars per system (`sy_snum`).
- Distribution of known planets across stellar systems.

## 📈 Key Findings

### 1. Planetary mass and radius

A positive relationship was identified between planetary mass and radius, based on 976 records containing both measurements.

| Statistical method | Correlation |
|---|---:|
| Pearson (original scale) | 0.34 |
| Spearman | 0.78 |
| Pearson (logarithmic scale) | 0.84 |

The results suggest a strong monotonic relationship that becomes more evident after logarithmic transformation. The dispersion may reflect differences in planetary composition and measurement methods.

### 2. Orbital distance and equilibrium temperature

A negative Spearman correlation of **-0.50** was observed between orbital distance and equilibrium temperature.

The visual analysis highlights the concentration of hot planets in close orbits, including hot Jupiters, as well as the presence of large, distant planets with high temperatures.

### 3. Orbital eccentricity

The analysis reveals different orbital patterns across the observed population. Many planets in close orbits show low eccentricity, while some more distant planets exhibit substantially more elliptical orbits.

### 4. Extreme values and data distribution

Planetary properties show wide ranges and asymmetric distributions. Extreme observations were investigated as potentially meaningful astronomical cases rather than automatically classified as erroneous records.

## 🤖 Machine Learning — Random Forest Regressor

A Random Forest regression model was developed to predict **planetary equilibrium temperature (`pl_eqt`)** based on selected planetary and stellar characteristics.

### Data Preparation

| Stage | Records |
|---|---:|
| Initial dataset | 5,044 |
| Records after removing missing values (NaN) | 766 |
| Retained data | 15.2% |

Complete-case filtering was applied, removing records with missing values in the selected model variables.

### Model Configuration

- **Algorithm:** Random Forest Regressor.
- **Target variable:** Planetary equilibrium temperature (`pl_eqt`).
- **Data split:** 80% training / 20% testing.
- **Training records:** 612.
- **Testing records:** 154.

### Model Performance

| Evaluation metric | Result |
|---|---:|
| R² (Coefficient of Determination) | 0.934 |
| Mean Squared Error (MSE) | 21,539.515 |
| Root Mean Squared Error (RMSE) | 146.76 K |

### Preliminary Results

The model achieved an R² of 0.934, indicating that it explained approximately 93.4% of the variance in equilibrium temperature within the test sample.

The RMSE of approximately 146.76 K represents the typical magnitude of prediction errors, expressed in Kelvin.

Predictions showed smaller deviations for several medium and high-temperature observations, while some colder planets presented larger errors.

### Limitations and Considerations

- Only 15.2% of the initial dataset remained after removing records with missing values.
- The reduced sample size may limit the model's representativeness of the overall exoplanet population.
- The model's performance depends on the selected features and their completeness.
- Random Forest captures nonlinear relationships but does not establish physical causality.
- Further validation, feature importance analysis, and cross-validation are recommended to assess model robustness.

*The reported metrics correspond to the evaluated test sample and should not be interpreted as evidence of generalization to all known exoplanets. Model performance should be interpreted in the context of the validation strategy, sample size, and potential observational biases. *

## 🛠️ Technologies & Libraries

- 🐍 **Python** — Data analysis and model development.
- 🐼 **Pandas** — Data manipulation and preparation.
- 🔢 **NumPy** — Numerical operations.
- 📊 **Matplotlib & Seaborn** — Statistical visualization.
- 📈 **Plotly** — Interactive visualizations.
- 🧪 **SciPy** — Statistical analysis and correlation methods.
- 🤖 **Scikit-learn** — Machine Learning.

## ⚠️ Limitations

- Not all planetary parameters are available for every record.
- Some analyses use smaller subsets due to missing measurements.
- Planetary mass values may represent mass or projected mass (`M × sin(i)`), depending on the measurement method.
- Observational and detection biases influence the population of known exoplanets.
- Correlation does not imply causation.
- The number of known planets in a system does not necessarily represent the total number of planets that exist there.

## 📂 Repository Structure

```text
exoplanetary-systems-analytics/
│
├── README.md
├── requirements.txt
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   └── exoplanetary_systems_analytics.ipynb
│   └── exoplanetary_systems_ml.ipynb
│
└── outputs/
    ├── figures/
    └── interactive/
```

## 🚀 Project Purpose

This project combines my engineering background with my growing experience in Data Analytics and Data Science. It demonstrates an end-to-end analytical workflow, from data understanding and preparation to statistical exploration, visualization, and predictive modeling.

---

**Author:** Lilian Karely Martínez  
**Project:** NASA Exoplanets Analytics  
**Date:** November 2026
