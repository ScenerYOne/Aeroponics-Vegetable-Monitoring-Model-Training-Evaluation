![Python](https://img.shields.io/badge/Python-3.9-blue?logo=python&logoColor=white)
![YOLOv8](https://img.shields.io/badge/YOLO-Ultralytics-blueviolet)

# Aeroponics Vegetable Monitoring  

Dataset Engineering, Model Training & Deployment Pipeline (YOLOv8)

## 🔗 Connected Projects (End-to-End AI Pipeline)

This project is part of a complete AI workflow, covering data preparation, model training, and deployment.

### 1️⃣ Image Preprocessing & Dataset Generation  
[ScenerYOne/Aeroponics-Vegetable-Monitoring-Image-Preprocessing](https://github.com/ScenerYOne/Aeroponics-Vegetable-Monitoring-Image-Preprocessing.git)

- Perspective Transformation for camera correction  
- Image standardization  
- Dataset preparation for YOLO training  
- Manual labeling workflow  

---

### 2️⃣ Model Training & Evaluation (This Repository)   
[ScenerYOne/Aeroponics-Vegetable-Monitoring-Model-Training-Evaluation](https://github.com/ScenerYOne/Aeroponics-Vegetable-Monitoring-Model-Training-Evaluation)

- Dataset cleaning & normalization  
- Multi-dataset integration  
- YOLOv8 model training and fine-tuning  
- Automated training reports (mAP, Precision, Recall)  
- ONNX export  

---

### 3️⃣ Model Deployment Platform 
[ScenerYOne/AI-Model-Deployment-Evaluation-Platform](https://github.com/ScenerYOne/AI-Model-Deployment-Evaluation-Platform)

- Web-based YOLO model testing  
- FastAPI backend for inference  
- React frontend for visualization  
- Real-time detection with bounding boxes and class labels  

---

## 🔁 Full System Workflow

This repository documents my hands-on experience in **Computer Vision, Dataset Engineering, and Deep Learning model training**, focusing on an **Aeroponics vegetable monitoring system**.
The project demonstrates an **end-to-end AI workflow**, starting from image preprocessing and dataset normalization, through model training and evaluation, and finally connecting to a deployment platform.

This repository serves both as:
- A **technical record** of my work
- A **portfolio project** for job applications in AI / ML / Computer Vision roles

##  Project Objective

The main goals of this project are to:

- Prepare high-quality datasets from real-world aeroponics environments
- Normalize YOLO labels from multiple data sources
- Train a robust vegetable detection model using YOLOv8
- Track experiments and training metrics
- Export trained models for deployment
- Demonstrate a production-oriented AI pipeline

---

##  Key Design Principles

- **No AI-based preprocessing**  
  → All preprocessing is deterministic and script-based

- **Human-verified labels only**  
  → No auto-labeling or pseudo-labeling

- **Data quality over model complexity**

- **Reproducible and auditable pipeline**

- **Designed for real deployment, not demo-only**

---

##  Project Structure

```text
MODEL_CUU/
│
├── dataset/ # Main dataset
├── dataset_method_1/ # Additional dataset (Method 1)
│
├── pre-process/ # Dataset engineering scripts
│ ├── changeclass.py
│ ├── check.py
│ ├── delename_time.py
│ ├── delete.py
│ ├── delete_image.py
│ ├── delete_imagejpg.py
│ ├── delete_imagetxt.py
│ └── delete_name.py
│
├── runs/ # YOLO training outputs
├── training_logs/ # Training reports & metrics
│
├── train_main_method_3.py # Training (Method 3 only)
├── train_main_method_1_3.py # Training (Method 1 + 3)
├── Traning_model_1_3_bestmodel.py
│
├── report_utils.py # Automated training reports
├── test.py # Model evaluation
│
├── yolov8.pt
├── yolov8s.pt
├── yolov11n.pt
└── .gitignore
```

##  Dataset Engineering & Preprocessing

### 🔹 Class Normalization
**`changeclass.py`**
- Remaps YOLO class IDs to a unified master index
- Required when merging datasets from different annotation standards

---

### 🔹 Label Validation
**`check.py`**
- Verifies YOLO label correctness
- Detects invalid class IDs
- Summarizes object counts per class

---

### 🔹 File Name & Dataset Cleanup
A collection of scripts designed to handle real-world dataset issues:

- Hashes from Roboflow exports
- Duplicate files
- Incorrect label extensions (`.jpg` instead of `.txt`)
- Long or inconsistent filenames

Scripts include:
- `delename_time.py`
- `delete_name.py`
- `delete_image.py`
- `delete_imagejpg.py`
- `delete_imagetxt.py`
- `delete.py`

**Result**
- 1:1 image-label mapping
- No duplicates
- YOLO-ready dataset structure

---

##  Dataset Integration

- Supports merging multiple datasets safely
- Prevents filename collisions
- Preserves original datasets (copy-based integration)

---

##  Automatic Dataset Splitting

Datasets are automatically split into:

- **Train:** 70%
- **Validation:** 15%
- **Test:** 15%

The system checks for existing splits and avoids re-splitting when unnecessary.

---

##  Model Training

### 🔹 YOLOv8 Framework
This project uses **Ultralytics YOLOv8**:

- Official YOLOv8 repository: https://github.com/ultralytics/ultralytics
- Paper reference: *Ultralytics YOLOv8: Next-Generation, Real-Time Object Detection*

YOLOv8 was chosen for:
- Strong performance
- Clean API
- Production-ready training & export tools

---

### 🔹 Training Scripts

 `train_main_method_3.py` 
- Baseline training using Method 3 dataset only
- Used for performance comparison

 `train_main_method_1_3.py`
- Combined training (Method 1 + Method 3)
- Optimized training strategy:
  - Optimizer: **AdamW**
  - Cosine learning rate schedule
  - Warmup epochs
  - Early stopping

`Traning_model_1_3_bestmodel.py`
- Fine-tuning from an existing best model
- Used when datasets are extended or hyperparameters are adjusted

---

##  Experiment Tracking & Reporting

`report_utils.py`

A custom-built training report system that automatically:

- Saves training plots:
  - Confusion Matrix
  - Precision / Recall / F1 curves
  - PR Curve
- Extracts best epoch metrics
- Generates:
  - `TRAINING_REPORT.txt`
  - `summary.json`
- Archives best model checkpoints

This design reflects real-world **ML experiment tracking practices**.

---

##  Model Evaluation

`test.py`

- Evaluates the trained model on the test split
- Reports:
  - mAP50
  - mAP50–95
- Generates evaluation plots for analysis

---

##  Model Export & Deployment Readiness

- Trained models are exported to **ONNX**
- ONNX models are used in the connected deployment repository:
  👉 [ScenerYOne/AI-Model-Deployment-Evaluation-Platform](https://github.com/ScenerYOne/AI-Model-Deployment-Evaluation-Platform)
---

##  Environment & Tools

### 🔹 Programming Language
- Python 3.9+

### 🔹 Core Libraries
- **Ultralytics YOLOv8**
- PyTorch
- OpenCV
- NumPy
- Pandas

### 🔹 Environment Management
- Conda (Anaconda / Miniconda)
- GPU training with NVIDIA CUDA

Example environment setup:
```bash
conda create -n aeroponics-ai python=3.9
conda activate aeroponics-ai
pip install ultralytics opencv-python pandas numpy

```


```text

Image Capture
   ↓
Perspective Transformation
   ↓
Manual YOLO Labeling
   ↓
Dataset Cleaning & Normalization
   ↓
Multi-Dataset Integration
   ↓
Auto Train/Val/Test Split
   ↓
YOLOv8 Training
   ↓
Automated Report Generation
   ↓
Model Evaluation
   ↓
ONNX Export
   ↓
Deployment Platform

```


