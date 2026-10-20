# SDWPF Wind Power Forecasting

This repository contains the Jupyter notebooks and generated output files for a study of wind-power forecasting using the **Spatial Dynamic Wind Power Forecasting (SDWPF)** dataset. The study examines data-quality handling and forecasting generalization to turbines that are held out from model training.

**Repository:** https://github.com/hnkhoaa8-flower/sdwpf-wind-power-forecasting

## Repository organization

The project is organized across two branches so that the main analysis notebooks remain separate from the files generated when they are run.

### `main` branch — notebooks and documentation

The `main` branch contains three files:

- `README.md` — project overview and instructions.
- **Notebook A** — the first primary analysis notebook.
- **Notebook B** — the second primary analysis notebook.

Open the [main branch](https://github.com/hnkhoaa8-flower/sdwpf-wind-power-forecasting/tree/main) to view the notebooks and their original filenames.

## Research overview

The project uses SDWPF, a public wind-turbine dataset, to study short-term wind-power forecasting. The analysis documented in the notebooks covers:

- data inspection and data-quality handling;
- forecasting-model evaluation against a persistence baseline;
- evaluation on turbines used during model development and on held-out, unseen turbines;
- comparison of forecast performance across the evaluated prediction horizons.

The experiment details, implementation, and outputs should be taken from the notebooks and the saved files in the `report` branch. Results are specific to the data selection, preprocessing, split strategy, model settings, and evaluation procedures implemented in those notebooks.

## Dataset

The SDWPF dataset is publicly available on Figshare:

- [SDWPF dataset — Version 2](https://doi.org/10.6084/m9.figshare.24798654)
- [Dataset paper](https://doi.org/10.1038/s41597-024-03427-5)

The raw dataset is not stored in this repository. Download the required data from the official dataset page and follow the data paths and preprocessing steps specified in the notebooks. The exact files needed may depend on which dataset version and subset the notebook expects.

The dataset authors' data-processing and baseline implementation is available in the [PaddleSpatial WPF baseline repository](https://github.com/PaddlePaddle/PaddleSpatial/tree/main/apps/wpf_baseline_gru).

## How to run the notebooks

1. Clone or download this repository.
2. Download the SDWPF data files required by the notebooks from the official dataset source.
3. Open the notebooks from the `main` branch in Jupyter Notebook, JupyterLab, or Google Colab.
4. Check the import/setup cells and update any dataset paths so that they point to the downloaded files.
5. Run the notebook cells in their documented order. If a notebook relies on files or variables produced by the other notebook, follow the dependency notes in the notebook before running it.

This repository currently keeps the two notebooks and README in `main`; a separate `requirements.txt` is not included. Install the Python packages imported by the notebooks in your environment before running them. For reproducibility, record the Python and package versions used for your experiment.

## Reproducibility notes

- The 41 generated files are stored in the [`report` branch](https://github.com/hnkhoaa8-flower/sdwpf-wind-power-forecasting/tree/report).
- To reproduce the results, use the same dataset version, data subset, preprocessing rules, train/validation/test split, model settings, and evaluation metrics as documented in the notebooks.
- Saved outputs help readers inspect the results without rerunning the full analysis, but they do not by themselves guarantee that the results can be reproduced in a different environment.
- The outputs should be interpreted in the context of the experiments and limitations described in the notebooks.

## Citation

If you use the SDWPF dataset, please cite its accompanying dataset paper:

> Zhou, J., Lu, X., Xiao, Y., Tang, J., Su, J., Li, Y., Liu, J., Lyu, J., Ma, Y., & Dou, D. (2024). *SDWPF: A Dataset for Spatial Dynamic Wind Power Forecasting over a Large Turbine Array*. Scientific Data, 11, 649. https://doi.org/10.1038/s41597-024-03427-5

## Code availability

The notebooks and study-generated outputs are available in this repository:

- [Source notebooks (`main` branch)](https://github.com/hnkhoaa8-flower/sdwpf-wind-power-forecasting/tree/main)
- [Generated outputs (`report` branch)](https://github.com/hnkhoaa8-flower/sdwpf-wind-power-forecasting/tree/report)
