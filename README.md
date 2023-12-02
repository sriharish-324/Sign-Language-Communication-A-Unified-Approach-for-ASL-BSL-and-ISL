# Sign Language Communication: A Unified Approach for ASL, BSL, and ISL

Before we get into hand sign recognition , it is mandatory to install mediapipe .

This model mainly works on Multi Layered Perceptron (MLP) which detects the hand gestures using the keypoints attained by the algorithm

# Requirements
  mediapipe 0.8.3<br>
  OpenCV 3.4.2 or Later<br>
  Tensorflow 2.12.0+nv23.06 or Later<br>
  tf-nightly 2.5.0.dev or later<br> 
  scikit-learn 0.23.2<br>
  matplotlib 3.3.2<br> 

## Mediapipe Installation for Jetson

### Method 1: Using Default Python 3.6.9

The Jetson device comes with Python 3.6.9 by default. You can install Mediapipe 0.8.3 using the following command:

pip install https://files.pythonhosted.org/packages/12/74/f55fc21266c08c304f05a409ba388c50f94fb52ef0f99100bb60287c4d91/mediapipe-0.8.3-cp36-cp36m-manylinux2014_x86_64.whl

### Method 2: Changing Python3.6 to Version 3.8 in Jetson
If you prefer using Python 3.8, you can follow these steps:
This will change your default python3.6 to python 3.8
```bash
sudo apt update
sudo apt install python3.8
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.8 1
sudo apt install python-pip
pip install mediapipe
```
### Tensorflow Installation for Jetson
For Python3.6.9
```bash
     sudo apt-get update
     sudo apt-get install libhdf5-serial-dev hdf5-tools libhdf5-dev zlib1g-dev zip libjpeg8-dev liblapack-dev libblas-dev gfortran
     sudo apt-get install python3-pip
     sudo python3 -m pip install --upgrade pip
     sudo pip3 install -U testresources setuptools==65.5.0
     sudo pip3 install -U numpy==1.22 future==0.18.2 mock==3.0.5 keras_preprocessing==1.1.2 keras_applications==1.0.8 gast==0.4.0 protobuf pybind11 cython pkgconfig packaging h5py==3.6.0
     sudo pip3 install --extra-index-url https://developer.download.nvidia.com/compute/redist/jp/v$JP_VERSION tensorflow==$TF_VERSION+nv$NV_VERSION
```
For Python3.8
    https://simeontrieu.medium.com/a-gentle-introduction-to-computer-vision-part-2-building-tensorflow-for-the-jetson-xavier-nx-fcd11fc93be7<br>
    Follow the steps from the above link to build tensorflow from source 

### How to use the Model

### app.py
This is a sample program for inference.<br>
In addition, learning data (key points) for hand sign recognition,<br>
You can also collect training data (index finger coordinate history) for finger gesture recognition.

### Hand_sign_classifier_model.ipynb
This is a model training script for hand sign recognition.

### TipPointClassification-Model.ipynb
This is a model training script for finger gesture recognition.


### utils/cvfpscalc.py
This is a module for FPS measurement.

# Training
Hand sign recognition and finger gesture recognition can add and change training data and retrain the model.

#### 1.Learning data collection
Press "k" to enter the mode to save key points（displayed as 「MODE:Logging Key Point」）<br>
<img src="https://user-images.githubusercontent.com/37477845/102235423-aa6cb680-3f35-11eb-8ebd-5d823e211447.jpg" width="60%"><br><br>
If you press "0" to "9", the key points will be added to "model/keypoint_classifier/keypoint.csv" as shown below.<br>
1st column: Pressed number (used as class ID), 2nd and subsequent columns: Key point coordinates<br>
<img src="https://user-images.githubusercontent.com/37477845/102345725-28d26280-3fe1-11eb-9eeb-8c938e3f625b.png" width="80%"><br><br>
The key point coordinates are the ones that have undergone the following preprocessing up to ④.<br>
<img src="https://user-images.githubusercontent.com/37477845/102242918-ed328c80-3f3d-11eb-907c-61ba05678d54.png" width="80%"><br><br>
In the initial state, three types of learning data are included: open hand (class ID: 0), close hand (class ID: 1), and pointing (class ID: 2).<br>
If necessary, add 3 or later, or delete the existing data of csv to prepare the training data.<br>
<img src="https://user-images.githubusercontent.com/37477845/102348846-d0519400-3fe5-11eb-8789-2e7daec65751.jpg" width="25%">　<img src="https://user-images.githubusercontent.com/37477845/102348855-d2b3ee00-3fe5-11eb-9c6d-b8924092a6d8.jpg" width="25%">　<img src="https://user-images.githubusercontent.com/37477845/102348861-d3e51b00-3fe5-11eb-8b07-adc08a48a760.jpg" width="25%">

#### 2.Model training
Open "[Hand_sign_classifier_model.ipynb](Hand_sign_classifier_model.ipynb)" in Jupyter Notebook and execute from top to bottom.<br>
To change the number of training data classes, change the value of "NUM_CLASSES = 3" <br>and modify the label of "model/Hand_sign/Hand_sign_label.csv" as appropriate.<br><br>

#### X.Model structure
The image of the model prepared in "[Hand_sign_classifier_model.ipynb](Hand_sign_classifier_model.ipynb)" is as follows.
<img src="https://user-images.githubusercontent.com/37477845/102246723-69c76a00-3f42-11eb-8a4b-7c6b032b7e71.png" width="50%"><br><br>
