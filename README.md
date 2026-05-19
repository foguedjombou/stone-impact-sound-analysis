# stone-impact-sound-analysis
Codebase for predictive assessment of stones frost resistance using impact sound analysis

# Predictive Assessment of Tilestones Frost Resistance through Impact Sound Analysis

This repository contains the source code and datasets for the acoustic analysis and predictive modeling of tilestones' frost resistance, as presented in our paper submitted to the *Journal of the Acoustical Society of America* (JASA).

This project establishes a direct link between the acoustic properties of tilestones and their frost resistance using digital signal processing. It proves that structural durability can be predicted via statistical descriptors of impact sound, providing a scientific foundation to support and understand empirical methods like traditional stone hammering.

## Project Overview

When traditional roofing craftsmen select tilestones (lauzes), they hammer them and listen for a "bright tinkling" as an indicator of durability. This project objectifies this practice using:
1. **Acoustic Preprocessing:** Isolating and cleaning the impact sound.
2. **Feature Computing:** Extracting key audio features (RMS, spectral centroid, flatness, contrast, sound damping coefficient, etc.) using `librosa`.
3. **Statistical Analysis:** Evaluating correlations and training a classifier to predict frost resistance based on early acoustic descriptors.

---

## Repository Structure

The project directory is organized as follows:

```
├── audio/                  # Audio data directories
│   ├── 0_raw_sound/        # Original, unedited impact sound recordings (.wav)
│   ├── 1_mono/          # Cropped sound signals
│   ├── 2_filtered/           # Filtered sound signals
│   ├── 3_trim/         # Sound signals time normed
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

## Key Findings Highlight
Our model demonstrates that frost resistance is strongly linked to the internal homogeneity of the stone microstructure. Key predictive features identified include: c_std: The standard deviation of the sound damping coefficient (reflecting structural homogeneity), minimum RMS and Spectral Flatness thresholds. Mechanically, this confirms that acoustic energy dissipates through microstructural flaws, such as microcrack friction, in less resistant stones.

## Authors & Citation
Yannick Igor Fogue Djombou¹, Patrice Guyot², Nicolas Sutton-Charani², and Stéphane Corn³
¹CESI LINEACT, CESI, Villeurbanne, France ² EuroMov Digital Health in Motion, Univ Montpellier, IMT Mines Ales, France ³ LMGC, Univ Montpellier, IMT Mines Ales, CNRS, Ales, France

If you find this work or code useful for your research, please cite our JASA paper:
```
@article{fogue2026predictive,
  title={Predictive assessment of tilestones frost resistance through impact sound analysis},
  author={Fogue Djombou, Yannick Igor and Guyot, Patrice and Sutton-Charani, Nicolas and Corn, Stéphane},
  journal={The Journal of the Acoustical Society of America},
  year={2026},
  publisher={The Journal of the Acoustical Society of America}
}
```
