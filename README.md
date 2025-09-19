# Kidney Detection using DenseNet201 with Progressive Fine-Tuning Pipeline and Bayesian Optimiztion

> **Progressive fine-tuning pipeline with class-weight balancing by Bayesian optimization and Test-Time Augmentation (TTA) achieving up to 99.9199% accuracy**

[![License](https://img.shields.io/badge/License-Proprietary-red.svg)](LICENSE_KIDNEY_CLASSIFICATION.txt)
[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)](https://tensorflow.org)
[![Status](https://img.shields.io/badge/Status-Research%20Complete-green.svg)]()

## Author & Academic Context

**Ziad M. Amer** | Student ID: 20240219  
📧 ziadmoamer@gmail.com | 🌐 [ziadamer.com](https://ziadamer.com)

**Academic Affiliation:**
- 🎓 Bachelor in Computer Science (Artificial Intelligence)
- 🏛️ Faculty of Computers and Artificial Intelligence, Cairo University
- 👩‍🏫 Supervisor: Dr. Elham Shawky
- 📅 Development: August 2025 - September 2025

---

## What This Project Does

This research introduces a **progressive fine-tuning methodology** for automatically diagnosing kidney diseases from CT scans. 
Unlike conventional fine-tuning, this pipeline incrementally unlocks model capacity, then applies **class-weight balancing by Bayesian optimization** to address dataset imbalance before performing ensemble-style Test-Time Augmentation.

### The Problem We Solved
- Manual kidney disease diagnosis is time-consuming and subjective
- Traditional AI models struggle with medical imaging nuances
- Existing approaches often fail to achieve clinical-grade accuracy
- Need for automated, reliable diagnostic assistance

### Our Innovation
- **Progressive Fine-Tuning Pipeline:** Feature extraction → selective fine-tuning → ultra fine-tuning → class-weight optimized ultra refinement
- **Class Imbalance Mitigation:** Automated computation + Bayesian search of weighting space
- **Medical-Optimized Preprocessing:** Custom HU windowing + CLAHE enhancement
- **TestTime Augmentation:** 5-strategy ensemble for maximum accuracy
- **CPU-Friendly Implementation:** Accessible without expensive GPU hardware

---

## Key Results

| Metric | Achievement |
|--------|-------------|
| **Accuracy (TTA)** | **99.9199%** |
| **Accuracy (Standard Inference)** | 97.99% |
| **Dataset** | 12,446 CT images |
| **Classes** | Normal, Cyst, Stone, Tumor |
| **Overall Epoch Budget** | ~30 effective epochs (early stopping per step) |
| **Hardware** | CPU-optimized |

### Performance Breakdown
- **Step 1 (Feature Extraction):** Rapid convergence to ~91–97% val accuracy (classification head only)
- **Step 2 (Selective Fine-tuning - last 30 layers):** Stability + representation refinement (~97–98.5%)
- **Step 3 (Ultra Fine-tuning - last 50 layers):** Higher domain adaptation (~99.2% peak val)
- **Class-Weight Balacing By Bayesian Optimization:** Imbalance-aware refinement, stable generalization
- **+ Test-Time Augmentation (5-view ensemble):** **99.9199% final accuracy**

---

## Technical Innovation

### Progressive Fine-Tuning Pipeline
```
Step 1: Feature Extraction
  - Freeze all DenseNet201 layers
  - Train only classification head
  - Establish domain alignment

Step 2: Selective Fine-tuning
  - Unfreeze last 30 layers
  - LR = 1e-5 (conservative)
  - Refine high-level discriminative blocks

Step 3: Ultra Fine-tuning
  - Unfreeze last 50 layers
  - LR = 5e-6 (ultra conservative)
  - Deep adaptation to medical texture statistics

Class-Weight Balacing By Bayesian Optimization
  - Compute per-class weights (inverse frequency / smoothed)
  - Bayesian search over weight scaling
  - Short controlled refinement (few epochs)
  - Stabilize minority-class sensitivity

Inference Enhancement: Test-Time Augmentation (5-policy ensemble averaging)
```

### Medical Image Preprocessing Pipeline
1. **HU Windowing:** Optimize for kidney tissue contrast
2. **CLAHE Enhancement:** Adaptive histogram equalization
3. **Normalization:** Stable neural network input
4. **Augmentation:** Medical-imaging appropriate transforms

### Test-Time Augmentation Strategy
- Base prediction (no augmentation)
- Horizontal flip variations
- Small rotation adjustments  
- Zoom perturbations
- Position shifts
- **Ensemble averaging** for final prediction

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
4. **Open the notebook:** `Fine-Tuned_Optimized_TTA_DenseNet201_Kidney_Detection.ipynb`
5. **Run cells sequentially** to reproduce results

### CPU-Friendly Design
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

### Research Contributions
1. **Progressive Fine-Tuning Pipeline:** Adds imbalance-aware optimization beyond conventional multi-phase fine-tuning
2. **Medical Image Optimization:** Custom HU + CLAHE pipeline tailored to kidney parenchyma contrast dynamics
3. **High Accuracy Achievement:** 99.9199% (TTA) surpassing typical DenseNet baselines on this task
4. **Imbalance Mitigation:** Integrated class-weight computation and search improves minority recall
5. **Accessibility Focus:** CPU-based reproducibility for low-resource academic settings

### Publication Plans
This research is being prepared for journal submission with focus on:
- Medical imaging conference presentations
- AI in healthcare publications
- Open-source medical AI initiatives

### Why This Matters
- **Clinical Applications:** Potential diagnostic assistance tool
- **Educational Value:** Demonstrates advanced undergraduate research capabilities
- **Technical Innovation:** Novel approach applicable to other medical imaging tasks
- **Accessibility:** Makes advanced medical AI more accessible

---

## How to Cite

If you use this work in your research, please cite:

```bibtex
@mastersthesis{amer2025kidney,
  title={Progressive Fine-Tuning Pipeline with Class-Weight Balancing By Bayesian Optimization (CW3BO) and TTA for Kidney CT Classification using DenseNet201},
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

**🤝 Interested in Collaboration?**
- 📧 **Email:** ziadmoamer@gmail.com
- 🌐 **Website:** [ziadamer.com](https://ziadamer.com)
- 🎓 **Academic Supervisor:** Dr. Elham Shawky (FCAI Cairo University)

**💡 Open to:**
- Research collaborations
- Journal co-authorship opportunities
- Medical AI consultations
- Educational partnerships

---

## License & Usage

**📋 Academic Use:** This research is available for academic review and evaluation. 

**🚫 Commercial Use:** Prohibited without explicit permission.

**📚 Citation Required:** Please use proper attribution for any academic reference.

**📄 Full Terms:** See [LICENSE_KIDNEY_CLASSIFICATION.txt](LICENSE_KIDNEY_CLASSIFICATION.txt)

---

## Acknowledgments

- **Dr. Elham Shawky** for academic supervision and guidance
- **Faculty of Computers and Artificial Intelligence, Cairo University** for research support
- **Open Source Community** for providing excellent tools and frameworks
- **Medical Imaging Community** for inspiration and domain knowledge

---

## Final Note

This project represents the culmination of intensive undergraduate research, demonstrating that high-impact medical AI research can be conducted with dedication, creativity, and resourcefulness. The novel fine-tuning methodology (feature extraction → progressive unfreezing → deep adaptation → imbalance-aware refinement) opens new possibilities for medical image classification.

**Developed to advance accessible, reliable medical AI**

---

*© 2025 Ziad M. Amer. This project is protected under intellectual property rights while being shared for academic advancement.*








