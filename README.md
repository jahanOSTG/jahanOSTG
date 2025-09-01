# Plant Disease Classification using EfficientNetB0

## Project Overview
This project aims to classify **plant leaves** into three categories:
- 🌿 Healthy
- 🌱 Powdery Mildew
- 🍂 Rust

We used **EfficientNetB0 (Transfer Learning)** with fine-tuning to build a high-accuracy classification model.

Dataset: [Kaggle: Plant Disease Recognition](https://www.kaggle.com/datasets/rashikrahmanpritom/plant-disease-recognition-dataset)


---

## Tools Used

| Tool/Library | Badge | Purpose |
|--------------|-------|---------|
| Python 3.x   | ![Python](https://img.shields.io/badge/python-%233776AB.svg?style=for-the-badge&logo=python&logoColor=white) | Programming language |
| TensorFlow   | ![TensorFlow](https://img.shields.io/badge/tensorflow-%23FF6F00.svg?style=for-the-badge&logo=tensorflow&logoColor=white) | Deep learning framework |
| Keras        | ![Keras](https://img.shields.io/badge/keras-%23D00000.svg?style=for-the-badge&logo=keras&logoColor=white) | Neural network API |
| Google Colab | ![Colab](https://img.shields.io/badge/colab-%23F9AB00.svg?style=for-the-badge&logo=googlecolab&logoColor=white) | Cloud execution |
| NumPy        | ![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white) | Numerical operations |
| Pandas       | ![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white) | Data handling |
| Matplotlib   | ![Matplotlib](https://img.shields.io/badge/matplotlib-%23006BB3.svg?style=for-the-badge&logo=matplotlib&logoColor=white) | Plotting & visualization |
| Seaborn      | ![Seaborn](https://img.shields.io/badge/seaborn-%23000000.svg?style=for-the-badge&logo=seaborn&logoColor=white) | Advanced plotting |
| PIL          | ![PIL](https://img.shields.io/badge/pillow-%23DD3C00.svg?style=for-the-badge&logo=python&logoColor=white) | Image processing |

---

## Techniques Applied

| Technique | Badge | Description |
|-----------|-------|-------------|
| Transfer Learning | ![TL](https://img.shields.io/badge/transfer--learning-%23007ACC.svg?style=for-the-badge) | Using EfficientNetB0 pretrained on ImageNet |
| Data Augmentation | ![Aug](https://img.shields.io/badge/augmentation-%23FFB000.svg?style=for-the-badge) | Increase dataset diversity to prevent overfitting |
| Fine-tuning | ![FT](https://img.shields.io/badge/fine--tuning-%23008000.svg?style=for-the-badge) | Unfreeze top layers of base model for better accuracy |
| Early Stopping | ![ES](https://img.shields.io/badge/early--stopping-%23FF0000.svg?style=for-the-badge) | Stop training when validation stops improving |
| Reduce LR on Plateau | ![LR](https://img.shields.io/badge/reduce--lr-%230077FF.svg?style=for-the-badge) | Reduce learning rate when improvement stalls |
| Model Checkpoint | ![MC](https://img.shields.io/badge/model--checkpoint-%23AA00FF.svg?style=for-the-badge) | Save best model during training |
| Image Preprocessing | ![IP](https://img.shields.io/badge/image--preprocessing-%2300CCFF.svg?style=for-the-badge) | Resize, scale, and normalize input images |
| Prediction | ![Pred](https://img.shields.io/badge/prediction-%23FF8800.svg?style=for-the-badge) | Predict disease class for new images |

---

## Workflow

### 1. Data Preparation
- Dataset organized into `Train`, `Validation`, and `Test` folders
- Classes: `Healthy`, `Powdery`, `Rust`
- Image augmentation applied to increase dataset diversity:
  - 🔄 Rotation
  - ↔ Width/Height shift
  - ✂ Shear
  - 🔍 Zoom
  - ↕ Horizontal/Vertical flip
- Preprocessing using **EfficientNetB0 preprocess_input**

### 2. Model Architecture
- **Base Model**: EfficientNetB0 (ImageNet pretrained, top removed)
- **Added Layers**:
  - GlobalAveragePooling2D
  - Dropout(0.4)
  - Dense(3, activation='softmax')
- Optimizer: Adam
- Loss Function: Categorical Crossentropy
- Metrics: Accuracy

### 3. Training Strategy
- **Phase 1 (Feature Extraction)**: Freeze base model, train only added head layers
- **Phase 2 (Fine-tuning)**: Unfreeze top 50 layers of EfficientNetB0 for further training
- Callbacks used:
  - ⏹ EarlyStopping
  - ⚡ ReduceLROnPlateau
  - 💾 ModelCheckpoint

### 4. Results
- Validation Accuracy: 100% (best epoch)
- Test Accuracy: 93.3%
- Confusion Matrix & Classification Report show high precision and recall across all classes

### 5. Visualization
- 📈 Training/Validation Accuracy & Loss curves
- 🔥 Confusion Matrix heatmap

### 6. Prediction on Custom Images
- Preprocess custom image (resize 224x224, preprocess_input)
- Use the trained model for prediction
- Display predicted class and probability scores

---

## Performance Metrics

| Class     | Precision | Recall | F1-score | Support |
|-----------|-----------|--------|----------|---------|
| 🌿 Healthy   | 0.93      | 0.86   | 0.90     | 50      |
| 🌱 Powdery   | 0.90      | 0.94   | 0.92     | 50      |
| 🍂 Rust      | 0.96      | 1.00   | 0.98     | 50      |

**Overall Test Accuracy: 93%**

---

## Key Takeaways
- ✅ Transfer learning with EfficientNetB0 gave excellent performance
- 🎨 Data augmentation improved model generalization
- 🔧 Fine-tuning boosted validation accuracy to 100%
- 🖼 The trained model successfully predicts plant diseases from unseen images

---

## References
- [EfficientNet: Rethinking Model Scaling for CNNs](https://arxiv.org/abs/1905.11946)
- [Kaggle Plant Disease Dataset](https://www.kaggle.com/datasets/rashikrahmanpritom/plant-disease-recognition-dataset)
