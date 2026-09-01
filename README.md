# Diabetic Retinopathy Prediction Using Machine Learning

## 📌 Project Overview

Diabetic Retinopathy Prediction is a machine learning project that uses retinal fundus images to classify whether **Diabetic Retinopathy (DR)** is detected.

The project uses **Python and TensorFlow/Keras** to preprocess retinal images, train a Convolutional Neural Network (CNN), evaluate its performance, and predict the presence or absence of diabetic retinopathy from new retinal images.

The original dataset contains five diagnostic categories:

* No_DR
* Mild
* Moderate
* Severe
* Proliferate_DR

For the prediction task, these categories are converted into a **binary classification problem**:

* `No_DR` → Diabetic Retinopathy Not Detected
* `Mild`, `Moderate`, `Severe`, `Proliferate_DR` → Diabetic Retinopathy Detected

---

## 🎯 Objectives

* Analyze and preprocess retinal image data.
* Convert multi-class diabetic retinopathy labels into binary classes.
* Split the dataset into training, validation, and testing sets.
* Build a CNN-based image classification model.
* Train the model using TensorFlow/Keras.
* Evaluate model performance on test data.
* Save the trained model for future predictions.
* Predict diabetic retinopathy from new retinal images.

---

## 🛠️ Technologies Used

| Technology                      | Purpose                          |
| ------------------------------- | -------------------------------- |
| Python                          | Programming language             |
| Pandas                          | Dataset loading and manipulation |
| NumPy                           | Numerical operations             |
| TensorFlow                      | Machine learning framework       |
| Keras                           | CNN model development            |
| OpenCV                          | Image processing                 |
| Matplotlib                      | Data and image visualization     |
| Scikit-learn                    | Dataset splitting                |
| Jupyter Notebook / Google Colab | Development environment          |

---

## 📂 Project Structure

```text
Diabetic-Retinopathy-Prediction/
│
├── diabetic_retinopathy.ipynb
├── 64x3-CNN.model
├── README.md
│
└── input/
    └── diabetic-retinopathy-224x224-gaussian-filtered/
        ├── train.csv
        └── gaussian_filtered_images/
```

> The dataset and trained model may not be included in the GitHub repository because of their size. See the Dataset section for details.

---

## 📊 Dataset

The project uses the **Diabetic Retinopathy 224x224 Gaussian Filtered** dataset.

The dataset contains retinal fundus images and corresponding diagnosis labels.

The CSV file contains information including:

* `id_code`
* `diagnosis`

The diagnosis values range from:

```text
0 → No_DR
1 → Mild
2 → Moderate
3 → Severe
4 → Proliferate_DR
```

For binary classification, the project maps the labels as follows:

```text
0 → No_DR
1 → DR
2 → DR
3 → DR
4 → DR
```

This allows the model to perform binary classification between:

```text
No Diabetic Retinopathy
          vs
Diabetic Retinopathy
```

---

## 🔄 Project Workflow

```text
Dataset
   ↓
Load CSV
   ↓
Map Diagnosis Labels
   ↓
Data Exploration
   ↓
Train / Validation / Test Split
   ↓
Image Organization
   ↓
Image Resizing & Normalization
   ↓
CNN Model
   ↓
Model Training
   ↓
Model Evaluation
   ↓
Save Trained Model
   ↓
New Image Prediction
```

---

## 🧹 Data Preprocessing

The project performs the following preprocessing steps:

1. Loads the dataset using Pandas.
2. Maps the original diagnosis values to diagnostic categories.
3. Creates binary classification labels.
4. Splits the dataset into:

   * Training data
   * Validation data
   * Testing data
5. Organizes images into corresponding class directories.
6. Resizes images to:

```text
224 × 224
```

7. Normalizes pixel values using:

```python
1./255
```

---

## 🧠 CNN Model

A Convolutional Neural Network is used for retinal image classification.

The architecture includes:

* Convolutional layers
* Max Pooling layers
* Batch Normalization
* Flatten layer
* Dense layers
* Dropout
* Softmax output layer

The model uses an input image size of:

```text
224 × 224 × 3
```

The final layer contains two output classes for binary classification.

### Model Configuration

```text
Optimizer: Adam
Learning Rate: 1e-5
Output Classes: 2
Epochs: 15
Activation: ReLU / Softmax
```

---

## 📈 Model Training

The model is trained using the training dataset and validated using the validation dataset.

Example training process:

```python
history = model.fit(
    train_batches,
    epochs=15,
    validation_data=val_batches
)
```

Training and validation performance can be analyzed using the generated model history.

---

## 🧪 Model Evaluation

After training, the model is evaluated using the test dataset.

The notebook calculates:

```text
Test Loss
Test Accuracy
```

Example:

```python
loss, acc = model.evaluate(test_batches, verbose=1)

print("Loss: ", loss)
print("Accuracy: ", acc)
```

The actual accuracy should be taken from the output produced when the notebook is executed.

---

## 🔍 Prediction

The trained model can be used to predict diabetic retinopathy from a new retinal image.

The prediction workflow:

```text
Input Retinal Image
        ↓
Read Image
        ↓
Convert BGR → RGB
        ↓
Resize to 224 × 224
        ↓
Normalize Pixel Values
        ↓
Load CNN Model
        ↓
Generate Prediction
        ↓
Display Classification Result
```

Example:

```python
predict_class(
    'path/to/retinal/image.png'
)
```

The model returns one of two outcomes:

```text
Diabetic Retinopathy Detected
```

or

```text
Diabetic Retinopathy Not Detected
```

---

## 💾 Model Saving

The trained model is saved using TensorFlow/Keras:

```python
model.save('64x3-CNN.model')
```

This allows the trained model to be loaded later for prediction without retraining.

---

## ▶️ How to Run the Project

### 1. Clone the repository

```bash
git clone https://github.com/ravikiran966/Diabetic-Retinopathy-Prediction.git
```

### 2. Open the notebook

Open:

```text
diabetic_retinopathy.ipynb
```

using:

* Google Colab
* Jupyter Notebook
* JupyterLab

### 3. Install dependencies

```bash
pip install tensorflow pandas numpy matplotlib opencv-python scikit-learn
```

### 4. Add the dataset

Place the dataset in the expected project directory:

```text
input/
└── diabetic-retinopathy-224x224-gaussian-filtered/
```

Make sure the CSV and image directories match the paths used in the notebook.

### 5. Run the notebook

Run the cells sequentially to:

* Load the dataset
* Preprocess the images
* Split the dataset
* Train the CNN
* Evaluate the model
* Save the model
* Perform predictions

---

## 📌 Key Features

* Retinal image preprocessing
* Binary diabetic retinopathy classification
* CNN-based image classification
* Training, validation, and testing workflow
* Model evaluation
* Image-based prediction
* Trained model persistence

---

## 📚 Project Learning Outcomes

Through this project, I gained practical experience in:

* Python-based data analysis
* Data preprocessing
* Image preprocessing
* Exploratory data analysis
* CNN architecture
* TensorFlow/Keras
* Machine learning model training
* Model evaluation
* Computer vision
* Handling image datasets
* Making predictions using trained models

---

## ⚠️ Disclaimer

This project is developed for **educational and research purposes only**.

The model should not be used as a substitute for professional medical diagnosis or clinical decision-making.

---

## 👨‍💻 Author

**Ravikiran Y**


---

## ⭐ Future Improvements

* Improve CNN architecture and model performance.
* Experiment with transfer learning models such as ResNet or EfficientNet.
* Add additional evaluation metrics such as precision, recall, F1-score, and confusion matrix.
* Implement data augmentation to improve model generalization.
* Deploy the trained model as a web application.
* Add an interactive interface for retinal image upload and prediction.
* Improve model interpretability using explainable AI techniques.
