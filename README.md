# SkinNet-HAM10000
Code, notebooks and results for “SkinNet: Leakage-Controlled Multimodal Dermoscopic Image Classification Using EfficientNetB3, CBAM Attention, and Clinical Metadata”: lesion-grouped 5-fold ablation on HAM10000, same-protocol benchmarks and external validation on BCN20000.
SkinNet: Leakage-Controlled Multimodal Dermoscopic Image Classification

Code, notebooks and results for the paper:

Z. Ullah, F. Ullah, M. H. Khan, D. Shah, S. A., M. Tahir. "SkinNet: Leakage-Controlled Multimodal Dermoscopic Image Classification Using EfficientNetB3, CBAM Attention, and Clinical Metadata." Computer Methods in Biomechanics and Biomedical Engineering: Imaging & Visualization (under revision).

Overview

SkinNet combines an EfficientNetB3 image branch (with a convolutional refinement block and CBAM attention) and a clinical-metadata branch (age, sex, anatomical site). The study is a controlled, paired, leakage-audited evaluation:

Lesion-grouped, stratified splits (StratifiedGroupKFold): 1,441-image hold-out test set plus 5 training/validation folds
Ablation of every component: 22 configurations, 117 fold-runs on identical folds
Same-protocol benchmarks: ResNet50, ConvNeXt-Tiny, ViT-B/16
External validation on BCN20000, including out-of-distribution SCC images
Calibration, decision-curve analysis, Grad-CAM/LIME faithfulness, metadata permutation importance and Shapley values

Final model (J, 5-fold ensemble with TTA, HAM10000 test set): macro-F1 0.711 (95% CI 0.649–0.764), balanced accuracy 0.721, macro AUC 0.972, melanoma recall 0.753.

Repository contents
File / folder	Description
notebooks/session-1.ipynb	[AUTHORS: e.g., data audit, preprocessing and splits]
notebooks/session-2.ipynb	[AUTHORS: e.g., ablation configurations A–J]
notebooks/session-3.ipynb	[AUTHORS: e.g., supplementary arms and benchmarks]
notebooks/session-4.ipynb	[AUTHORS: e.g., external validation on BCN20000]
notebooks/session-5.ipynb	[AUTHORS: e.g., calibration, DCA, explainability, final tables and figures]
results/	All result tables (CSV), including fold_metrics_long.csv, ensemble_metrics.csv, posthoc_correction_*.csv
figures/	All figures in the paper
Release assets	Trained weights of all folds, per-fold metadata preprocessors, inference script (see Releases)

All notebooks are saved with their cell outputs, so every reported number can be inspected without re-running.

Datasets (not included)
HAM10000: https://challenge.isic-archive.com/data/#2018
BCN20000 (CC-BY 4.0): https://challenge.isic-archive.com/data/#2019 (labelled training partition only)

Place the data in the paths set at the top of the first notebook (on Kaggle, add the datasets as inputs).

Environment
Python 3.12.13, TensorFlow 2.20.0, Keras 3.13.2
Hardware: 2 × NVIDIA Tesla T4 (Kaggle), mixed precision
Fixed seeds are set in each notebook. GPU training is not bit-wise deterministic; a same-seed re-run is reported in the paper (Section 5.10).
How to reproduce
Open the notebooks in order (session 1 → 5) on Kaggle or a local GPU machine.
Attach the HAM10000 and BCN20000 datasets.
Run all cells. Training is organised in resumable units (one per configuration and fold), so a session can be continued after a time-out.
Citation
[AUTHORS: add the final citation and DOI after publication]
License

[AUTHORS: choose a license, e.g., MIT]

Contact

Zia Ullah: [ziaullahj238@gmail.com]
