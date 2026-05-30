# Phase 3 Notebooks

This folder contains the Phase 3 experiments for the Multimodal Transformer-Based Area Estimation project.

## Structure

| Notebook | Backbone | Parameters |
|----------|----------|------------|
| `DeiT_Tiny.ipynb` | DeiT-Tiny | ~5.7M |
| `SwinV2.ipynb` | Swin Transformer V2 | ~28M |
| `MaxVit.ipynb` | MaxViT | ~31M |

## Relationship to Phase 2

Phase 2 notebooks (`03_phase2/`) established the baseline multimodal experiments using SwinV2 and MaxViT with MiniLM and DistilBERT text encoders across three caption types at a fixed text scale of 0.7. Phase 3 extends those experiments in three ways:

- **New backbone:** DeiT-Tiny is introduced as a weaker transformer baseline to investigate whether lower-capacity image models benefit more from textual information.
- **New text encoder:** RemoteCLIP (ViT-B-32), pretrained on remote sensing data, is added to all three backbones alongside MiniLM and DistilBERT.
- **Text scale ablation:** For each backbone, the best configuration (caption type × text encoder) is selected based on validation MAE, then evaluated across text scale values [ 0.3, 0.5, 0.7, 1.0, 1.5] to analyze sensitivity to text contribution strength. 

Each notebook follows the same pipeline:

1. Image-only baseline
2. Multimodal experiments — all caption types × all text encoders at scale 0.7
3. Best configuration selection based on validation MAE
4. Text scale ablation on the best configuration

## Research Questions

- **RQ1:** Do certain caption types improve regression performance more than others?
- **RQ2:** Do weaker image backbones benefit more from textual information than stronger ones?

## Tracking

All experiments are logged to Weights & Biases:
- Main experiments (scale 0.7): `DI725-Project-landcover-regression_phase3_experiments`
- Text scale ablation: `DI725-Project-landcover-regression_phase3_text_scale_exp`
