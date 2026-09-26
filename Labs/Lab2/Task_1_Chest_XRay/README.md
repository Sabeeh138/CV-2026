# Task 1 — Diagnostic Enhancement of Chest X-Rays

Student: Sabeeh | Roll number: 23K-0002

## Objective
Apply classic intensity enhancement operations to one grayscale chest X-ray and save each result for comparison.

## Dataset and sample
COVID19+PNEUMONIA+NORMAL Chest X-Ray Image Dataset ([Kaggle](https://www.kaggle.com/datasets/sachinkumar413/covid-pneumonia-normal-chest-xray-images)). The dataset is not bundled. Download one permitted sample image and save it as `data/sample_xray.png` (PNG, JPG, or JPEG accepted when named `sample_xray` with that extension). Do not copy the full dataset.

## Pipeline and mathematics
Grayscale histogram equalization redistributes intensities using the cumulative histogram. `COLORMAP_JET` maps the equalized intensity to a false-color visualization. A per-channel affine color shift moves the JET image toward neutral channel balance. Strict thresholding keeps only pixels above the selected high-intensity cutoff. The logarithmic transform `c*log(1+x)` expands low intensities; gamma correction `x**gamma` with gamma below 1 brightens darker values. These are display/educational operations, not clinical diagnosis.

## Libraries
OpenCV, NumPy, Matplotlib, and Jupyter.

## Run
From the repository root: `python -m pip install -r requirements.txt`, then `jupyter notebook Task_1_Chest_XRay/xray_enhancement.ipynb`. Place the sample in `Task_1_Chest_XRay/data/` first.

## Outputs
The notebook writes original, equalized, JET, balanced, thresholded, logarithmic, gamma-corrected, and comparison PNGs into `output/`.
