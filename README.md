# Image Panorama Stitching

**A feature-based computer vision pipeline for creating panoramic images from overlapping photographs.**

This project implements an image stitching pipeline that detects and matches local features, estimates geometric transformations, and combines multiple images into a seamless panorama.

Rather than relying on a single high-level stitching function, the project implements key components of the pipeline, including normalized Direct Linear Transform (DLT), RANSAC-based homography estimation, and distance-weighted image blending.

## Results

### Sunset panorama

![Sunset panorama](outputs/sunset_result.jpg)

### Tufa panorama

![Tufa panorama](outputs/tufa_result.jpg)

### Additional example

![Additional panorama](outputs/cuadro_result.jpg)

## How It Works

The stitching pipeline consists of the following stages:

**1. Feature Detection and Description**

SIFT is used to detect distinctive keypoints and extract local feature descriptors.

**2. Adaptive Non-Maximal Suppression (ANMS)**

ANMS selects spatially distributed keypoints to improve feature coverage across each image.

**3. Feature Matching**

Descriptor correspondences are obtained using brute-force matching with Euclidean distance. The implementation supports cross-check matching, Lowe's ratio test, and a combined strategy.

**4. Homography Estimation**

A projective transformation is estimated using normalized DLT and Singular Value Decomposition (SVD).

**5. RANSAC**

Random Sample Consensus identifies geometrically consistent correspondences and reduces the influence of incorrect matches.

**6. Image Warping and Blending**

Images are transformed into a common panorama canvas using perspective warping. Distance-transform-based blending weights are used to combine overlapping regions and reduce visible seams.

## Technologies

- Python
- OpenCV
- NumPy
- Matplotlib
- SIFT
- RANSAC
- Projective Geometry

## Project Structure

```text
.
├── inputs/
├── outputs/
│   ├── sunset_result.jpg
│   ├── tufa_result.jpg
│   └── cuadro_result.jpg
├── src/
│   ├── anms.py
│   ├── features.py
│   ├── homography.py
│   ├── matching.py
│   ├── ransac.py
│   ├── stitching.py
│   └── visualization.py
├── tp1_pano.ipynb
├── requirements.txt
└── README.md
```

## Getting Started

Install the required Python libraries:

```bash
pip install opencv-python numpy matplotlib jupyter
```

Open the main notebook:

```bash
jupyter notebook tp1_pano.ipynb
```

The notebook contains the experimental workflow and panorama generation process.

## Academic Context

Developed as an academic Computer Vision project focused on feature-based image alignment, robust geometric estimation, and panoramic image generation.
