# Exploratory Data Analysis

This notebook performs a preliminary EDA on the multimodal land cover dataset prior to model training.

## What is covered

- **Class distribution analysis** — mean and boxplot of land cover proportions across all seven classes, revealing that Grass and Crop are dominant while Built-up and Water are underrepresented
- **Caption analysis** — word length distributions across all five caption sources (hybrid, text-only, vision-based), showing variability in descriptive detail across caption types
- **Subset creation** — a stratified 500-sample subset is created from the full dataset using dominant-class proportions, confirmed to preserve the original class distribution within ~1% difference

## Outputs
- `captions_subset.csv` — a representative 500-sample subset saved to Google Drive, used in early-stage experiments
