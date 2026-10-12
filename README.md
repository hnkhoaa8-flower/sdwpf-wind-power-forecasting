# SDWPF Wind Power Forecasting

## Overview

This project investigates short-term wind power forecasting using the SDWPF dataset, with a focus on SCADA data cleaning, persistence-baseline comparison, unseen-turbine generalization, and multi-horizon forecasting.

## Research Topics

- SCADA data quality and cleaning rules
- One-hour-ahead wind power forecasting
- Comparison of ten regression models against persistence
- Generalization to unseen wind turbines
- Forecast-horizon sensitivity
- Day-block bootstrap uncertainty estimation

## Repository Structure

- `paper/`: LaTeX manuscript, figures, and final PDF
- `notebooks/`: Data preprocessing, model training, and evaluation
- `sql/`: SQL queries used to select the experimental data
- `results/`: Experimental tables and evaluation outputs

## Dataset

SDWPF dataset v2: https://doi.org/10.6084/m9.figshare.24798654

Please refer to the dataset's original publication for data definitions and recommended preprocessing rules.

## Reproducibility

1. Install the Python packages listed in `requirements.txt`.
2. Download the dataset from the original source.
3. Configure the dataset path in the notebook.
4. Run the notebooks in the documented order.
5. Compare the generated metrics with the files in `results/`.

## Authors

- Nhat Khoa Ha
- Ngoc Dat Pham
- Thu Le

FPT University, Vietnam
