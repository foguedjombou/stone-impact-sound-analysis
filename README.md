# Predictive Assessment of Tilestones Frost Resistance through Impact Sound Analysis

This repository contains the source code and datasets for our paper "Predictive assessment of tilestones frost resistance through impact sound analysis", submitted to the *Journal of the Acoustical Society of America* (JASA).

## Project Overview

In traditional roofing, craftsmen select tilestones by hammering them, seeking a 'bright tinkling' as an indicator of durability. In order to assess this practice objectively, monitored impact tests were conducted in the laboratory on tilestones samples selected from limestone with varying geological characteristics. The resulting sound signals were analysed over multiple recordings per sample using some statistical audio features. Then, whilst these tilestones were subjected to freeze–thaw cycles, their mechanical integrity was monitored by probing their vibratory impulse response, which subsequently led to classify each sample as frost resistant or not. In this study, the ability of audio features to forecast the frost resistance of tilestones is investigated through interpretable statistical learning approaches. 

This repository is organised as follows:
1. **Acoustic pre-processing:** Designed to isolate the intrinsic vibratory response of the material from possible impact-related artifacts.
2. **Features extraction:** Extracting audio features (rms, centroid, flatness, rolloff, contrast, peak frequency and sound decay rate) using `librosa`.
3. **Statistical Analysis:** Learning and evaluation of supervised approaches. Feature importance rankings. Spearman correlation analysis.

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
- Step 1: Preprocessing the Audio
Clean and segment the raw impact recordings. This script processes files from audio/0_raw_sound/ through various stages and saves the final outputs into audio/4_norm/
- Step 2: Feature Extraction
Compute the audio descriptors (e.g., spectral flatness, contrast, temporal RMS, and damping coefficients) from the preprocessed audio files
- Step 3: Statistical Analysis & Prediction
Run the statistical analysis to evaluate feature correlations with frost resistance and train the predictive model using a leave-one-out cross-validation scheme

Contact : yifoguedjombou@cesi.fr
