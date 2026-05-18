# Warming-driven lower-tropospheric stratification intensifies atmospheric ducting over global oceans

[![Python Version](https://img.shields.io/badge/python-3.12-blue.svg)](https://www.python.org/downloads/release/python-3120/)
[![OS](https://img.shields.io/badge/OS-Windows_11-lightgrey.svg)]()

## 📖 Overview
This repository contains the source code and usage instructions associated with the manuscript entitled **“Warming-driven lower-tropospheric stratification intensifies atmospheric ducting over global oceans”**. 

The code is designed for atmospheric duct data processing, analysis, and visualization. The workflow includes:
* Data reading and preprocessing
* Empirical Orthogonal Function (EOF) analysis
* Statistical analysis
* Map-based visualization

> **Note:** Due to the large volume of the high-resolution meteorological dataset, raw data are not included in this repository and must be downloaded directly from the public repository (see [Data Acquisition](#-data-acquisition)).

---

## 💻 System Requirements

### Hardware Requirements
The software can be run on a standard desktop or laptop computer. No non-standard hardware or GPU acceleration is required.
* **CPU:** Standard multi-core processor
* **RAM:** 16 GB or higher
* **Storage:** Depends on the temporal and spatial extent of the downloaded data (at least **50 GB** of available space is recommended for processing large reanalysis datasets).

### Software Requirements
* **Operating System:** Tested on Windows 11 (64-bit)
* **Environment:** [PyCharm](https://www.jetbrains.com/pycharm/) (Recommended)
* **Interpreter:** Python 3.12

---

## ⚙️ Installation Guide

### Step-by-Step Installation
1. Clone this repository or download the source code and open the project in PyCharm.
2. Ensure the project interpreter is set to **Python 3.12**.
3. Open the PyCharm terminal (or your standard command prompt).
4. Update `pip` and install the required dependencies by running the following commands:

```bash
python -m pip install --upgrade pip
python -m pip install pandas==2.2.3 numpy==1.26.4 netCDF4==1.7.2 cartopy==0.24.1 matplotlib==3.9.4 numba==0.61.2 eofs==2.0.0 scipy==1.15.3 xarray==2024.4.0
```
Typical Installation Time: Approximately 10–20 minutes on a standard desktop, depending on internet speed and local environment configuration.

## 📥 Data Acquisition

Due to the massive size of the high-resolution reanalysis data, the raw dataset is not included. Users must download the raw experimental data from the Copernicus Climate Data Store (CDS) or the ECMWF Data Catalogue.

### Primary Method: Direct Download (Recommended)
* **Dataset:** ERA5 hourly data on single levels
* **Source:** Copernicus CDS
* **Required Variables:** `dndzn`, `dndza`, `tplt`, `tplb`, `dctb`
* **Format:** Ensure the downloaded data is in **NetCDF (`.nc`)** format for script compatibility.

### Alternative Method: Calculation from Model Levels
Alternatively, atmospheric ducting parameters can be derived by calculating the modified atmospheric refractive index profile from raw meteorological variables.

* **Source:** ECMWF Data Catalogue
* **Required Variables:**
  * Specific humidity & Temperature *(Model levels 88–137)*
  * Logarithm of surface pressure & Geopotential *(Model level 1)*

---

## 🚀 Usage Instructions

### General Workflow
1. **Download** the required ERA5 dataset (in `.nc` format) to a local folder.
2. **Open** the provided Python script in PyCharm.
3. **Configure Paths:** Locate the folder path variables in the main script and modify them to match your local environment:
   * `INPUT_FOLDER`: Point this to the directory containing your downloaded ERA5 NetCDF files.
   * `OUTPUT_FOLDER`: Point this to the desired directory for saving generated figures and processed data.
   > **Note:** Ensure your downloaded `.nc` file names match the naming conventions expected in the Python script, or adjust the script's read function accordingly.
4. **Run** the script using the Python 3.12 interpreter.
5. **Check** the specified output directory for your results.

### Expected Inputs and Outputs
* **Input:** `.nc` files downloaded from the ERA5 repository.
* **Output:** Depending on the script executed, the code will generate:
  * Processed tabular data files
  * Statistical analysis results
  * EOF analysis outputs
  * Figures and maps (visualizations of atmospheric ducting)
  * Intermediate/final result files

### ⏱️ Expected Run Time
On a standard desktop computer, run time depends heavily on the temporal and spatial size of the ERA5 dataset processed.

* **Subset Data (e.g., single year/specific region):** ~10–30 minutes.
* **Multi-decadal Global Data:** Significantly longer.
