# DI725 Project
# Multimodal Land Cover Regression (Image + Text)

This project investigates whether incorporating textual descriptions improves land-cover area estimation compared to image-only models, and how model capacity influences the benefit of multimodal fusion.

## Overview

We extend a unimodal image-based regression framework to a multimodal setting by integrating textual captions with images. The goal is to predict land-cover area proportions across seven classes: Tree, Shrub, Grass, Crop, Built-up, Barren, and Water.

## Methodology

### Models
Two vision transformer backbones are used:
- SwinV2 (moderate capacity)
- MaxViT (higher capacity)

### Multimodal Fusion
Text and image features are combined using a gated fusion mechanism:
- Text is encoded using MiniLM and DistilBERT
- Text encoders are frozen during training
- Text features are projected into the image feature space
- A learnable gate and scaling factor control text contribution

### Caption Types
Three caption sources are evaluated:
- text_qwen3-4b (text-only)
- hybrid_gemma3-4b (hybrid)
- vision_gemma3-4b (vision-based)

### Data Processing
- Captions are cleaned to remove numerical values and prevent label leakage
- Dataset split: 80% train, 10% validation, 10% test (stratified)

## Results

Text improves performance when captions are informative. Text-only captions consistently perform best, while vision-based captions provide little or no improvement.

SwinV2 benefits more from textual information than MaxViT, indicating that weaker models rely more on multimodal inputs, while stronger models already capture richer visual representations.

## Evaluation

Metrics used:
- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- Class-wise MAE

## Experiments

Experiments vary:
- Vision backbone
- Text encoder
- Caption type
- Multimodal vs image-only setup

All experiments use consistent training settings (learning rate, batch size, epochs, and random seed).

## Future Work

- Evaluate additional image and text models  
- Tune text scaling factor  

## Repository Structure

    data/

    notebooks/
        01_eda/
            DI725_Term_Project_EDA_244...
            README.md
        02_poc/
            DEIT_Proof_of_Concept_DI725...
            Resnet_Proof_of_Concept_DI7...
            SWIN_Proof_of_Concept_DI72...
            README.md
        03_phase2/
            SWIN_V2.ipynb
            MaxVit.ipynb
            README.md

    reports/
    results/

    README.md
    requirements.txt

## Notes

- Text encoders are frozen
- Image backbones are pretrained and fine-tuned
- Experiments are reproducible via fixed seeds

## Author

Ayse — Data Informatics Student
