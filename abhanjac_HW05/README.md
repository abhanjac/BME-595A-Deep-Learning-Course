
## BME 595A Deep Learning: Homework 5 Report

### Arindam Bhanja Chowdhury

##### Platform and Packages used:
Anaconda 4.3, python 3.6, PyTorch.
Operating System:   Ubuntu 14.04.
PyCharm IDE.

#### Overview of the code:
The objective of this assignment is to use the **LeNet5** ([LeNet5](http://yann.lecun.com/exdb/publis/pdf/lecun-01a.pdf)) convolution neural network to train the **MNIST** ([MNIST](http://yann.lecun.com/exdb/mnist/)) dataset and then compare the performance with the neural network that was used in the **abhanjac_HW04**. In the second part of the code we have to train the same **LeNet5** network on the **CIFAR100** ([CIFAR100](https://www.cs.toronto.edu/~kriz/cifar.html)) image dataset and check the performance of the network. The CIFAR100 dataset has got **50000** training images and **10000** test images. 
We have also used a **view** and another **cam** function for this assignment.
The view function takes in a **3x32x32** byte tensor (which is also the form in which the training images are fed to the LeNet5 network) and convert and display them as colored images. The images however are very small, and so they are resized to a **320x240** image before displaying it. It also internally calls the forward function of the LeNet5 network and also displays the predicted label as the title of the displayed window.
The cam function captures the video from a camera and shows the video. This function also internally calls the forward function of the LeNet5 network and feeds it with a **32x32** resized version of every video frame (which is actually of **640x480** size). If a picture of an object that the network has been trained with is held in front of the camera, then the predicted object name is displayed on the screen.
Details of the accuracy and time of the LeNet5 on CIFAR100 and the comparison between LeNet5 and the neural network (of abhanjac_HW04 assignment) when both running MNIST, is given below in the result section.

#### How to run the code:
The **Img2Num** and the **Img2Obj** classes can be imported into a python script and they can be trained using the **train()** function and then they can be tested using their **forward()** function.

#### Results:

##### Training and Validation error vs the number of Iterations (Img2Num - LeNet5 on MNIST):
![error_vs_iteration_Img2Num.png](https://github.com/abhanjac/BME-595A-Deep-Learning-Course/blob/master/abhanjac_HW05/error_vs_epoch_img2num.png)

##### Training time (seconds) vs the number of Iterations (Img2Num - LeNet5 on MNIST):
![training_time_vs_iteration_Img2Num.png](https://github.com/abhanjac/BME-595A-Deep-Learning-Course/blob/master/abhanjac_HW05/training_time_vs_epoch_img2num.png)

##### Training time comparison between the NnImg2Num (network based on abhanjac_HW04) and LeNet5 network:
![training_time_comparison_img2num_and_NnImg2Num.png](https://github.com/abhanjac/BME-595A-Deep-Learning-Course/blob/master/abhanjac_HW05/training_time_comparison_img2num_and_NnImg2Num.png)

##### 

The results obtained during training on the **MNIST** in the first ans last few iterations are the following (output in the terminal):
NnImg2Num is when MNIST was training the simple neural network of abhanjac_HW04 and Img2Num is when MNIST was training the LeNet5 network.

```
########## ---------- 	[[   Img2Num   ]]	 ---------- ########## 

Train Epoch: 1	[60000/60000 (100%)]		Loss: 0.032771
Training error: 0.064 	Accuracy: 89.49 % 	Validation Error: 0.032 	Training time: 22.156 sec

Train Epoch: 2	[60000/60000 (100%)]		Loss: 0.019410
Training error: 0.024 	Accuracy: 93.96 % 	Validation Error: 0.017 	Training time: 30.245 sec

........

Train Epoch: 49	[60000/60000 (100%)]		Loss: 0.004314
Training error: 0.002 	Accuracy: 98.93 % 	Validation Error: 0.003 	Training time: 19.853 sec

Train Epoch: 50	[60000/60000 (100%)]		Loss: 0.001863
Training error: 0.002 	Accuracy: 98.91 % 	Validation Error: 0.003 	Training time: 24.203 sec


########## ---------- 	[[   NnImg2Num   ]]	 ---------- ########## 

Train Epoch: 1	[60000/60000 (100%)]		Loss: 0.090459
Training error: 0.090 	Accuracy: 10.32 % 	Validation Error: 0.090 	Training time: 16.225 sec

Train Epoch: 2	[60000/60000 (100%)]		Loss: 0.088952
Training error: 0.090 	Accuracy: 19.96 % 	Validation Error: 0.088 	Training time: 16.482 sec

........

Train Epoch: 49	[60000/60000 (100%)]		Loss: 0.000079
Training error: 0.001 	Accuracy: 97.66 % 	Validation Error: 0.004 	Training time: 16.415 sec

Train Epoch: 50	[60000/60000 (100%)]		Loss: 0.000176
Training error: 0.001 	Accuracy: 97.67 % 	Validation Error: 0.004 	Training time: 20.947 sec

```

The full list of the output is give in the following file ([training_status_of_Img2Num_NnImg2Num.txt](https://github.com/abhanjac/BME-595A-Deep-Learning-Course/blob/master/abhanjac_HW05/training_status_of_img2num_NnImg2Num.txt)).

#### Comparison between the MyImg2Num and NnImg2Num neural networks:
(**Note:** Both the networks are trained for the same number or iterations and have identical structures.)

| Model attributes | MyImg2Num | NnImg2Num |
|---|---|---|
| **Training time (sec) (approx, for every iteration)** | 8.5 | 17 |
| **Training error (after 50 iterations)** | 0.000 | 0.001 |
| **Validation error (after 50 iterations)** | 0.069 | 0.004 |
| **Accuracy (%) (after 50 iterations)** | 98.48 | 97.72 |
| **Learning rate (eta)** | 0.05 | 6.7 |

#### Comments and Observations:
* It seems that when we try to use a bigger model with more hidden layers, the training takes more time.
* Training the images in batches is faster than training the whole set of images together.
* The MyImg2Num performs better overall, but there is a difference between the training and the validation error at the end of the 50th iteration. But the NnImg2Num on the other hand has these two errors very close to each other in values.
* If the size of the batches is decreased then the training takes more time.

