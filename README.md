# Mushroom Classification with Deep Learning

## Overview

This project focuses on building a deep learning model to classify mushrooms into nine genera based on their visual features. The model uses images of mushrooms to identify their classes, leveraging transfer learning and fine-tuning techniques. Mushroom classification is important for various real-world applications, such as:
- **Foraging Safety**: Identifying edible vs. toxic mushrooms.
- **Biodiversity Studies**: Supporting mycologists in cataloging and studying fungi species.
- **Agriculture**: Detecting mushroom species for commercial cultivation.

## Objective

The primary objective is to train a robust and accurate image classification model that:
- Accurately predicts the genus of a given mushroom image.
- Handles challenges such as class imbalance and natural variations in image orientation, lighting, and quality.
- Provides insights into the classification performance for individual mushroom classes.

---

## Dataset Description

The dataset consists of images of mushrooms classified into the following 9 genera:
1. **Agaricus** (Mixed edibility, includes edible and toxic species)
2. **Amanita** (Mostly toxic, includes deadly poisonous mushrooms)
3. **Boletus** (Mostly edible but includes mildly toxic species)
4. **Cortinarius** (Mostly inedible or toxic)
5. **Entoloma** (Mostly toxic)
6. **Hygrocybe** (Mostly inedible, colorful mushrooms)
7. **Lactarius** (Mixed edibility)
8. **Russula** (Mixed edibility)
9. **Suillus** (Mostly edible)

---

## Modeling Approach

### Transfer Learning with ResNet-18
The project leverages a pre-trained ResNet-18 backbone, fine-tuned for mushroom classification. The transfer learning approach provides:
- Faster convergence by leveraging learned features from ImageNet.
- Improved performance with limited data.

### Fine-Tuning
The model undergoes staged fine-tuning:
- Initial training of the classification head while freezing the backbone.
- Gradual unfreezing of layers in the backbone for fine-tuning.

---

## Data Augmentation and Preprocessing

To handle the variability in mushroom images and improve generalization, the following transformations were applied:
- **Training Data**:
  - `RandomHorizontalFlip`
  - `RandomRotation(15°)`
  - `CenterCrop`
  - `Normalization`
- **Validation and Test Data**:
  - Resized to `224x224 pixels`
  - `CenterCrop`
  - `Normalization`

Class imbalance was addressed by weighting the loss function based on class frequencies.

---

## Model Evaluation

### Metrics
The following metrics were used to evaluate the model:
- **Accuracy**: Overall proportion of correctly classified images.
- **Class-Wise Metrics**: Precision, recall, and F1-score for each class.
- **Confusion Matrix**: Visual representation of class-specific misclassifications.
- **Inference Time**: Average time to classify a single image.

### Results
- **Overall Accuracy**: 83%
- **Key Observations**:
  - Strong performance for classes with adequate representation (e.g., **Boletus**, **Amanita**).
  - Challenges with minority classes like **Entoloma** and **Suillus**, due to limited samples.

---

## How to Run the Project

1. **Clone the Repository**:

2. **Install Dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

3. **Execute Jupyter notebook**:

---

## Visualizations and Insights

### Learning Curves
Loss and accuracy plots are provided to track the model's performance over epochs.

### Class-Wise Accuracy
A breakdown of the accuracy achieved for each mushroom genus highlights areas of strength and potential improvement.

---

## Limitations and Future Work

- **Class Imbalance**: Some classes have significantly fewer samples, affecting model performance.
- **Dataset Quality**: Variations in image quality and subject can introduce noise.

**Future Work**:
1. Expand the dataset with more diverse and balanced samples.
2. Experiment with larger models (e.g., ResNet-50) for improved feature extraction.
3. Implement additional techniques such as class-specific data augmentation or semi-supervised learning.

---

## License

This project is licensed under the MIT License.

---
