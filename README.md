# Voice-Based Detection of Parkinson's Disease: A Comparative Study of ML and Transfer Learning

This repository contains the official implementation for the paper:

**"A Comparative Study of Machine Learning and Transfer Learning Approaches to Vocal Biomarker Detection in Parkinson’s Disease"**

> **Preprint:** [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.17508693.svg)](https://doi.org/10.5281/zenodo.17508693)  

## Abstract

Parkinson’s disease (PD) affects speech in up to 90% of patients, making voice a promising biomarker for early, non-invasive screening. This study benchmarks voice-based classification frameworks for PD detection across three tiers: classical machine learning (ML) on handcrafted acoustic features, ensemble learning, and transfer learning with convolutional neural networks (CNNs) on spectrograms using MobileNetV2.

Our key findings reveal that:
*   Classical ML models achieve strong performance when age is included as a feature, but performance collapses upon its exclusion, revealing a critical demographic bias.
*   Ensemble methods offer minimal improvements and suffer from instability (high variance) on small datasets.
*   By making PD detection an image classification task, transfer learning with MobileNetV2 outperforms traditional approaches, achieving a best test AUC of **0.896** by learning patterns directly from spectrograms.


## Repository Contents

This repository provides code and scripts to reproduce the experiments in the paper:

*   `ML_Methods/`: Scripts for classical machine learning and ensemble methods.
    *   Feature extraction using OpenSMILE and the GeMAPS feature set.
    *   Implementations of six ML models (LR, SVM, kNN, RF, GB, XGBoost).
    *   Four feature selection techniques (PCA, SelectKBest, RFE, mRMR).
    *   Ensemble learning scripts (Hard/Soft Voting, Stacking).
    *   Relevant visualizations and all
*   `DL_Methods/`: Scripts for the transfer learning approach (MobileNetV2).
    *   Spectrogram generation from raw audio signals.
    *   Data augmentation pipeline.
    *   Fine-tuning and evaluation of the pre-trained MobileNetV2 model.
*   `requirements.txt`: List of python dependencies.

All relevant details and tunable parameters are saved as used in the paper for ease of reproducibility.

### Dataset Used:
can be accessed and downloaded in figshare [here](https://figshare.com/articles/dataset/Voice_Samples_for_Patients_with_Parkinson_s_Disease_and_Healthy_Controls/23849127)

## Citation

If you use this code or find our work helpful, please cite our paper:

```bibtex
@unpublished{balloul2025parkinson,
  author = {Balloul, Mary and Ali, Maram and Ali, Shahd},
  title  = {A Comparative Study of Machine Learning and Transfer Learning Approaches to Vocal Biomarker Detection in Parkinson's Disease},
  institution = {Tartous University},
  note   = {Manuscript in preparation},
  month  = {September},
  year   = {2025},
}
```

## Acknowledgments

This work was supported by the Faculty of Information and Communication Technology Engineering at Tartous University.
