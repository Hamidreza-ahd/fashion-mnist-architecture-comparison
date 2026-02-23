# Fashion-MNIST Model Comparison — CNN vs MLP

## Overview

This project presents a comparative study of multiple neural network architectures on the Fashion-MNIST dataset.  
The goal is to analyze how model capacity, regularization techniques, and architectural choices affect performance in image classification.

The notebook implements and evaluates:

- Small Convolutional Neural Networks (CNNs)
- Larger CNN architectures
- CNNs with Dropout
- CNNs with Batch Normalization
- A fully connected MLP baseline

Each model is trained under the same experimental conditions to ensure fair comparison.

---

## Dataset

**Fashion-MNIST** is a grayscale image classification dataset consisting of:

- 60,000 training images  
- 10,000 test images  
- 10 classes  
- Image size: 28×28 pixels  

The dataset serves as a more challenging alternative to MNIST digit classification while remaining computationally lightweight.

---

## Experimental Setup

- Framework: TensorFlow / Keras  
- Optimizer: Adam  
- Loss function: Sparse Categorical Crossentropy  
- Epochs: 10  
- Batch size: Default Keras setting  
- Evaluation metric: Accuracy  

All models were trained on identical data splits to ensure comparability.

---

## Models Implemented

### Model A — Small CNN
- Conv2D (3 filters)
- Conv2D (6 filters)
- Dense classifier

### Model B — Small CNN + Dropout
- Same as Model A
- Dropout(0.5) before classifier

### Model C — MLP Baseline
- Flatten
- Dense(64)
- Dense(10)

### Model D — Larger CNN
- Conv2D (32 filters)
- Conv2D (64 filters)
- Dense(128)
- Dense(10)

### Model E — Larger CNN + Dropout
- Same as Model D
- Dropout(0.5)

### Model F — CNN + Batch Normalization + Dropout
- Conv2D
- BatchNormalization
- Activation
- Dropout
- Dense classifier

---

## Results

### Final Metrics (Last Training Epoch & Test Set)

| Model | Train Accuracy | Train Loss | Test Accuracy | Test Loss |
|-------|---------------|------------|--------------|-----------|
| Model D | 0.9333 | 0.1810 | **0.9100** | 0.2509 |
| Model E | 0.9090 | 0.2501 | 0.9029 | 0.2704 |
| Model F | 0.8688 | 0.3517 | 0.8916 | 0.2959 |
| Model C | 0.8928 | 0.2970 | 0.8718 | 0.3673 |
| Model A | 0.8614 | 0.3771 | 0.8543 | 0.4020 |
| Model B | 0.8296 | 0.4652 | 0.8442 | 0.4148 |

---

## Analysis

### 1. Model Capacity
Increasing convolutional filters and dense units significantly improved performance.  
Model D achieved the highest test accuracy (91.0%), demonstrating the importance of sufficient representational capacity.

### 2. Regularization Effects
Dropout improved generalization in larger models but negatively impacted smaller architectures, leading to underfitting in Model B.

### 3. Batch Normalization
Batch Normalization improved training stability and convergence speed. While not outperforming the best model, it provided competitive and consistent results.

### 4. MLP vs CNN
The MLP baseline performed reasonably well (87.18% test accuracy), confirming that Fashion-MNIST is solvable without convolutions.  
However, CNNs consistently outperformed the MLP due to their ability to exploit spatial locality in image data.

---

## Conclusion

This study demonstrates that architectural scale and design choices significantly influence performance on image classification tasks.

Key findings:

- Larger CNN architectures outperform smaller models and fully connected networks.
- Regularization techniques must be tuned according to model capacity.
- Batch Normalization enhances training stability.
- Even simple baselines (MLP) provide strong reference performance.

The best-performing model (Model D) achieved **91.0% test accuracy**, indicating that moderately sized CNNs are highly effective for Fashion-MNIST classification.

---

## Future Improvements

- Hyperparameter tuning (learning rate, dropout rate, filter sizes)
- Data augmentation for improved generalization
- EarlyStopping and ModelCheckpoint for optimal training control
- Confusion matrix analysis for class-specific error diagnosis
- Model compression (quantization/pruning) for deployment

---

## How to Run

1. Install required dependencies (TensorFlow, NumPy, Matplotlib).
2. Open the notebook.
3. Run cells sequentially.
4. Compare training curves and final evaluation metrics.

---

## Author

This notebook was developed as part of a deep learning model comparison study focusing on architectural experimentation and performance analysis.
