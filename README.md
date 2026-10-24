# Deployability Access: The Paradox of Covert Consciousness

**Author:** Mohammad Dawood Rahimi, Freie Universität Berlin  
**ORCID:** [0000-0002-6282-1862](https://orcid.org/0000-0002-6282-1862)  
**Contact:** MD.Rahimi@fu-berlin.de  
**Repository:** https://github.com/dawooderahimi-md/MD.Rahimi  
**Software DOI:** Add the version-specific DOI after archiving the first release on Zenodo.

## Purpose and scope

This repository contains the computational materials accompanying the Perspective *Deployability Access: The Paradox of Covert Consciousness*. The notebook and its input tables implement exploratory simulations used to clarify the framework's assumptions and illustrate selected mathematical consequences. They do not constitute an empirical test of deployability access (DA), are not fitted to patient data, and do not establish that the model's reserve proxy measures biological energy or that the network reproduces cognitive motor dissociation (CMD). All model parameters are specified for the computational demonstrations rather than estimated from clinical observations.

The framework distinguishes three requirements for a task-related response to support observable behavior: **formation**, **persistence**, and **propagation**. The simulations illustrate selected implications of this distinction. Their results should be interpreted only within the equations, parameters, and operational readouts implemented in the notebook.

## Repository contents

The notebook and both input tables currently sit in the repository root:

| File | Description |
|---|---|
| `DA_complete_colab_perspective.ipynb` | Main Jupyter/Google Colab notebook for the supporting computations. |
| `TableS1a_connectivity_W.csv` | Modeler-specified directed connectivity matrix. Rows represent target nodes; columns represent source nodes. |
| `TableS1b_tau_theta.csv` | Node-level relaxation-time and sigmoid-threshold parameters, together with the task-input fields included in the archived table. |
| `README.md` | Project description, execution guidance, output inventory, and limitations. |
| `ONLINE_RELEASE_CHECKLIST.md` | Release-preparation checklist; it is administrative documentation, not an input to the analysis. |
| `CITATION.cff` | Recommended citation metadata; add it to the repository before creating a versioned release. |

The notebook is intended to generate `DA_outputs/` and a downloadable `DA_outputs.zip` during execution. These are generated results, not input files. Include the generated outputs in the public release only after running the notebook successfully and checking the resulting files. Add `CITATION.cff` and the chosen licence file(s) before tagging a citable release. The current repository is public, but a versioned release and software DOI have not yet been created.

## Run the notebook in Google Colab

1. Upload the notebook and the two CSV files to a public GitHub repository, or open the notebook directly in Google Colab after uploading it there.
2. Open `DA_complete_colab_perspective.ipynb` in Colab.
3. The first code cell checks for the two expected CSVs in `/content/DA_inputs/` (or the folder set by `DA_INPUT_DIR`). If either file is missing in Colab, the cell opens a single upload dialog for the missing input(s). Upload `TableS1a_connectivity_W.csv` and `TableS1b_tau_theta.csv` with their exact filenames. The setup cell validates the matrix labels, node order, dimensions, and the `tau`, `theta`, and `task_input` columns.
4. Select **Runtime → Run all**. Runtime depends on the Colab session, package versions, and hardware; no fixed execution time is guaranteed.
5. Inspect `DA_outputs/TableA_code_checks.csv`, `Table2_parameters.csv`, and `MANIFEST.json`. Confirm that all 13 checks pass, that the intended production files were loaded, and that the figures and tables exist. Download `DA_outputs.zip` before closing or resetting the session.

**Important:** Google Colab runtimes are temporary. Download any generated files that you want to preserve before closing or resetting the session.

## Run locally

Use Python 3 with `numpy`, `scipy`, `pandas`, `matplotlib`, and `openpyxl`. Open `DA_complete_colab_perspective.ipynb` in Jupyter Notebook or JupyterLab and run the cells in order. Place both CSV files in the location expected by the notebook's input-loading cell, or use the built-in fallback if that is what the notebook reports. The notebook reads `DA_INPUT_DIR` if it is set; otherwise, it uses `/content/DA_inputs/` in Colab or `./DA_inputs/` in a local environment. The input loader reads the `tau`, `theta`, and `task_input` columns from `TableS1b_tau_theta.csv`, validates the seven-row node order, and uses the seven task-input values in the simulation. If the archived file is absent, the notebook uses the built-in defaults. The updated notebook has been executed end-to-end in a local Python environment with both production CSVs present; all 13 automated checks passed. This is not a substitute for rerunning the published commit in a clean Colab session before creating the versioned release. Inspect the input-source message, `Table2_parameters.csv`, and `MANIFEST.json` in that release run. The manifest records the Python and core package versions.

For reproducible reporting, record the Python version, package versions, operating environment, notebook revision, selected input source, and random seeds used in the run. Do not describe results as independently reproduced until a fresh run has completed successfully.

## Random seeds and reproducibility

The notebook specifies the following seeds for the principal simulation groups:

| Analysis | Seed |
|---|---:|
| Nominal network ensemble | `12345` |
| Extended no-input control | `12346` |
| Reduced-model Kramers-rate analysis | `1` |
| Reduced-model signature analyses | `3` |
| Duty-cycle demonstrations | `7` |

The fixed seeds support reproducibility under the same code and compatible software environment. Exact numerical identity across different package versions, platforms, or modified notebooks should not be assumed without checking the outputs. Sensitivity analyses use matched stochastic paths where specified, and the step-size comparison uses matched Brownian increments. The local validation run recorded Python 3.13.5, NumPy 2.3.5, pandas 2.2.3, SciPy 1.17.0, Matplotlib 3.10.8, and openpyxl 3.1.5 in `MANIFEST.json`.

## Verification before release

After a complete run, inspect `DA_outputs/TableA_code_checks.csv`. The notebook reports 13 automated checks covering update rules, Brownian-increment coarsening, connectivity-matrix summaries, and selected headline results. In the local end-to-end validation completed on 2026-10-24 with both production CSV files present, all 13 checks passed. This validates the supplied notebook in that environment; it does not guarantee that a later edit or a different runtime will produce the same result. Rerun the exact public commit in a clean Colab session before publishing a versioned release. The connectivity checks for the archived matrix returned row sums `0.1` (sensory) and `1.3` (motor), spectral norm `1.3117`, and spectral radius `0.9015`.

Also inspect `Table2_parameters.csv` and `MANIFEST.json` to confirm which connectivity and node-parameter files the notebook loaded. Keep the manifest with the outputs. If a check fails or the recorded input source differs from the intended source, resolve that discrepancy before creating a citable release.

## Output files and their locations in the article

The following mapping describes the intended relationship between generated output files and the manuscript. Confirm the file inventory against a fresh `DA_outputs.zip` before release, because the actual contents depend on a successful notebook run.

| Output file | Intended article location or use |
|---|---|
| `Table2_parameters.csv` | Main-text Table 2. |
| `Table3_reference_crossing_times.csv`, `Table3b_reference_vs_observed.csv` | Main-text Table 3 and its reference calculations. |
| `Table4_ensemble_summary.csv`, `ensemble_outcomes_all_runs.csv` | Main-text Table 4 and per-realization outcomes. |
| `Table4b_windowed_motor_frontal_ratios.csv` | Main-text Table 5. |
| `Table9_reduced_model_Kramers.csv` | Main-text Table 6. |
| `Table5_sensitivity_one_at_a_time.csv` | Supplementary Table S2. |
| `Table6_step_size_check.csv` | Supplementary Table S3. |
| `Table6b_gain_branch_stress_test.csv` | Supplementary Table S4. |
| `TableS5_duty_cycle.csv` | Supplementary Table S5. |
| `TableS6_contraction_bound.csv` | Supplementary Table S6. |
| `Table7_frozen_reserve_equilibria.csv` | Supplementary Table S7. |
| `TableS8_duty_cycle_criterion.csv` | Supplementary Table S8. |
| `TableS1a_connectivity_W.csv`, `TableS1b_tau_theta.csv` | Supplementary Tables S1a and S1b. |
| `Table8a_persistence_after_cue.csv`, `Table8b_variance_autocorrelation.csv` | Reduced-model values discussed in Section 4.6. |
| `TableA_analytical_properties.csv` | Analytical properties cited in the text. |
| `TableA_code_checks.csv` | Automated implementation checks. |
| `TableA_text_values.csv` | In-text numerical values not tabulated elsewhere. |
| `Figure1`–`Figure7` in PDF and PNG formats | Main figures. Figures 1 and 7 are conceptual schematics; Figures 2, 5, and 6 concern the reduced model. Check figure captions for the scope of the remaining figures. |
| `FigureS1`–`FigureS7` | Supplementary figures: depletion stress test, duty-cycle comparison, no-input control, connectivity matrix, event-time distributions, windowed activity ratios, and ensemble bands. |
| `Supplementary_Tables_all.xlsx` | Workbook containing output tables on separate sheets, with an index sheet. |
| `MANIFEST.json` | File inventory and run metadata. |

Spreadsheet software may reinterpret character strings such as `5-15` as dates when CSV files are opened directly. Import such columns as text when necessary, or use the typed cells in the generated Excel workbook.

## Interpretation and limitations

- The seven-node network uses a modeler-specified connectivity matrix; the weights were not estimated from diffusion MRI, functional-connectivity data, or patient data.
- The reserve variables are dimensionless computational proxies, not measurements of ATP, phosphocreatine, mitochondrial capacity, glucose metabolism, or regional energy availability.
- The implemented shared gain is a model parameter controlling the sigmoid transfer function. It is not a direct measure of neuromodulation or hierarchical precision; the conceptual precision expression is not implemented in the network.
- The reduced model's bifurcation, potential barrier, and Kramers-rate results do not automatically transfer to the seven-node network.
- The frozen-gate contraction analysis applies only when gates, gain, and input are fixed. It does not characterize the full reserve-coupled system's long-term dynamics.
- Duty-cycle outputs are fractions of simulated task time above an activity criterion, not probabilities of detecting CMD or consciousness.
- The motor-to-frontal activity ratio is a descriptive model readout, not a measure of propagation efficiency.
- Agreement between a simulation and an expected pattern demonstrates internal consistency under the stated assumptions; it does not validate the framework biologically.

## Citation

The public source repository is available at https://github.com/dawooderahimi-md/MD.Rahimi. No versioned software release or DOI has been issued yet. After uploading the corrected notebook, rerunning the published commit in a clean Colab session, and checking the outputs, create a GitHub release and archive that version on Zenodo. Then replace this paragraph with the version-specific software citation and DOI supplied by Zenodo. Cite the associated manuscript separately using its final publication details; do not list a journal, publication year, volume, or page range before those details are confirmed.

**Suggested software citation format after the first release:**  
Rahimi, M. D. (2026). *Deployability Access: The Paradox of Covert Consciousness — Supporting Computational Materials* (Version 1.0.0) [Computer software]. Zenodo. [Insert the version-specific DOI issued by Zenodo].

## Licensing

Resolve licensing before the public release. A practical arrangement is to license the notebook/code under the MIT License and original tables and figures under the Creative Commons Attribution 4.0 International licence (CC BY 4.0), using separate licence files and clearly identifying which materials each covers. This is a recommendation, not a licence already granted. Do not leave alternative licence choices or ambiguous licensing terms in the published repository.

## Release history

- **Pre-release working repository:** Public source files are online. The revised notebook now loads all seven task-input values from the parameter CSV and validates the input tables. A local end-to-end run using both production CSVs passed all 13 automated checks. Version 1.0.0 remains planned; first upload the revised notebook and documentation, rerun the published commit in a clean Colab session, inspect outputs, and select licences.
