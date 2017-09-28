
## BME 595A Deep Learning: Homework 4 Report

### Arindam Bhanja Chowdhury

##### Platform and Packages used:
Anaconda 4.3, python 3.6, PyTorch.
Operating System:   Ubuntu 14.04.
PyCharm IDE.

#### Overview of the code:
The objective of this assignment is to train a neural network (having the same structure as created in the **abhanjac_HW03**) and train it on the **MNIST** dataset. Then another network built with the classes of pytorch has to be trained with the same dataset and the total training time and error has to be compared between the two.

The **MNIST** dataset ([MNIST](http://yann.lecun.com/exdb/mnist/)) has got **60000** training images of **single channel** handwritten digits, each of **28x28** pixels. It also has a set of **10000** test images.

In this code the 60000 image training dataset is imported and then the set is broken down into **1200** batches of **50** images. The test data is also divided into **200** similarly sized batches.
Each of the images of the training and the testing dataset are converted from a 28x28 image into a **1x784** tensor. These will be the input to the neural network and the corresponding output will be a **1x10** tensor that has a **1** in the index corresponding to the digit represented be the image. All the other indices are **0**. 
A neural network is created using the same **NeuralNetwork** class of abhanjac_HW03 having the following structure **784-400-200-100-10** where 784 is the number of input layer nodes and 10 is the number of output layer nodes. The others are the nodes of the **three** hidden layers. The learning rate for this network is selected to be **eta = 0.05**. Then the set of all the image tensors of one batch is sent as a **50x784** tensor into the network one by one in a loop and corresponding output set is obtained in the form of a **50x10** tensor. In this way when training is completed with all batches, the total **mean squared training error** and the **trining time** are calculated. The network is validated with the test set images to evaluate the **accuracy** and the **mean squared validation error**. Then the training and testing datasets are re-shuffled. And again the same procedure of training with 50x784 training image batches are continued. In this way **50** iterations of training and validation are performed.
The plot of the variation of the training and validation error vs the iterations and the training time vs the iterations are shown in the figures given in the result section.

The final accuracy of the network became **98.48 %** and the average training time was **8.5 seconds**.
Similar procedure is followed for the other neural network of same structure, created by using the **optim** package of pytorch. But for this network the **eta = 6.7** was selected and the overall accuracy was obtained to be **97.72 %**. The average training time was **17 seconds**. The time taken for the training was also more. The relevant plots for this network are also shown in the result section.

#### How to run the code:
The **MyImg2Num** and the **NnImg2Num** classes can be imported into a python script and they can be trained using the **train()** function and then they can be tested using their **forward()** function.

#### Results:

##### Training and Validation error vs the number of Iterations (MyImg2Num - network based on abhanjac_HW03):
![error_vs_iteration_MyImg2Num.png](https://github.com/abhanjac/BME-595A-Deep-Learning-Course/blob/master/abhanjac_HW04/error_vs_iteration_MyImg2Num.png)

##### Training time (seconds) vs the number of Iterations (MyImg2Num - network based on abhanjac_HW03):
![training_time_vs_iteration_MyImg2Num.png](https://github.com/abhanjac/BME-595A-Deep-Learning-Course/blob/master/abhanjac_HW04/training_time_vs_iteration_MyImg2Num.png)

##### Training and Validation error vs the number of Iterations (NnImg2Num - network based on pyTorch classes):
![error_vs_iteration_NnImg2Num.png](https://github.com/abhanjac/BME-595A-Deep-Learning-Course/blob/master/abhanjac_HW04/error_vs_iteration_NnImg2Num.png)

##### Training time (seconds) vs the number of Iterations (NnImg2Num - network based on pyTorch classes):
![training_time_vs_iteration_NnImg2Num.png](https://github.com/abhanjac/BME-595A-Deep-Learning-Course/blob/master/abhanjac_HW04/training_time_vs_iteration_NnImg2Num.png)

##### Training time comparison between the MyImg2Num and NnImg2Num networks:
![training_time_comparison_MyImg2Num_and_NnImg2Num.png](https://github.com/abhanjac/BME-595A-Deep-Learning-Course/blob/master/abhanjac_HW04/training_time_comparison_MyImg2Num_and_NnImg2Num.png)

The results obtained during the training in the first ans last few iterations are the following (output in the terminal):

```
########## ---------- 	[[   MyImg2Num   ]]	 ---------- ########## 

Train Iteration: 1	[60000/60000 (100%)]		Loss: 0.053507
Iteration: 1 	Training error: 0.290 	Accuracy: 91.32 % 	Validation Error: 0.326 	Training time: 7.862 sec

Train Iteration: 2	[60000/60000 (100%)]		Loss: 0.041670
Iteration: 2 	Training error: 0.046 	Accuracy: 94.85 % 	Validation Error: 0.202 	Training time: 7.867 sec

........

Train Iteration: 49	[60000/60000 (100%)]		Loss: 0.000000
Iteration: 49 	Training error: 0.000 	Accuracy: 98.47 % 	Validation Error: 0.069 	Training time: 8.021 sec

Train Iteration: 50	[60000/60000 (100%)]		Loss: 0.000000
Iteration: 50 	Training error: 0.000 	Accuracy: 98.48 % 	Validation Error: 0.069 	Training time: 8.063 sec


########## ---------- 	[[   NnImg2Num   ]]	 ---------- ########## 

Train Iteration: 1	[60000/60000 (100%)]		Loss: 0.089956
Iteration: 1 	Training error: 0.090 	Accuracy: 10.32 % 	Validation Error: 0.090 	Training time: 13.977 sec

Train Iteration: 2	[60000/60000 (100%)]		Loss: 0.077065
Iteration: 2 	Training error: 0.089 	Accuracy: 24.19 % 	Validation Error: 0.080 	Training time: 13.695 sec

........

Train Iteration: 49	[60000/60000 (100%)]		Loss: 0.000421
Iteration: 49 	Training error: 0.001 	Accuracy: 97.69 % 	Validation Error: 0.004 	Training time: 14.896 sec

Train Iteration: 50	[60000/60000 (100%)]		Loss: 0.003981
Iteration: 50 	Training error: 0.001 	Accuracy: 97.72 % 	Validation Error: 0.004 	Training time: 15.581 sec
```

The full list of the output is give in the following file ([training_status_of_MyImg2Num_NnImg2Num.txt](https://github.com/abhanjac/BME-595A-Deep-Learning-Course/blob/master/abhanjac_HW04/training_status_of_MyImg2Num_NnImg2Num.txt)).

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

