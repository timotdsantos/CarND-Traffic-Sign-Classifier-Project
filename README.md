## Project: Build a Traffic Sign Recognition Program
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

Overview
---
In this project, deep neural networks and convolutional neural networks were used to classify traffic signs. A model was trained and validated so it can classify traffic sign images using the [German Traffic Sign Dataset](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset). After the model was trained, the model was used to label images of German traffic signs found on the web.


Three main files are submitted here: a file containing project code and a file containing a brief write up explaining the solution. 
- [Traffic_Sign_Classifier.ipynb (code)](https://github.com/timotdsantos/CarND-Traffic-Sign-Classifier-Project/blob/master/Traffic_Sign_Classifier.ipynb)
- [report.html (exported code)](https://github.com/timotdsantos/CarND-Traffic-Sign-Classifier-Project/blob/master/report.html)
- [README.md (write up)](https://github.com/timotdsantos/CarND-Traffic-Sign-Classifier-Project/blob/master/README.md)

The Project
---
The goals / steps of this project are the following:
* Load the data set
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report
---
### Dependencies
This lab requires:

* [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit)

The lab enviroment can be created with CarND Term1 Starter Kit. Click [here](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md) for the details.

### Basic Summary of the Data Set 

1. This is a pickled dataset in which the data was already resized to 32x32 images. It contains a training, validation and test set. It is not included in the repository, but should be downloaded [here](https://d17h27t6h515a5.cloudfront.net/topher/2017/February/5898cd6f_traffic-signs-data/traffic-signs-data.zip).

2. Validation set is taken from the training data, which is an 80-20 split.

3. Here is a basic summary of the data set:
`Number of training examples = 27839
Number of testing examples = 12630
Number of validation examples = 6960
Image data shape = (32, 32, 3)
Number of classes = 43
Number of classes in validation = 43
Number of classes in test = 43`

4. Here's a sample of the data:
<img src="examples/grayscale.jpg" width="480" alt="sample and grayscaled" />


```