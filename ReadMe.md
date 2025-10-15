# XGB-UNetFuse: A Density-Aware Hybrid Framework for Automated Retinal Ganglion Cell Quantification 

This repository contains the complete pipeline for **retinal ganglion cell (RGC) detection and counting** using deep learning.  
It includes data preparation, model training, post-processing, and performance evaluation scripts implemented primarily in Jupyter Notebooks.

---

## 🧠 Overview

This framework provides a **deep-learning-based solution** for cell counting across different retinal regions (central, middle, peripheral).  
The modular design allows independent execution of each stage, from preprocessing to model evaluation.

**Main functionalities:**
- DIC-like preprocessing and image tiling
- U-Net and Light-U-Net model training
- Gaussian smoothing, thresholding, reconstruction and local maxima post-processing
- Statistical evaluation via Bland–Altman and bootstrap analysis
- Visualization and reconstruction of final outputs


### 🚀 Prerequisites

Make sure you have all required packages listed in `requirements.txt`. Or install all required packages:

```bash
pip install -r requirements.txt
```

### 📂 Dataset Usage

You can use our **custom dataset** located in the `Dataset/` folder, or you can place your own dataset in this directory.  
Make sure to split your data into three subsets: `train/`, `test/`, and `evaluation/`.  

Each of these folders should contain the following subdirectories:
- **`orig/`** → Original RGC (retinal ganglion cell) images  
- **`gt/`** → Expert-annotated ground truth images (manual markings by the expert)

This structure ensures compatibility with all preprocessing, training, and evaluation scripts in the framework.


## 🧩 Framework Pipeline

The following figure illustrates the complete workflow of the RGC detection and counting framework — from dataset preparation to model training, prediction, and evaluation.

<p align="center">
  <img src=".\assets\Paper_Workflow.jpg" alt="Framework Pipeline" width="800"/>
</p>


## 📘 Code Overview

This repository includes several Jupyter Notebooks, each implementing a key component of the RGC counting framework.  
Below is a brief description of the functionality and purpose of each file:


| Notebook | Description |
|-----------|--------------|
| **Dataset_Preparation.ipynb** | Handles all preprocessing steps, including normalization, DIC-like enhancement of input RGC images and Region label prepration to prepare them for training |
| **tiling_solution.ipynb** | Implements the tiling and stitching logic for handling large microscopy images that exceed GPU memory limits, ensuring seamless reconstruction. |
| **generator.ipynb** | Builds data generators for efficient batch loading and augmentation during model training. It ensures consistent pairing between `orig` and `gt` images. |
| **model.ipynb** | Defines the neural network architectures used in this project (U-Net and Light-U-Net) and their building blocks, including convolutional, pooling, and upsampling layers. |
| **U-Net-train_using_image_itself.ipynb** | Trains the U-Net model using the prepared dataset, monitors training/validation losses, and saves model checkpoints. |
| **Light-U-Net-train_using_image_itself.ipynb** | Trains a lightweight variant of the U-Net architecture optimized for faster inference with fewer parameters while maintaining accuracy. |
| **extract_features_and_train_xgb.ipynb** | Extracts image- or region-based features (e.g., mean intensity, texture) from outputs to support hybrid models or correlation studies with manual annotations. |
| **plot_network_results.ipynb** | Loads trained model checkpoints and plots the predicted outputs for each image tile, saving the visualized predictions for further reconstruction or analysis. |
| **reconstruct_best.ipynb** | Reconstructs full-size retinal images from tiled predictions produced by the both-performing model, enabling visualization and quantitative validation on complete images for later comparison. |
| **final_workflow.ipynb** | Integrates all steps—preprocessing, model inference, post-processing, and evaluation—into a single end-to-end pipeline ready for deployment or benchmarking. |
| **Bootstrap.ipynb** | Performs bootstrap statistical analysis on prediction results to estimate confidence intervals and quantify variability of both U-Net and Light-U-Net models across multiple samples. |
| **bland_altman_plots_light_unet.ipynb** | Generates Bland–Altman plots to assess agreement between predicted and manual RGC counts, providing insight into both model and the final framework bias and consistency. |
---

Each notebook can be executed independently, but running them in the above order is recommended for reproducing the complete RGC detection and counting pipeline.

## 👩‍🔬 Authors

**Narges Yarahmadi Gharaei**  
📧 narges.yarahmadi@dal.ca  

**Darshana Upadhyay**  
📧 Darshana@dal.ca

**Delaney C. M. Henderson**  

**Aliénor J. Jamet**  

**Michele L. Hooper**  

**Balwantray C. Chauhan**  

**Srinivas Sampalli**  
