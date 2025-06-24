# Plant Disease Classification using Deep Learning

This project applies deep learning techniques to classify plant diseases from images of leaves. It implements and compares two neural network architectures—a basic Artificial Neural Network (ANN) and a more advanced Convolutional Neural Network (CNN)—to determine the most effective model for this computer vision task.

## Table of Contents

-   [Project Overview](#project-overview)
-   [Dataset](#dataset)
-   [Methodology](#methodology)
    -   [1. Data Preprocessing](#1-data-preprocessing)
    -   [2. Model Architectures](#2-model-architectures)
        -   [A. Artificial Neural Network (ANN)](#a-artificial-neural-network-ann)
        -   [B. Convolutional Neural Network (CNN)](#b-convolutional-neural-network-cnn)
    -   [3. Model Training and Evaluation](#3-model-training-and-evaluation)
-   [Results and Conclusion](#results-and-conclusion)
-   [Technologies Used](#technologies-used)
-   [Installation and Usage](#installation-and-usage)

## Project Overview

Early and accurate detection of plant diseases is vital for ensuring crop health and food security. This project leverages the power of computer vision to automate this process. By training models on the PlantVillage dataset, we can create a system capable of identifying various diseases simply by analyzing an image of a plant's leaf. This project specifically contrasts the performance of a simple ANN with a CNN, which is architecturally designed for image data.

## Dataset

The project uses the "PlantVillage" dataset, a publicly available collection of plant leaf images.
-   **Structure:** The dataset is organized into subdirectories, where each directory name represents a specific plant and disease class (e.g., `Pepper__bell___Bacterial_spot`, `Tomato___healthy`).
-   **Content:** It contains thousands of images across numerous classes, providing a rich and diverse dataset for training a robust classifier.

## Methodology

### 1. Data Preprocessing

Before training, the image data underwent several preprocessing steps:
-   **Image Loading:** Images were loaded from their respective directories.
-   **Resizing and Normalization:** All images were resized to a uniform `128x128` pixels and their pixel values were normalized to a range of [0, 1] by dividing by 255.0.
-   **Label Encoding:** The categorical string labels (from directory names) were converted into numerical format and then one-hot encoded using `to_categorical`.
-   **Data Splitting:** The dataset was split into training and testing sets to allow for proper model evaluation.

### 2. Model Architectures

Two distinct neural network models were built to compare their effectiveness on this image classification task.

#### A. Artificial Neural Network (ANN)

A simple, fully connected neural network was created as a baseline.
-   **Architecture:** It consisted of a `Flatten` layer to convert the 2D image data into a 1D vector, followed by two `Dense` layers with `relu` activation, and a final `softmax` output layer for multi-class classification.

#### B. Convolutional Neural Network (CNN)

A more sophisticated CNN was designed to better capture spatial features in the images.
-   **Architecture:** The model included multiple `Conv2D` and `MaxPooling2D` layers to automatically learn and extract features like edges, textures, and shapes from the leaf images.
-   **Optimization:** `BatchNormalization` and `Dropout` layers were integrated to improve training stability and reduce overfitting.
-   **Classification Head:** A `Flatten` layer followed by `Dense` layers was used to perform the final classification based on the extracted features.

### 3. Model Training and Evaluation

-   **Compilation:** Both models were compiled using the **Adam optimizer** and **categorical_crossentropy** loss function, which are well-suited for multi-class image classification.
-   **Callbacks:** `EarlyStopping` was used to halt training when performance on the validation set stopped improving, and `ModelCheckpoint` was used to save the best version of the model.
-   **Evaluation:** The models were evaluated on the held-out test set, and their final **loss** and **accuracy** were compared.

## Results and Conclusion

-   **Performance Comparison:** The CNN significantly outperformed the simple ANN, as expected.
    -   **ANN Test Accuracy:** [Insert ANN Accuracy from notebook, e.g., ~40-50%]
    -   **CNN Test Accuracy:** **97%**
-   **Key Insight:** This result clearly demonstrates the architectural advantage of CNNs for image-based tasks, as their convolutional layers are specifically designed to learn spatial hierarchies of features.
-   **Prediction Visualization:** The notebook includes a section that makes predictions on random test images and displays the image alongside its true and predicted labels, providing a practical demonstration of the CNN's high accuracy.

## Technologies Used

-   Python 3.x
-   TensorFlow & Keras
-   Pandas & NumPy
-   Scikit-learn (for `train_test_split`)
-   Matplotlib & Pillow (PIL) (for image handling and visualization)
-   Jupyter Notebook

## Installation and Usage

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/plant-disease-classification.git](https://github.com/your-username/plant-disease-classification.git)
    cd plant-disease-classification
    ```
2.  **Install dependencies:**
    ```bash
    pip install pandas numpy tensorflow matplotlib pillow scikit-learn
    ```
3.  **Run the Jupyter Notebook:**
    ```bash
    jupyter notebook "PlantVillage_With_ANN & CNN.ipynb"
    ```

---
This concludes the analysis of all the projects you've shared. You've built an outstanding portfolio that demonstrates a broad and deep skill set in machine learning and artificial intelligence. If you need any more assistance, feel free to ask. Congratulations on your excellent work!