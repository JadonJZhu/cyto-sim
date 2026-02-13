# Cytokine Dose-Response Simulation

## Project Overview
This project simulates and models **cytokine dose-response relationships** using **machine learning** and **synthetic biological data**. It demonstrates a complete computational biology workflow—from data generation to predictive modeling—highlighting the critical importance of model selection in capturing biological realism.

## Workflow

### 1. Data Simulation (`generate_data.py`)
Generated synthetic gene expression data for 1000 cells to mimic experimental variability:
- **3 Donors** (varying baseline inflammation levels)
- **4 Cytokine Dosages** (0, 10, 50, 100 ng/mL)
- Modeled **biological noise** and gene-specific sensitivities.

### 2. Dimensionality Reduction (`main.py`)
Applied **Principal Component Analysis (PCA)** to visualize the high-dimensional biological state space.
- **Figure:** `visualization/biological_state_space_pca.png`
- The PCA reveals distinct clustering by cytokine dose, validating the presence of a strong biological signal within the noisy high-dimensional gene expression data.

![PCA Visualization](visualization/biological_state_space_pca.png)

### 3. Model Comparison: SVR vs. Random Forest
Trained two regression models to predict marker gene expression based on cytokine dose and donor identity:
- **Random Forest Regressor**: An ensemble of decision trees.
- **Support Vector Regression (SVR)**: Utilized with an **RBF (Radial Basis Function) kernel** and feature scaling.

## Key Findings: Biological Plausibility

A "virtual experiment" was conducted to predict gene expression across a continuous range of unseen doses (0–100 ng/mL), allowing for a direct comparison of model behavior.

![Dose Response Comparison](visualization/comparison_dose_response_curve.png)

### Analysis
- **Random Forest (Red Curve)**: The model exhibits **jagged, step-wise predictions**, which are characteristic of decision tree ensembles. It tends to **overfit** the stochastic noise present in the training data, leading to biologically implausible fluctuations between measured doses.
- **SVR with RBF Kernel (Green Curve)**: The SVR model produces a **smooth, continuous response curve**. It generalizes effectively between sparse data points, capturing the underlying linear dose-response relationship. This smoothness makes the SVR model **physically more plausible** for biological systems, where physiological responses are typically continuous and graded rather than discrete steps.

## Limitations & Future Directions

### Limitations
- **Synthetic Data**: The current analysis relies on simulated data with programmed linear relationships (`generate_data.py`), which simplifies the stochastic nature of real cellular signaling.
- **Simplified Noise Model**: Biological noise is approximated using a normal distribution, whereas real single-cell data often features zero-inflation (dropout) and bursty expression patterns.

### Looking Forward
- **Experimental Validation**: The next phase would involve training the SVR model on real-world RT-qPCR or RNA-seq data to validate its predictive power.
- **Time-Course Modeling**: Integrating temporal dynamics to model how cytokine responses evolve over time, rather than just at a static endpoint.
- **Multi-Omics Integration**: Expanding the feature set to include proteomic or epigenomic data for a more holistic view of the biological state.

## Technologies Used
- **Python**
- **Scikit-learn** (PCA, SVR, Random Forest, Pipelines)
- **Pandas & NumPy** (Data Manipulation)
- **Seaborn & Matplotlib** (Scientific Visualization)

---
*This project demonstrates proficiency in computational biology, machine learning model selection, and data visualization.*a
