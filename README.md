# A real time application to predict the ASL using advanced machine learning techniques, using various data processing techniques 

This endeavor involves deploying a real-time system for recognizing hand signs,employing a fine-tuned MobileNet model trained on the Sign Language MNIST dataset. The primary goal is to precisely classify hand signs representing alphabet letters, utilizing live video input.

The dataset used for this project was found on kaggle.com:
https://www.kaggle.com/datasets/datamunge/sign-language-mnist

The foundation of our project is the Sign Language MNIST dataset, a modified version of the classic MNIST dataset that is commonly used in image recognition tasks within the machine learning community. This dataset is specifically adapted to include images of hand signs representing 24 letters of the ASL alphabet (omitting J and Z due to their motion-based nature). Each image is a 28x28 pixel, greyscale photograph of a hand sign against a uniform background, providing a clear and focused dataset for training our models.

**Data Preprocessing:**

Our preprocessing pipeline included several augmentation techniques to improve model robustness:
● Rescaling: Normalizes pixel values to a range of [0,1] for faster training convergence.
● Rotation, Width Shift, Height Shift, and Zoom: These augmentations help the model generalise better over different orientations and scales of hand signs.
● Shear: Simulates a slanting of signs, providing angular diversity.
● Horizontal Flip: Increases the dataset variety by mirroring images, although not always applicable to ASL.
● Fill Mode: Determines how newly created pixels are filled, with 'nearest' using the nearest pixel value.

**Model Development:**

Employed three different neural network architectures, each with unique characteristics suited to specific aspects of image and sequence processing:


