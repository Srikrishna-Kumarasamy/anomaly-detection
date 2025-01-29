# Anomaly Detection with Anomalib

This project focuses on anomaly detection for quality control and automated inspection, utilizing the MVTec-AD dataset. The dataset contains various product categories labeled as normal or anomalous. For this assignment, we concentrate on three flat surface categories: **tile**, **leather**, and **grid**.

We leverage the Anomalib library, which provides a streamlined interface for training, evaluating, and visualizing anomaly detection models. The two primary models used are **PatchCore** and **EfficientAD**, each designed to handle different anomaly detection challenges.

## Models Overview

### 1. PatchCore
- Optimized for memory efficiency while maintaining high accuracy.
- Processes images in patches to focus on localized features.
- Uses coresets to retain essential data patterns while reducing memory usage.
- Calculates anomaly scores by comparing patches against the coreset.

### 2. EfficientAD
- Designed for speed and resource efficiency.
- Utilizes a lightweight CNN architecture for quick feature extraction.
- Suitable for real-time applications or environments with limited computational resources.

## Workflow

### 1. Data Preparation
- **Dataset Selection**: Use the `tile`, `leather`, and `grid` categories from the MVTec-AD dataset.
- **Data Loading**: Preprocess images using the Anomalib library for resizing, normalization, or standardization.

### 2. Model Setup and Training
- **PatchCore**: Initialize and train the model on the selected categories.
- **EfficientAD**: Similarly, initialize and train this model for speed-focused anomaly detection.

### 3. Evaluation
- Calculate AUROC scores for each model and category to assess their performance in distinguishing between normal and anomalous samples.

### 4. Similarity Search
- Extract features from a selected category and store them in a Qdrant vector database.
- Use a query image to fetch similar images (normal or anomalous) based on feature similarity.

## Results

| Category | PatchCore AUROC | EfficientAD AUROC |
|----------|------------------|-------------------|
| Tile     | 0.8586           | 0.9636            |
| Leather  | 1.0000           | 0.8798            |
| Grid     | 0.9766           | 0.9808            |

### Key Insights
- PatchCore performs exceptionally well for high-accuracy anomaly detection.
- EfficientAD is optimized for low-resource environments, achieving real-time detection.

## Requirements

- Python 3.8+
- Anomalib library
- Qdrant for similarity search
- PyTorch, NumPy, and other dependencies (refer to `requirements.txt`).

Install dependencies with:
```bash
pip install -r requirements.txt
