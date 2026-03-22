# EMG Practical Workshop for 3rd-Year Bachelor Students

This repository contains a guided EMG practical experiment designed to help students move from signal understanding to data-driven movement classification.

## Experiment Purpose

The main purpose of this experiment is to teach students how to analyze EMG data in a complete workflow:

1. Understand raw EMG behavior across channels.
2. Compare normalization methods and explain why normalization is needed.
3. Extract meaningful EMG features from time and frequency domains.
4. Build and evaluate baseline classification models.
5. Understand the difference between random-split performance and subject-level generalization.

By the end of the practical, students should be able to explain not only model results, but also the reasoning behind preprocessing and feature choices.

## Repository Structure

- [experiment.ipynb](experiment.ipynb): Main practical notebook (step-by-step tutorial and experiments).
- [dataset_experiment](dataset_experiment): EMG dataset folders and CSV files.
- [LICENSE](LICENSE): License information.
- [Download Slide Presentation](B3-Workshop-EMG-2026.pdf): The World of EMG

## Dataset Details

### High-Level Summary

- Total subjects: 5 (`subject01` to `subject05`)
- Total CSV files: 200
- Movements (8 classes):
  - `2-finger-flexion`
  - `3-finger-flexion`
  - `extension-wrist`
  - `flexion-wrist`
  - `forearm-pronation`
  - `forearm-supination`
  - `radial-deviation`
  - `ulnar-deviation`
- Channels per sample: `EMG1`, `EMG2`, `EMG3`
- Typical recording duration: around 5 seconds per file
- Typical sampling rate: around 1000 Hz (actual value is provided per file)

### Folder and File Pattern

Data is grouped by subject folder:

- `dataset_experiment/subject01/`
- `dataset_experiment/subject02/`
- `dataset_experiment/subject03/`
- `dataset_experiment/subject04/`
- `dataset_experiment/subject05/`

Each file follows this naming pattern:

`subjectXX_<movement>_<trial>.csv`

Example:

`subject03_forearm-pronation_4.csv`

Meaning:
- `subject03`: participant ID
- `forearm-pronation`: gesture label
- `4`: trial index

### CSV Format

Each CSV contains:

1. Metadata lines (prefixed by `#`), such as:
   - requested and actual sampling rate
   - requested and actual duration
   - REST/MAX calibration values
   - normalization note
2. Data table with columns:
   - `sample_idx`
   - `EMG1`
   - `EMG2`
   - `EMG3`

## What Students Will Do in experiment.ipynb

The notebook is organized into practical steps:

1. Load and index all EMG files.
2. Visualize raw EMG signals (EMG1-EMG3).
3. Interpret envelope comparison for movement trends.
4. Compare normalization methods:
   - Min-Max
   - Z-score
   - Robust (median/IQR)
5. Extract EMG features:
   - Time-domain (MAV, RMS, VAR, WL, IEMG, ZC, SSC)
   - Frequency-domain (MNF, MDF, PWR)
6. Visualize feature behavior across channels and classes.
7. Build baseline movement classification.
8. Evaluate generalization with:
   - random train-test split
   - subject-independent hold-out
   - Leave-One-Subject-Out (LOSO)

## Why Generalization Testing Matters

A high score on random split does not always mean the model works well on new users.

This practical explicitly compares:

- Random split accuracy: easier setting, may mix subject characteristics in train and test.
- Subject-level validation (hold-out and LOSO): harder but more realistic for real-world deployment.

Students are expected to interpret this gap and discuss model robustness.

## Suggested Student Deliverables

Students should submit:

1. Brief interpretation of each major plot.
2. Comparison of normalization techniques and chosen method.
3. Feature analysis: which features appear most discriminative and why.
4. Classification comparison summary (random split vs subject-level validation).
5. Final conclusion with limitations and possible improvements.

## How to Run

1. Open [experiment.ipynb](experiment.ipynb).
2. Run cells from top to bottom.
3. If packages are missing, install: `numpy`, `pandas`, `matplotlib`, `scikit-learn`.

## Notes for Instructors

This material is intentionally designed at intermediate level for 3rd-year students:

- Strong students can extend to model tuning and filtering experiments.
- All students can still complete core workflow and interpretation tasks.

This balance supports both conceptual understanding and practical ML reasoning on biosignals.
