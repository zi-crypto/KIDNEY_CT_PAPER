# Kidney CT Classification using DenseNet201 with Three-Stage Progressive Training

> **Novel deep learning approach achieving 99.76% accuracy in kidney disease classification from CT scans**

[![License](https://img.shields.io/badge/License-Proprietary-red.svg)](LICENSE_KIDNEY_CLASSIFICATION.txt)
[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)](https://tensorflow.org)
[![Status](https://img.shields.io/badge/Status-Research%20Complete-green.svg)]()

## Author & Academic Context

**Ziad M. Amer** | Student ID: 20240219  
Email: ziadmoamer@gmail.com | Website: [ziadamer.com](https://ziadamer.com)

**Academic Affiliation:**
- Bachelor in Computer Science (Artificial Intelligence)
- Faculty of Computers and Artificial Intelligence, Cairo University
- Supervisor: Dr. Elham Shawky
- Development: August 2025 - September 2025

---

## What This Project Does

This research introduces a **revolutionary three-stage progressive training methodology** for automatically diagnosing kidney diseases from CT scans. Instead of traditional transfer learning approaches, we developed a smart strategy that gradually "awakens" different parts of the neural network, achieving unprecedented accuracy in medical image classification.

### **The Problem We Solved**
- Manual kidney disease diagnosis is time-consuming and subjective
- Traditional AI models struggle with medical imaging nuances
- Existing approaches often fail to achieve clinical-grade accuracy
- Need for automated, reliable diagnostic assistance

### **Our Innovation**
- **Novel 3-Stage Training:** Progressive layer unfreezing strategy
- **Medical-Optimized Preprocessing:** Custom HU windowing + CLAHE enhancement
- **Test Time Augmentation:** 5-strategy ensemble for maximum accuracy
- **CPU-Friendly Implementation:** Accessible without expensive GPU hardware

---

## Key Results

| Metric | Achievement |
|--------|-------------|
| **Accuracy** | **99.76%** (with TTA) |
| **Dataset** | 12,446 CT images |
| **Classes** | Normal, Cyst, Stone, Tumor |
| **Training Time** | ~30 epochs total |
| **Hardware** | CPU-optimized |

### Performance Breakdown
- **Stage 1 (Feature Extraction):** ~97% accuracy
- **Stage 2 (30-layer Fine-tuning):** ~98.5% accuracy  
- **Stage 3 (50-layer Ultra Fine-tuning):** ~99.2% accuracy
- **+ Test Time Augmentation:** **99.76% final accuracy**

---

## Technical Innovation

### **Three-Stage Progressive Training**
```
Stage 1: Feature Extraction
├── Freeze all DenseNet201 layers
├── Train only classification head
└── Learn domain-specific features

Stage 2: Selective Fine-tuning  
├── Unfreeze last 30 layers
├── Conservative learning rate (1e-5)
└── Refine high-level features

Stage 3: Ultra Fine-tuning
├── Unfreeze last 50 layers  
├── Ultra-conservative rate (5e-6)
└── Perfect medical imaging adaptation
```

### **Medical Image Preprocessing Pipeline**
1. **HU Windowing:** Optimize for kidney tissue contrast
2. **CLAHE Enhancement:** Adaptive histogram equalization
3. **Normalization:** Stable neural network input
4. **Augmentation:** Medical-imaging appropriate transforms

### **Test Time Augmentation Strategy**
- Base prediction (no augmentation)
- Horizontal flip variations
- Small rotation adjustments  
- Zoom perturbations
- Position shifts
- **Ensemble averaging** for final prediction

---

## Project Structure

```
Kidney_CT_Classification/
├── Kidney_CT_Classification_DenseNet201_ThreeStage_TTA.ipynb  # Main research notebook
├── LICENSE_KIDNEY_CLASSIFICATION.txt                         # Usage terms
├── README_IP_NOTICE.txt                                      # IP documentation  
├── CITATION_TEMPLATE.txt                                     # Academic citations
├── README.md                                                 # This file
├── CT-KIDNEY-DATASET-Normal-Cyst-Tumor-Stone/              # Dataset
├── Results/DenseNet201/                                      # Model outputs
└── weights/                                                  # Pre-trained weights
```

---

## Getting Started

### Prerequisites
- Python 3.8+
- TensorFlow 2.x
- NumPy, Pandas, Matplotlib
- OpenCV, Scikit-learn
- Sufficient RAM (8GB+ recommended)

### Quick Start
1. **Clone/Download** this repository
2. **Install dependencies:** `pip install tensorflow numpy opencv-python scikit-learn matplotlib seaborn`
3. **Download dataset** and place in correct directory structure
4. **Open the notebook:** `Kidney_CT_Classification_DenseNet201_ThreeStage_TTA.ipynb`
5. **Run cells sequentially** to reproduce results

### **CPU-Friendly Design**
This implementation is optimized for CPU training, making it accessible without expensive GPU hardware. Training time is reasonable even on standard laptops.

---

## Dataset Information

**CT Kidney Dataset Features:**
- **Total Images:** 12,446 high-quality CT scans
- **Classes:** 4 categories (Normal, Cyst, Stone, Tumor)
- **Split:** 80% train, 10% validation, 10% test
- **Resolution:** 224×224 pixels (standardized)
- **Format:** JPG images with clear labeling

**Class Distribution:**
- Normal kidneys: ~3,700 images
- Kidney cysts: ~3,200 images  
- Kidney stones: ~2,300 images
- Kidney tumors: ~3,300 images

---

## Academic Impact

### **Research Contributions**
1. **Novel Training Methodology:** First application of progressive layer unfreezing to kidney CT classification
2. **Medical Image Optimization:** Custom preprocessing pipeline for kidney-specific enhancement
3. **High Accuracy Achievement:** 99.76% accuracy surpasses existing literature
4. **Accessibility Focus:** CPU-based implementation democratizes advanced medical AI

### **Publication Plans**
This research is being prepared for journal submission with focus on:
- Medical imaging conference presentations
- AI in healthcare publications
- Open-source medical AI initiatives

### **Why This Matters**
- **Clinical Applications:** Potential diagnostic assistance tool
- **Educational Value:** Demonstrates advanced undergraduate research capabilities
- **Technical Innovation:** Novel approach applicable to other medical imaging tasks
- **Accessibility:** Makes advanced medical AI more accessible

---

## How to Cite

If you use this work in your research, please cite:

```bibtex
@mastersthesis{amer2025kidney,
  title={Novel Three-Stage Progressive Training for Kidney CT Classification using DenseNet201 with Test Time Augmentation},
  author={Amer, Ziad M.},
  year={2025},
  school={Faculty of Computers and Artificial Intelligence, Cairo University},
  type={Bachelor's Thesis},
  supervisor={Dr. Elham Shawky},
  month={September}
}
```

---

## Contact & Collaboration

**Interested in Collaboration?**
- **Email:** ziadmoamer@gmail.com
- **Website:** [ziadamer.com](https://ziadamer.com)
- **Academic Supervisor:** Dr. Elham Shawky (FCAI Cairo University)

**Open to:**
- Research collaborations
- Journal co-authorship opportunities
- Medical AI consultations
- Educational partnerships

---

## License & Usage

**Academic Use:** This research is available for academic review and evaluation. 

**Commercial Use:** Prohibited without explicit permission.

**Citation Required:** Please use proper attribution for any academic reference.

**Full Terms:** See [LICENSE_KIDNEY_CLASSIFICATION.txt](LICENSE_KIDNEY_CLASSIFICATION.txt)

---

## Acknowledgments

- **Dr. Elham Shawky** for academic supervision and guidance
- **Faculty of Computers and Artificial Intelligence, Cairo University** for research support
- **Open Source Community** for providing excellent tools and frameworks
- **Medical Imaging Community** for inspiration and domain knowledge

---

## Final Note

This project represents the culmination of intensive undergraduate research, demonstrating that high-impact medical AI research can be conducted with dedication, creativity, and resourcefulness. The novel three-stage methodology opens new possibilities for medical image classification and showcases the potential of student-led innovation in healthcare technology.

**Made with care for advancing medical AI accessibility**

---

*© 2025 Ziad M. Amer. This project is protected under intellectual property rights while being shared for academic advancement.*
