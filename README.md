# Sign Language Communication: A Unified Approach for ASL, BSL, and ISL

Before we get into hand sign recognition , it is mandatory to install mediapipe .

This model mainly works on Multi Layered Perceptron (MLP) which detects the hand gestures using the keypoints attained by the algorithm

# Requirements
  mediapipe 0.8.3<br>
  OpenCV 3.4.2 or Later<br>
  Tensorflow 2.3.0 or Later<br>
  tf-nightly 2.5.0.dev or later<br> 
  scikit-learn 0.23.2<br>
  matplotlib 3.3.2<br> 

## Mediapipe Installation for Jetson & JetBot

### Method 1: Using Default Python 3.6.9

The Jetson device comes with Python 3.6.9 by default. You can install Mediapipe 0.8.3 using the following command:

pip install https://files.pythonhosted.org/packages/12/74/f55fc21266c08c304f05a409ba388c50f94fb52ef0f99100bb60287c4d91/mediapipe-0.8.3-cp36-cp36m-manylinux2014_x86_64.whl

### Method 2: Changing Python to Version 3.8
If you prefer using Python 3.8, you can follow these steps:
This will change your default python3.6 to python 3.8
```bash
sudo apt update
sudo apt install python3.8
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.8 1
sudo apt install python-pip
pip install mediapipe
```
#### 2.Model training
Open "[Hand_sign_classifier_model.ipynb](Hand_sign_classifier_model.ipynb)" in Jupyter Notebook and execute from top to bottom.<br>
To change the number of training data classes, change the value of "NUM_CLASSES = 3" <br>and modify the label of "model/Hand_sign/Hand_sign_label.csv" as appropriate.<br><br>

#### X.Model structure
The image of the model prepared in "[Hand_sign_classifier_model.ipynb](Hand_sign_classifier_model.ipynb)" is as follows.
<img src="https://user-images.githubusercontent.com/37477845/102246723-69c76a00-3f42-11eb-8a4b-7c6b032b7e71.png" width="50%"><br><br>
