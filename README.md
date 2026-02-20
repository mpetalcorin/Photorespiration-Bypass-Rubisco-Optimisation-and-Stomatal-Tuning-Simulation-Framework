# Photorespiration-Bypass-Rubisco-Optimisation-and-Stomatal-Tuning-Simulation-Framework
This repository contains simulation and analysis scripts used in the study “Integrative Simulation of Photorespiration Bypass, Rubisco Optimisation, and Stomatal Tuning Predicts Synergistic Improvements in C₃ Crop Photosynthetic Efficiency.”

The framework combines synthetic biology and machine learning to explore how three photosynthetic engineering interventions—photorespiration bypass (PB), Rubisco optimisation (RO), and stomatal tuning (ST)—affect photosynthetic efficiency, water-use efficiency (WUE), and nitrogen-use efficiency (NUE) under realistic environmental conditions.

## Key Features
	•	Generates synthetic plant–environment datasets (10,000 virtual conditions)
	•	Implements biochemical and physiological parameters for PB, RO, and ST
	•	Uses Random Forest regression to model nonlinear interactions
	•	Quantifies feature importance and trait-environment synergies
	•	Produces interpretable plots for ΔAₙₑₜ, ΔWUE, and ΔNUE

## Project structure

```text
photosynthesis-simulation
 ┣ data
 ┃ ┣ environmental_parameters.csv
 ┃ ┗ simulation_results.csv
 ┣ models
 ┃ ┗ random_forest_model.pkl
 ┣ figures
 ┃ ┣ deltaAn_by_temp.png
 ┃ ┣ deltaWUE_by_vpd.png
 ┃ ┣ model_deltaAn_feature_importance.png
 ┃ ┗ deltaNUE_by_soilN.png
 ┣ photorespiration_bypass_rubisco_stomata.ipynb
 ┣ README.md
 ┣ DATA_SHEET.md
 ┗ MODEL_CARD.md
```
## Dependencies

	•	Python ≥ 3.10
	•	NumPy, Pandas, Matplotlib, Seaborn
	•	scikit-learn
	•	Jupyter Notebook

## Outputs

	•	Predicted changes in photosynthetic (ΔAₙₑₜ), water-use (ΔWUE), and nitrogen-use (ΔNUE) efficiency
	•	Visual feature importance and heatmaps
	•	Machine learning model artifacts for reproducibility

 # DATA_SHEET.md

 ## Dataset Name
Synthetic Crop Photosynthetic Response Dataset (v1.0)

 ## Motivation
The dataset was generated to explore how bioengineering interventions in C₃ photosynthesis—photorespiration bypass, Rubisco optimisation, and stomatal tuning—interact with environmental and nutrient conditions to affect crop performance metrics such as carbon assimilation, water-use efficiency, and nitrogen-use efficiency.

 ## Composition

| Variable | Description | Units | Range |
|-----------|--------------|--------|--------|
| temperature | Leaf temperature | °C | 18–42 |
| light_intensity | Photosynthetic photon flux density (PPFD) | µmol m⁻² s⁻¹ | 200–1800 |
| vapor_pressure_deficit | Atmospheric dryness | kPa | 0.6–3.0 |
| soil_nitrogen | Available soil nitrogen | ppm | 10–120 |
| ΔAₙₑₜ | Change in net CO₂ assimilation | µmol CO₂ m⁻² s⁻¹ | -0.05–0.20 |
| ΔWUE | Change in water-use efficiency | dimensionless | -0.10–0.25 |
| ΔNUE | Change in nitrogen-use efficiency | dimensionless | -0.05–0.30 |
| trait_PB | Photorespiration bypass activation (binary) | 0/1 | — |
| trait_RO | Rubisco optimisation activation (binary) | 0/1 | — |
| trait_ST | Stomatal tuning activation (binary) | 0/1 | — |

## Collection Process

Data were synthetically generated using parameter distributions derived from peer-reviewed literature on rice (Oryza sativa), wheat (Triticum aestivum), and soybean (Glycine max). Environmental variability was sampled via Latin Hypercube Sampling to ensure broad coverage of realistic conditions.

## Preprocessing

All continuous variables were normalized between 0–1. Binary trait indicators (PB, RO, ST) were encoded as 0/1 categorical variables.

## Intended Uses
	•	Evaluating machine learning models for crop photosynthesis
	•	Exploring environmental and biochemical trait interactions
	•	Developing explainable AI tools for plant metabolic modeling

## Limitations
	•	Simulated data do not replace empirical field trials
	•	Trait effects assume additive noise models based on literature ranges
	•	Results depend on parameter selection and environmental sampling density

# MODEL_CARD.md

## Model Name

Photosynthesis Trait Interaction Model (Random Forest Regressor)

## Overview

A Random Forest regression model trained on 10,000 synthetic crop-environment data points to predict:
	•	ΔAₙₑₜ (change in net CO₂ assimilation)
	•	ΔWUE (change in water-use efficiency)
	•	ΔNUE (change in nitrogen-use efficiency)

The model captures nonlinear relationships among bioengineered traits and environmental factors.

## Model Details

| Attribute | Description |
|------------|--------------|
| Framework | scikit-learn |
| Algorithm | Random Forest Regressor |
| Number of Trees | 200 |
| Max Depth | 10 |
| Cross-Validation | 5-fold |
| R² Score | 0.96 |
| RMSE | 0.013 (ΔAₙₑₜ) |

## Training Data

Synthetic dataset representing environmental and physiological variability across C₃ crops (rice, wheat, soybean). Derived parameters align with known photosynthetic responses from field and chamber studies (South et al., 2019; Carmo-Silva et al., 2023).

## Intended Use
	•	Identify key drivers of photosynthetic efficiency
	•	Quantify interaction effects between engineered traits
	•	Support hypothesis generation for experimental crop engineering

## Interpretability

Feature importance analysis was conducted using permutation methods, revealing that:
	•	Rubisco optimisation contributed 31% of ΔAₙₑₜ variance
	•	Temperature and light intensity contributed 43% collectively
	•	Photorespiration bypass explained most ΔBiomass variance under stress

## Limitations
	•	The model relies on synthetic data, not direct experimental calibration
	•	Predictions are context-dependent (C₃ crops under controlled environmental distributions)
	•	Not intended for absolute yield prediction or policy decision-making

## Ethical and Scientific Considerations
	•	No personal or sensitive data involved
	•	Promotes open reproducibility in agricultural modeling
	•	Intended solely for academic and educational purposes

## How to cite

**Petalcorin, M.I.R.** (2025). Redesigning photosynthesis: a machine learning simulation and synthetic strategies to enhance carbon, water, and nitrogen efficiency in crops. agriRxiv. https://www.cabidigitallibrary.org/doi/pdf/10.31220/agriRxiv.2025.00374

## License

MIT License © 2025 Mark Ihrwell R. Petalcorin
 
