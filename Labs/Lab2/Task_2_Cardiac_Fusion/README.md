# Task 2 — Multi-Modal Cardiac Image Fusion

Student: Sabeeh | Roll number: 23K-0002

## Objective
Enhance one corresponding cardiac CT/MRI slice pair and combine their heatmaps into a single visualization.

## Dataset and sample
Heart CT & MRI Dataset ([Kaggle](https://www.kaggle.com/datasets/ziya07/heart-ct-and-mri-dataset)). The full dataset is not included. Copy one corresponding heart CT slice to `data/sample_ct.png` and its heart MRI counterpart to `data/sample_mri.png` (PNG/JPG/JPEG supported by OpenCV). The files supplied so far are a labeled lung CT and a brain image containing MRI/CT views, so they are not suitable cardiac inputs; A CT montage has since been supplied and stored as `data/sample_ct.png`, but it is a small multi-slice chest montage rather than one aligned heart slice. The earlier ZIP also contained two-tone circle placeholders, which the notebook rejects. Task 2 fusion still requires one real heart CT slice and its matching MRI slice from the same region. The notebook validates that both files exist, rejects placeholder graphics, and requires their dimensions to match exactly because resizing does not align anatomy.

## Pipeline and fusion logic
CT and MRI are independently converted to grayscale and histogram-equalized, then mapped to JET heatmaps. `cv2.addWeighted(ct_heatmap, 0.70, mri_heatmap, 0.30, 0)` gives CT the heavier contribution to retain sharper boundaries while the lighter MRI contribution adds soft-tissue contrast. This is an illustrative overlay, not a registered or clinically validated fusion. Logarithmic and gamma (<1) transforms are applied to the fused image for display.

## Libraries
OpenCV, NumPy, Matplotlib, and Jupyter.

## Run
From the repository root: `python -m pip install -r requirements.txt`, then `jupyter notebook Task_2_Cardiac_Fusion/modal_fusion.ipynb`.

## Outputs
Enhanced CT/MRI slices, both heatmaps, fused and transformed images, and a side-by-side comparison are saved in `output/`.
