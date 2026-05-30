# Phase 2 Notebooks

This folder contains the Phase 2 experiments for the Multimodal Transformer-Based Area Estimation project.

## Structure

| Notebook | Backbone | Parameters |
|----------|----------|------------|
| `SwinV2.ipynb` | Swin Transformer V2 | ~28M |
| `MaxVit.ipynb` | MaxViT | ~31M |

## Overview

Phase 2 establishes the main multimodal experimental framework, extending the proof-of-concept from Phase 1 to the full dataset of 10,000 remote sensing images. Two transformer-based image backbones are evaluated under both image-only and multimodal settings.

## Experiment Structure per Notebook

Each notebook follows the same pipeline:

1. Image-only baseline
2. Multimodal experiments — all three caption types × MiniLM and DistilBERT text encoders at a fixed text scale of 0.7
3. Results summary with class-wise MAE analysis

## Caption Types

Three caption types are evaluated:

| Column | Description |
|--------|-------------|
| `text_qwen3_4b_clean` | Text-only descriptions |
| `hybrid_gemma3_4b_clean` | Hybrid image and text descriptions |
| `vision_gemma3_4b_clean` | Vision-generated descriptions |

All captions are preprocessed to remove numerical values and percentage expressions to prevent label leakage.

## Text Encoders

| Encoder | Type |
|---------|------|
| `sentence-transformers/all-MiniLM-L6-v2` | General-purpose, lightweight |
| `distilbert-base-uncased` | General-purpose, lightweight |

Text encoders are kept frozen during training. Image backbones are initialized with pretrained weights and fine-tuned.

## Fusion Mechanism

Image and text features are combined through a gated fusion mechanism with a learnable gate controlling text contribution. A fixed text scale of 0.7 is applied across all experiments.

## Tracking

All experiments are logged to Weights & Biases under the project `DI725-Project-landcover-regression_phase3_experiments`.
