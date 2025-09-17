# DIVA-seg
Deep learning for Intracranial Vessel and Aneurysm segmentation from MRA-TOF based on nnU-Net v2

## Overview
This repository provides a trained segmentation model based on **nnU-Net v2**.  
The model was trained on proprietary data and therefore the training data cannot be shared. Only the model weights and configuration files required for inference are included.  

- **Framework:** nnU-Net v2  
- **Task:** Vessel and aneurysm segmentation from MRA-TOF scans  
- **Input:** 1. MRA-TOF image, and 2. binary image with aneurysm center of mass. both NIfTI format  
- **Output:** segmentation mask of vessels (label 1) and aneurysms (label 2)  

---

## Contents
```
DIVA-seg/
├──nnUNetTrainer__nnUNetPlans__3d_fullres
	├── fold_0
		├── checkpoint_final.pth         # trained weights
		├── debug.json
		├── progress.png
	├── fold_1
		├── checkpoint_final.pth         # trained weights
		├── debug.json
		├── progress.png
	├── fold_2
		├── checkpoint_final.pth         # trained weights
		├── debug.json
		├── progress.png
	├── fold_3
		├── checkpoint_final.pth         # trained weights
		├── debug.json
		├── progress.png
	├── fold_4
		├── checkpoint_final.pth         # trained weights
		├── debug.json
		├── progress.png
	├── dataset.json                     # dataset specification
	├── dataset_fingerprint.json         # dataset fingerprint
	├── plans.json                       # preprocessing & architecture plans
└── README.md                            # this document
```

---

## Usage

### 1. Installation
Make sure you have nnU-Net v2 installed:  
```bash
pip install nnunetv2
```

### 2. Download the trained model
Copy the `DIVA-seg/` folder into your nnU-Net results directory:  
```bash
$RESULTS_FOLDER/<TaskName>/nnUNetTrainer__nnUNetPlans__3d_fullres
```

### 3. Run inference
```bash
nnUNetv2_predict   -i INPUT_IMAGES_FOLDER   -o OUTPUT_FOLDER   -d TaskXXX_DIVA-seg   -c 3d_fullres   -tr nnUNetTrainer   --chk checkpoint_final
```

- `INPUT_IMAGES_FOLDER`: Folder containing preprocessed input images (NIfTI format).  
- `OUTPUT_FOLDER`: Destination for segmentation outputs.  
- `TaskXXX_DIVA-seg`: Replace with your task name (defined in `dataset.json`).  

---

## Notes
- This release **does not include training data**.  
- The model is research-only and has **not been certified for clinical decision making**.  

---

## Citation
If you use this model, please cite:  

```
nnU-Net v2: Isensee, F., Jaeger, P. F., Kohl, S. A., Petersen, J., & Maier-Hein, K. H. (2020). nnU-Net: a self-configuring method for deep learning-based biomedical image segmentation. Nature Methods, 1-9.
```
```
DIVA-seg: Verschuur, A.S., Zhang, J. Kamphuis, M.J., Tax, C.M.W., van der Schaaf, I.C. [year] Towards improved decision making of unruptured intracranial aneurysms using automated segmentation from MRA-TOF. [journal] [vol,issue,pages]

```

