# BUSI Breast Ultrasound Classification Comparison

## Introduction

This project performs breast ultrasound image classification using the BUSI dataset. The task is to classify each image as benign or malignant. ResNet50, VGG16, and DenseNet121 were trained and evaluated, and this comparison examines their classification performance using the evaluation metrics recorded in the completed experiments.

## Models

### ResNet50

ResNet50 is a convolutional neural network that uses residual connections to help information pass through a deep sequence of layers. The experiment initialized the model with the pretrained ImageNet weights `ResNet50_Weights.IMAGENET1K_V2` before training it on the BUSI classification task.

### VGG16

VGG16 is a convolutional neural network built from a sequence of small convolutional filters arranged in progressively deeper layers. The experiment initialized the model with the pretrained ImageNet weights `VGG16_Weights.IMAGENET1K_V1` before training it on the BUSI classification task.

### DenseNet121

DenseNet121 is a convolutional neural network in which each layer receives feature information from earlier layers through dense connections. The experiment initialized the model with the pretrained ImageNet weights `DenseNet121_Weights.DEFAULT` before training it on the BUSI classification task.

## Experimental Settings

The three models used consistent experimental settings so that their classification performance could be fairly compared.

- Dataset split: predefined BUSI `train.xlsx` and `test.xlsx` files
- Training set: 517 images
- Testing set: 130 images
- Image size: 224 × 224 pixels
- Image format: conversion to RGB
- Preprocessing: resize to 224 × 224, apply `ToTensor`, and normalize using the ImageNet mean `[0.485, 0.456, 0.406]` and standard deviation `[0.229, 0.224, 0.225]`
- Random seed: 42
- Batch size: 16
- Learning rate: 0.0001
- Number of epochs: 10
- Optimizer: Adam
- Loss function: `CrossEntropyLoss`
- Output classes: malignant and benign
- Label mapping: malignant = 0 and benign = 1

## Results

The following table compares the recorded test-set performance of the three models.

| Model | Accuracy | Recall | Precision | F1 Score | AUC |
|---|---:|---:|---:|---:|---:|
| ResNet50 | 0.8692 | 0.84 | 0.85 | 0.84 | 0.8966 |
| VGG16 | 0.8615 | 0.84 | 0.83 | 0.84 | 0.8986 |
| DenseNet121 | 0.9077 | 0.88 | 0.89 | 0.89 | 0.9259 |

**Note:** Precision, Recall, and F1 Score are the macro-average values across the malignant and benign classes from the saved classification reports. Accuracy is calculated across the full test set. AUC comes from `ROC_comparison.ipynb`, where malignant (label 0) was treated as the positive class for the ROC/AUC calculation.

## Findings

DenseNet121 showed the strongest overall performance among the three models, achieving the highest Accuracy, macro-average Recall, macro-average Precision, macro-average F1 Score, and AUC. ResNet50 had slightly higher Accuracy than VGG16, while VGG16 had a slightly higher AUC than ResNet50. The two models had the same recorded macro-average Recall and F1 Score, although ResNet50 had slightly higher macro-average Precision. Overall, DenseNet121 provided the strongest performance across the evaluation metrics used in this comparison.

## Conclusion

ResNet50, VGG16, and DenseNet121 were evaluated for benign-versus-malignant breast ultrasound image classification using the BUSI dataset. Consistent experimental settings were used to support a fair comparison, and all three models demonstrated useful classification performance in the completed experiments. DenseNet121 achieved the strongest overall results across the evaluation metrics used in this comparison. Therefore, among the three models evaluated on the BUSI data in this experiment, DenseNet121 was the best-performing model.
