# Results Overview

This folder contains the **final reported results** presented in the paper.  
The intermediate visualization outputs (such as per-tile network predictions) are **not included** here due to their large storage size.  
However, **all plots and numerical results are fully reproducible** using the provided notebooks and saved checkpoints.

---

## Reproducibility Instructions

### 1. Tile-Level Predictions
- The predicted tile images of both (U_Net and Light_U_Net) networks can be regenerated using the notebook **`plot_network_results.ipynb`**.  
- The model checkpoints are available under the **`checkpoints/`** directory.  
- Running this notebook will reproduce all network prediction visualizations shown in the paper.

### 2. Reconstructed Predictions and Cell Counting
- The **last two code blocks** of **`final_workflow.ipynb`** can be used to:
  - Reconstruct the full-sized prediction maps from tiles.  
  - Perform **cell counting** using the **local maxima detection** method with adjustable parameters **T (threshold)** and **σ (Gaussian smoothing)**.  
- The optimal parameters used in the paper are provided here for reference, but any configuration can be re-evaluated to reproduce or extend the results.

### 3. Region-Wise Error Analysis
- For region-specific quantitative comparisons, use **`compare_parameters.ipynb`** to generate the summary CSV files.  
- This notebook computes both **signed** and **absolute** cell count errors across retinal regions.  
- The resulting CSV file (e.g., **`average_signed_abs_over_under_errors.csv`**) includes detailed statistics for multiple parameter combinations.

---
## 🔗 External Storage Notice

Due to their large size, the following result folders are **not hosted directly in this repository**.  
They are instead available for download from the linked external drive:

| Folder | Description | External Link |
|:--------|:-------------|:---------------|
| **`Light_U_Net/`** | Contains the reconstructed prediction results of the *Light_U_Net* model, along with cell counts of  outputs for region-level error analysis. | [View on Google Drive](https://drive.google.com/drive/folders/19hTfl7-5WkmfUU_fa3dLsdkrGJ40v_eL?usp=sharing) |
| **`U_Net/`** | Includes the corresponding prediction maps, and final cell counting results for the *U_Net* model. | [View on Google Drive](https://drive.google.com/drive/folders/10FLmisv27bZeDpEot1JSl2LzWiObbyi4?usp=drive_link) |
| **`XGB_UNetFuse/`** | Provides the fused predictions, comparative analyses, and final quantitative results for the proposed *XGB-UNetFuse* framework. | [View on Google Drive](https://drive.google.com/drive/folders/1n0lYAqTn3DCT8joCUqiPONNRR0ThRT6G?usp=drive_link) |

> 📁 Each linked folder mirrors the same structure used in this repository and can be directly used with the provided notebooks to reproduce all plots and analyses presented in the paper.

---
## Notes
- Reported results in this folder correspond to the **best-performing configuration** described in the paper.  
- All results, including those not explicitly shown here, are **fully reproducible** using the provided code and model checkpoints.
