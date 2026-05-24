# Predictive Assessment of Tilestones Frost Resistance through Impact Sound Analysis

This repository contains the source code and datasets for the acoustic analysis and predictive modeling of tilestones frost resistance, as presented in our paper submitted to the *Journal of the Acoustical Society of America* (JASA).

## Project Overview

When traditional roofing craftsmen select tilestones (lauzes), they hammer them and listen for a "bright tinkling" as an indicator of durability. This project objectifies this practice using:
1. **Acoustic Preprocessing:** Isolating and cleaning the impact sound.
2. **Feature Computing:** Extracting key audio features (RMS, spectral centroid, flatness, contrast, sound decay rate, etc.) using `librosa`.
3. **Statistical Analysis:** Evaluating correlations and training a classifier to predict frost resistance based on early acoustic descriptors.

---

## Repository Structure

The project directory is organized as follows:

```
├── audio/                  # Audio data directories
│   ├── 0_raw_sound/        # Original, unedited impact sound recordings (.wav)
│   └── 4_norm/  # Final preprocessed sound signals used for feature extraction
│
├── data/                   # Experimental measurements
│   └── data_ini.csv # Physical properties (mass, frequencies, damping before/after freeze-thaw cycles)
│
├── preprocessing.py         # Script for audio signal cleaning and transformation
├── featurescomputing.py    # Script for extracting acoustic descriptors from audio/4_norm/
├── statistical_analysis.py # Script for correlation analysis and statistical analysis
├── stats.csv       # Extracted feature summary matrix used by the statistical script
└── README.md               # This file

```
## Installation & Requirements
To run the scripts, you need Python 3.8+ and the required libraries.
Clone the repository: Bashgit clone [https://github.com/foguedjombou/tilestone-impact-sound-analysis.git](https://github.com/foguedjombou/tilestone-impact-sound-analysis.git)

```
cd tilestone-impact-sound-analysis

 # Install the dependencies:

 #Bash
pip install numpy pandas librosa scikit-learn matplotlib soundfile
```
## How to Run the Pipeline
The analysis is executed in three sequential steps:
- Step 1: Preprocessing the AudioClean and segment the raw impact recordings. This script processes files from audio/0_raw_sound/ through various stages and saves the final outputs into audio/4_norm/.Bashpython preprocessing.py
- Step 2: Feature ExtractionCompute the audio descriptors (e.g., spectral flatness, contrast, temporal RMS, and damping coefficients) from the preprocessed audio files.Bashpython featurescomputing.py
- Step 3: Statistical Analysis & PredictionRun the statistical analysis to evaluate feature correlations with frost resistance and train the predictive model using a leave-one-out cross-validation scheme.Bashpython statistical_analysis.py

Contact : yifoguedjombou@cesi.fr
