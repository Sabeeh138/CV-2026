# Task 3 — Real-Time Echocardiogram Video Analysis

Student: Sabeeh | Roll number: 23K-0002

## Objective
Process frames from a short local EchoNet-Dynamic ultrasound MP4 and show raw and enhanced frames beside one another.

## Dataset and sample
Stanford EchoNet-Dynamic ([Kaggle](https://www.kaggle.com/datasets/manojkumarcs28/echonet-dynamic-by-stanford-university)). Do not download or include the full dataset. Put one short sample clip at `data/sample_echo.mp4`. The video is opened through `cv2.VideoCapture` using this relative path, never from a webcam.

## Pipeline
Each frame is converted to grayscale and histogram-equalized, mapped with JET, color-balanced by per-channel mean correction, and enhanced with logarithmic and gamma (1.4, greater than 1) transforms. The notebook displays the original and enhanced frame via `cv2.imshow`, saves representative raw/enhanced/side-by-side PNGs, and exits on `q` or end of file. Gamma greater than one compresses bright values relative to darker values to reduce backscatter prominence.

## Libraries
OpenCV, NumPy, Matplotlib, and Jupyter.

## Run
From the repository root: `python -m pip install -r requirements.txt`, then `jupyter notebook Task_3_Echo_Analysis/realtime_echo.ipynb`. In a desktop session, the frames appear in an OpenCV window; press `q` to close playback. If no GUI is available, the notebook continues processing the clip and still saves its representative frames.

## Outputs
Representative raw frame, enhanced frame, and side-by-side frame are saved in `output/`.
