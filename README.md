# A real time application to predict the ASL using advanced machine learning techniques, using various data processing techniques 

## Introduction

This endeavor involves deploying a real-time system for recognizing hand signs,employing a fine-tuned MobileNet model trained on the Sign Language MNIST dataset. The primary goal is to precisely classify hand signs representing alphabet letters, utilizing live video input.

The dataset used for this project was found on kaggle.com:
https://www.kaggle.com/datasets/datamunge/sign-language-mnist

The foundation of our project is the Sign Language MNIST dataset, a modified version of the classic MNIST dataset that is commonly used in image recognition tasks within the machine learning community. This dataset is specifically adapted to include images of hand signs representing 24 letters of the ASL alphabet (omitting J and Z due to their motion-based nature). Each image is a 28x28 pixel, greyscale photograph of a hand sign against a uniform background, providing a clear and focused dataset for training our models.

## Methodology

## Data Preprocessing

Our preprocessing pipeline included several augmentation techniques to improve model robustness:

● Rescaling: Normalizes pixel values to a range of [0,1] for faster training convergence.

● Rotation, Width Shift, Height Shift, and Zoom: These augmentations help the model generalise better over different orientations and scales of hand signs.

● Shear: Simulates a slanting of signs, providing angular diversity.

● Horizontal Flip: Increases the dataset variety by mirroring images, although not always applicable to ASL.

● Fill Mode: Determines how newly created pixels are filled, with 'nearest' using the nearest pixel value.

## Model Development

Employed three different neural network architectures, each with unique characteristics suited to specific aspects of image and sequence processing:

1. **CNN** model consists of several convolutional layers followed by pooling layers, dropout layers for regularisation, and fully connected layers for classification. The convolutional layers are designed to capture spatial hierarchies in the images by applying various filters that detect edges, textures, and other features.
2. **LSTM** networks are a type of recurrent neural network (RNN) suitable for processing sequences and time series data. Our LSTM model was designed to process
sequences of frames, although, for this project, it was adapted to handle single frames by treating them as a sequence of one.
3. **MobileNet** is designed for mobile and edge devices. It uses depthwise separable convolutions that split the convolution process into two layers: a depthwise layer and a pointwise layer. This structure reduces the computational load significantly.

MobileNet was our model of choice for real-time recognition due to its efficiency and speed. Its architecture allows for quick processing of video data with minimal
latency, making it ideal for live ASL translation.

## Real-time Processing Implementation

● Using OpenCV, video is captured from a standard webcam. MediaPipe Hands is employed to detect and track hands within the video feed in real-time.
● Once hands are detected, the regions of interest (hand gestures) are cropped, resized, and preprocessed to fit the input requirements of the MobileNet model.
● The preprocessed images are then fed into the MobileNet model, which classifies the ASL signs in real-time. The model outputs the predicted sign along with the accuracy of the prediction, which is displayed on the video stream.


![image](https://github.com/bhavyaaggarwal24/dl_asl_prediction/assets/163747248/34f8b7e9-60dd-4a26-aa65-f030cfaf1f5f) ![image](https://github.com/bhavyaaggarwal24/dl_asl_prediction/assets/163747248/fa7c49d7-0aee-4ed5-819a-a2c82c8dd6cb) ![image](https://github.com/bhavyaaggarwal24/dl_asl_prediction/assets/163747248/62e25f0c-afe7-473c-9325-144baade71bf) ![image](https://github.com/bhavyaaggarwal24/dl_asl_prediction/assets/163747248/fe157379-bc78-472f-8b25-3baeee23c99a)
