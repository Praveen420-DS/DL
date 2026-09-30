# Image Segmentation using U-Net

This is a Deep Learning project where I worked on **image segmentation using the U-Net architecture**.

The main idea of this project is to take an image and predict the class of each pixel. Instead of only telling what is present in an image, the model tries to identify **which pixels belong to different regions of the image**.

I used the **Oxford-IIIT Pet dataset** and built a U-Net model using TensorFlow/Keras.

## What I worked on

In this notebook, I went through the complete basic workflow of an image segmentation project:

* Loaded the Oxford-IIIT Pet dataset using TensorFlow Datasets
* Resized images and segmentation masks to **128 × 128**
* Normalized image pixel values
* Prepared the corresponding segmentation masks
* Built a U-Net model from scratch
* Used convolution blocks for feature extraction
* Used encoder and decoder blocks
* Added skip connections between the encoder and decoder
* Compiled the model using Adam optimizer
* Trained the model for 5 epochs
* Generated segmentation predictions
* Compared the original image, ground truth mask and predicted mask
* Plotted training and validation accuracy
* Calculated IoU for a sample prediction
* Evaluated the model on the test dataset

## Dataset

I used the **Oxford-IIIT Pet Dataset** through TensorFlow Datasets.

The dataset contains:

* Training samples: **3,680**
* Testing samples: **3,669**

The segmentation task contains **3 classes**, and the model predicts one class for each pixel.

## Model

The model used in this project is **U-Net**.

The architecture contains:

```text
Input Image
     ↓
Encoder
     ↓
Bottleneck
     ↓
Decoder
     ↓
Pixel-wise Prediction
```

The encoder extracts features from the image while reducing the spatial size.

The decoder gradually restores the spatial resolution. The **skip connections** transfer useful spatial information from the encoder to the decoder, which helps the model preserve object boundaries.

The final layer uses a **3-class softmax output** for pixel-level classification.

### Model details

* Input size: `128 × 128 × 3`
* Architecture: U-Net
* Optimizer: Adam
* Loss: Sparse Categorical Crossentropy
* Metric: Accuracy
* Total parameters: **1,925,667**
* Trainable parameters: **1,925,667**

## Training

I trained the model for **5 epochs**.

The validation accuracy improved during training:

| Epoch | Training Accuracy | Validation Accuracy |
| ----: | ----------------: | ------------------: |
|     1 |            65.83% |              72.34% |
|     2 |            72.86% |              75.44% |
|     3 |            77.30% |              79.17% |
|     4 |            80.44% |              82.35% |
|     5 |            82.60% |              83.85% |

The model reached a validation accuracy of about **83.85%** at the end of the 5 epochs.

## Test Results

The final evaluation in the notebook gave:

```text
Test Loss     : 0.4787
Test Accuracy : 0.8127
IoU Score     : 0.7610
```

The IoU value shown above was calculated on a sample prediction rather than across the complete test set.

## Visual Results

The notebook also compares:

```text
Original Image → Ground Truth Mask → Predicted Mask
```

This helps to visually understand how well the U-Net is separating the different regions of the image.

## Technologies Used

* Python
* TensorFlow
* TensorFlow Datasets
* Keras
* NumPy
* Matplotlib
* Google Colab

## What I learned

Through this project, I got a better understanding of:

* How image segmentation is different from image classification
* How U-Net works
* Encoder-decoder architecture
* Skip connections
* Pixel-level classification
* Image and mask preprocessing
* Training and validation of segmentation models
* IoU as a segmentation evaluation metric

This is currently a **learning/project implementation**, and there is still room to improve the preprocessing, training strategy and evaluation metrics.

## Notebook

The complete implementation is available in the Jupyter/Google Colab notebook in this repository.

---

**Project:** Image Segmentation
**Model:** U-Net
**Dataset:** Oxford-IIIT Pet
**Framework:** TensorFlow / Keras
