# Crop Disease Detection using Convolutional Neural Networks (CNNs)

This project applies CNNs to classify crop diseases in Rwanda, focusing on crops like potato, tomato, and bell pepper. The goal is to help farmers detect diseases early to improve productivity and food security.

## 1. Data Preprocessing

- **Dataset:** Split into training (`data/train`) and testing (`data/test`).
- **Image Rescaling:** All images rescaled by 1/255.
- **Image Dimensions:** 300x300 pixels.
- **Data Augmentation:** Applied rotations, shearing, zooming, and flipping.
- **Batch Size:** 32

## 2. Model Architectures

### Model 1: Simple CNN Model (Baseline)

**Architecture:**

| Layer Type   | Filters | Kernel Size | Activation | Pool Size | Dropout Rate |
|-------------|---------|-------------|------------|-----------|--------------|
| Conv2D      | 32      | (3, 3)      | ReLU       | -         | -            |
| MaxPooling2D| -       | -           | -          | (2, 2)    | -            |
| Conv2D      | 64      | (3, 3)      | ReLU       | -         | -            |
| MaxPooling2D| -       | -           | -          | (2, 2)    | -            |
| Flatten     | -       | -           | -          | -         | -            |
| Dense       | 64      | -           | ReLU       | -         | -            |
| Dense       | 32      | -           | ReLU       | -         | -            |
| Output      | -       | -           | Softmax    | -         | -            |

- **Optimizer:** Adam
- **Loss Function:** Categorical Crossentropy
- **Metrics:** Accuracy

**Training Results:**

- **Training Accuracy:** 94%
- **Test Accuracy:** 85%

### Model 2: Optimized CNN with Regularization and Dropout

**Architecture:**

| Layer Type         | Filters | Kernel Size | Activation | Pool Size | Dropout Rate | Regularization |
|--------------------|---------|-------------|------------|-----------|--------------|----------------|
| Conv2D             | 32      | (3, 3)      | ReLU       | -         | -            | L2(0.001)      |
| MaxPooling2D       | -       | -           | -          | (2, 2)    | 0.4          | -              |
| BatchNormalization | -       | -           | -          | -         | -            | -              |
| Conv2D             | 64      | (3, 3)      | ReLU       | -         | -            | L2(0.001)      |
| MaxPooling2D       | -       | -           | -          | (2, 2)    | 0.4          | -              |
| Flatten            | -       | -           | -          | -         | -            | -              |
| Dense              | 64      | -           | ReLU       | -         | 0.4          | L2(0.001)      |
| BatchNormalization | -       | -           | -          | -         | -            | -              |
| Dense              | 32      | -           | ReLU       | -         | -            | L2(0.001)      |
| Output             | -       | -           | Softmax    | -         | -            | -              |

- **Optimizer:** Adam
- **Loss Function:** Categorical Crossentropy
- **Callbacks:** EarlyStopping, ModelCheckpoint
- **Metrics:** Accuracy

**Training Results:**

- **Training Accuracy:** 40.00%
- **Test Accuracy:** 39%

## 3. Conclusion

- Model 1 performed well with high training accuracy but struggled with generalization.
- Model 2, using regularization and dropout, showed improved test performance.

## How to Run

1. **Clone the repository:**
   ```bash
   git clone https://github.com/NdanyuzweP/Crop-Disease-Detection
   cd Crop-Disease-Detection


### Run the Jupyter Notebook:
jupyter notebook notebook.ipynb

