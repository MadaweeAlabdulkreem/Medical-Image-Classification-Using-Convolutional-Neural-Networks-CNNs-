# Medical-Image-Classification - Skin Lesion Classification using Convolutional Neural Networks

## Project Overview

This project develops a deep learning framework for automatic skin lesion classification using a custom Convolutional Neural Network (CNN). The model classifies dermoscopic images into seven different categories of skin lesions from the HAM10000 dataset.

The objective is to assist in the early detection of melanoma and other skin diseases by providing fast and accurate image classification.

The project includes:

- Data preprocessing and visualization
- Data augmentation for class imbalance
- A custom CNN architecture
- Hyperparameter tuning using K-Fold Cross Validation
- Performance evaluation using multiple classification metrics

---

## Dataset

The project uses the **HAM10000 (Human Against Machine with 10000 Training Images)** dataset.

The dataset contains over **10,000 dermoscopic images** belonging to seven diagnostic classes:

- Melanocytic nevi (nv)
- Melanoma (mel)
- Benign keratosis (bkl)
- Basal cell carcinoma (bcc)
- Actinic keratoses (akiec)
- Vascular lesions (vasc)
- Dermatofibroma (df)

To avoid data leakage, images sharing the same lesion ID are placed in only one dataset split.

🔗 [HAM10000 Dataset](https://www.kaggle.com/datasets/kmader/skin-cancer-mnist-ham10000)

## Data Preprocessing

The preprocessing pipeline includes:

- Removing missing metadata entries
- Mapping image IDs to image paths
- Image resizing to **64×64**
- Pixel normalization to the range [0,1]
- Label encoding and one-hot encoding
- Dataset visualization
- Splitting the dataset by lesion ID
- Data augmentation on the training set only

Data augmentation includes:

- Rotation
- Horizontal flipping
- Zoom
- Width and height shifting
- Shearing

---

## Model Architecture

A custom CNN model was designed instead of using transfer learning.

The architecture consists of:

- Six Convolutional layers
- Batch Normalization
- Max Pooling
- Dropout layers
- Flatten layer
- Two Dense hidden layers
- Softmax output layer for seven-class classification

The network extracts both local and high-level image features while reducing overfitting using Batch Normalization and Dropout.

<img width="1115" height="328" alt="image" src="https://github.com/user-attachments/assets/77e86a29-e483-442d-97dd-3e351e44b52a" />

---

## Training Setup

Training configuration:

- Optimizer: AdamW
- Loss Function: Categorical Crossentropy
- Activation Function: ReLU
- Output Activation: Softmax
- Batch Size: 16
- Epochs: 30
- Learning Rate: 5e-4
- Weight Decay: 1e-5

Early Stopping and Model Checkpoint were used to save the best-performing model.

---

## Hyperparameter Tuning

Model hyperparameters were optimized using **3-Fold Cross Validation**.

The following parameters were explored:

- Learning rate
- Batch size
- Number of epochs
- Optimizer

The best configuration achieved the highest average validation score while maintaining stable training.

<img width="800" height="200" alt="image" src="https://github.com/user-attachments/assets/12b37e90-8ff6-4952-aa00-a0bd4549d5c1" />

---

## Techniques for Reducing Overfitting

Several regularization techniques were applied:

- Data Augmentation
- Batch Normalization
- Dropout
- AdamW Weight Decay
- Early Stopping

These methods significantly improved model generalization.

---

## Evaluation

The model is evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Classification Report
- Confusion Matrix

Performance is analyzed for each of the seven lesion classes.

---

## Results

The final model achieved approximately:

- **Test Accuracy:** 71%

The best performance was observed for the **Melanocytic Nevi (nv)** class, while minority classes such as **Dermatofibroma (df)** and **Actinic Keratoses (akiec)** remained more challenging because of class imbalance.

<img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/8ab3bab8-5b06-4ea0-b626-f49b1b817622" />

---

---
## Output example 
<img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/73b4f097-6c57-4e7e-8929-d1409ae024d2" />

---

## Technologies Used

- Python
- TensorFlow / Keras
- NumPy
- Pandas
- OpenCV
- Matplotlib
- Scikit-learn

---

## Future Improvements

Possible future work includes:

- Applying transfer learning (EfficientNet, ResNet, DenseNet)
- Addressing class imbalance using focal loss
- Increasing image resolution
- Ensemble learning
- Model deployment as a web application

---
