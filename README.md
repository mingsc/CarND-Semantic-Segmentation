# Semantic Segmentation

This project is part of my Udacity Self-Driving-Car Nano Degree project, was originally forked from [Udacity](https://github.com/udacity/CarND-Semantic-Segmentation) then modified by olala7846@gmail.com

for the origin project setup, please reference [Udacity's Repo](https://github.com/udacity/CarND-Semantic-Segmentation)

## Introduction
Sementic Segmentation with Fully Convolutional Networks using Python Tensorflow

##### Frameworks and Packages
Make sure you have the following is installed:
 - [Python 3](https://www.python.org/)
 - [TensorFlow](https://www.tensorflow.org/)
 - [NumPy](http://www.numpy.org/)
 - [SciPy](https://www.scipy.org/)
##### Dataset
[Kitti Road dataset](http://www.cvlibs.net/datasets/kitti/eval_road.php)

## Report
I implemented the [FCN-8 architecture](https://people.eecs.berkeley.edu/~jonlong/long_shelhamer_fcn.pdf) and train on AWS spot instances

The training data looks the following image
![train_x](./images/training/um_000002.png)
And the label data looks like this
![train_y](./images/training/um_road_000002.png)
The purple pixels are labeld as road.

After training 60 epochs, the results looks like the following images
##### Results after training 60 epochs (without using random normal initialization)
![sample1](./images/um_000002.png)
![sample2](./images/um_000018.png)
![sample3](./images/umm_000035.png)
![sample4](./images/uu_000098.png)

##### TODO(Olala): Results after initialize with random norm.

### Reflections
Building the network architecture with tensorflow is not very difficult, the hard part is baby sitting the training process of the network.

#### Baby sitting the Neuron Networks

##### Hyper parameters
FCNs are really large , so I ended up using batch_size = 8
More about [tuning hyper parameters](https://youtu.be/wEoyxE0GP2M)

##### Optimizer
I use Adam optimizer, It has built in momentum

##### Kernel Initializing
Ended up using the random normal distribution as the kernel initializer (as the Udacity reviewer suggested).

##### Regularization
I ended up added **L2 regularization** to every layer and use 0.5 keep probability as the VGG **dropout** paremeter.

##### TODOs:

###### [Test on more hyper parameters](https://youtu.be/wEoyxE0GP2M?t=1h14m34s)

####### Augmentat training data for better results

####### Inference Optimization and apply NN to video.