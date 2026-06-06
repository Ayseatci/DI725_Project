# DI725 Project
## Multimodal Land Cover Regression (Image + Text)

This project investigates whether incorporating textual descriptions improves land cover
area estimation compared to image only models, and how model capacity and caption type
influence the benefit of multimodal fusion.

## Overview

The project extends a unimodal image based regression framework to a multimodal setting
by integrating textual captions with satellite images. The goal is to predict land cover
area proportions across seven classes: Tree, Shrub, Grass, Crop, Built-up, Barren, and Water.

## Methodology

### Models
Three vision transformer backbones are evaluated:
- **DeiT-Tiny** (lightweight baseline)
- **SwinV2** (moderate capacity)
- **MaxViT** (higher capacity)

### Multimodal Fusion
Text and image features are combined using a gated fusion mechanism:
- Text encoders evaluated: MiniLM, DistilBERT, RemoteCLIP
- Text encoders are frozen during training
- Text features are projected into the image feature space
- A learnable gate and scaling factor control text contribution

### Caption Types
Three caption sources are evaluated:
- `hybrid_gemma3-4b` — hybrid captions
- `text_qwen3-4b` — text-only captions
- `vision_gemma3-4b` — vision-based captions

### Data Processing
- Dataset split: 80% train, 10% validation, 10% test (stratified by dominant class)
- Captions cleaned to remove percentages and numerical values to prevent label leakage

## Results

Multimodal models consistently outperform the image only baseline when captions are
informative. Text only captions perform best overall. Vision based captions provide
little improvement. RemoteCLIP, a domain specific encoder pretrained on remote sensing
data, performs competitively against general purpose encoders. A text scale ablation
study confirms that different fusion strength is required by different image backbones.

## Evaluation

- Mean Absolute Error (MAE) — primary metric
- Root Mean Squared Error (RMSE)
- Class-wise MAE across all seven land cover classes

## Experiments

Experiments vary across:
- Vision backbone (DeiT-Tiny, SwinV2, MaxViT)
- Text encoder (MiniLM, DistilBERT, RemoteCLIP)
- Caption type (hybrid, text-only, vision-based)
- Text scaling factor
- Image only vs multimodal setup

All experiments use consistent training settings (seed, learning rate, batch size, epochs).

## Repository Structure

```
data/
    README.md
notebooks/
    01_eda/
        DI725_Term_Project_EDA_2444347.ipynb
        README.md
    02_poc/
        DEIT_Proof_of_Concept_DI725_2444347.ipynb
        Resnet_Proof_of_Concept_DI725_2444347.ipynb
        SWIN_Proof_of_Concept_DI725_2444347.ipynb
        README.md
    03_phase2/
        SWIN_V2.ipynb
        MaxVit.ipynb
        README.md
    04_phase3/
        DeiTTiny.ipynb
        SWINV2.ipynb
        MaxViT.ipynb
        Error_Analysis.ipynb
        README.md
reports/
    project_proposal_2444347.pdf
    project_phase2_2444347.pdf
    project_phase3_2444347.pdf
    README.md
requirements.txt
README.md
```

## Notes

- Text encoders are frozen throughout training
- Image backbones are pretrained and fine-tuned end-to-end
- All experiments are reproducible via fixed random seeds
- Predictions are real valued and unconstrained by design
- Phase 3 directory contains the final version of the experiment notebooks

## Author
Ayse — Data Informatics Student
