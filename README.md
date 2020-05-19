# Object-Detection-using-tensorflow

## Brief Summary
*Last updated: with TensorFlow v1.15.*

This repository is a tutorial for how to use TensorFlow's Object Detection API to train an object detection classifier for multiple objects on Windows 10, 8, or 7. (It will also work on Linux-based OSes with some minor changes.) It was originally written using TensorFlow version 1.15, but will also work for newer versions of TensorFlow.

I will also make a YouTube video that walks through this tutorial. Any discrepancies between the video and this written tutorial are due to updates required for using newer versions of TensorFlow. 

**If there are differences between this written tutorial and the video, follow the written tutorial!**

This readme describes every step required to get going with your own object detection classifier:

## Introduction
The purpose of this tutorial is to explain how to train your own convolutional neural network object detection classifier for multiple objects, starting from scratch. At the end of this tutorial, you will have a program that can identify and draw boxes around specific objects in pictures, videos, or in a webcam feed.

There are several good tutorials available for how to use TensorFlow’s Object Detection API to train a classifier for a single object. However, these usually assume you are using a Linux operating system. If you’re like me, you might be a little hesitant to install Linux on your high-powered gaming PC that has the sweet graphics card you’re using to train a classifier. The Object Detection API seems to have been developed on a Linux-based OS. To set up TensorFlow to train a model on Windows, there are several workarounds that need to be used in place of commands that would work fine on Linux. Also, this tutorial provides instructions for training a classifier that can detect multiple objects, not just one.

The tutorial is written for Windows 10, and it will also work for Windows 7 and 8. The general procedure can also be used for Linux operating systems, but file paths and package installation commands will need to change accordingly. I used TensorFlow-GPU v1.15 while writing the initial version of this tutorial, but it will likely work for future versions of TensorFlow.

TensorFlow-GPU allows your PC to use the video card to provide extra processing power while training, so it will be used for this tutorial. In my experience, using TensorFlow-GPU instead of regular TensorFlow reduces training time by a factor of about 8 (3 hours to train instead of 24 hours). The CPU-only version of TensorFlow can also be used for this tutorial, but it will take longer. 

## Steps
### 1. Install Anaconda.
To install [Anaconda](https://www.anaconda.com/distribution/#download-section) as instructed in the video, because the Anaconda virtual environment will be used for the rest of this tutorial. (Note: The current version of Anaconda uses Python 3.7, which is not officially supported by TensorFlow. However, when creating an Anaconda virtual environment during this tutorial, we will tell it to use Python 3.5.)

### 2. Creating anaconda virtual Environment and Installing Dependencies.
Now, we'll work on setting up a virtual environment in Anaconda for tensorflow-gpu. From the Start menu in Windows, search for the Anaconda Prompt utility, right click on it, and click “Run as Administrator”. If Windows asks you if you would like to allow it to make changes to your computer, click Yes.

In the command terminal that pops up, create a new virtual environment called “tensorflow1” by issuing the following command:
```
C:\> conda create -n tensorflow1 pip python=3.5
```
Then, activate the environment and update pip by issuing:
```
C:\> activate tensorflow1

(tensorflow1) C:\>python -m pip install --upgrade pip
```
Install tensorflow-gpu in this environment by issuing:
```
(tensorflow1) C:\> pip install tensorflow-gpu==1.15 keras-gpu==2.31
```

(Note: You can also use the CPU-only version of TensorFow, but it will run much slower. If you want to use the CPU-only version, just use "tensorflow" instead of "tensorflow-gpu" in the previous command.)

Install the other necessary packages by issuing the following commands:
```
(tensorflow1) C:\> conda install -c anaconda protobuf
(tensorflow1) C:\> pip install pillow
(tensorflow1) C:\> pip install lxml
(tensorflow1) C:\> pip install Cython
(tensorflow1) C:\> pip install contextlib2
(tensorflow1) C:\> pip install jupyter
(tensorflow1) C:\> pip install matplotlib
(tensorflow1) C:\> pip install pandas
(tensorflow1) C:\> pip install opencv-python
```
(Note: The ‘pandas’ and ‘opencv-python’ packages are not needed by TensorFlow, but they are used in the Python scripts to generate TFRecords and to work with images, videos, and webcam feeds.)

### 3. Download or Clone My repository.

1. [Download the Repository from :-]()
