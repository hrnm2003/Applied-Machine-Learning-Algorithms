# Fruit Image Classification

This project implements a binary image classifier to distinguish between apples (Class 0) and bananas (Class 1) using only handcrafted color-based features, without relying on standard machine learning models. The pipeline includes preprocessing, feature extraction, custom metric evaluation, and error analysis.

## Methodology

1. **Preprocessing**: All images are resized to 128x128 pixels to reduce computational complexity while preserving sufficient spatial and color details for threshold-based feature extraction.

2. **Feature Extraction**:
   - **Criterion 1: Majority Color Thresholding**: Creates color range masks to identify red pixels (apple) and yellow pixels (banana). The class with the higher pixel count determines the prediction.
   - **Criterion 2: Average RGB Ratio**: Calculates the mean RGB color of the entire image. A high Red-to-Green ratio (> 1.25) indicates an apple, otherwise a banana.

3. **Performance Metrics**: Custom implementations for confusion matrix, accuracy, and precision are used to evaluate both criteria.

4. **Visualization and Error Analysis**: Random samples are displayed to verify the model, and misclassified images are identified to understand the shortcomings of the logic.

## Results

| Criterion | Accuracy | Precision |
|-----------|----------|-----------|
| Majority Color Thresholding | 90.32% | 96.15% |
| Average RGB Ratio | 79.03% | 72.97% |

The **Majority Color Thresholding** criterion significantly outperforms the Average RGB Ratio method, achieving higher accuracy and precision, indicating it is more reliable for this task.

## Requirements

Install the required packages using:

```bash
pip install -r requirements.txt