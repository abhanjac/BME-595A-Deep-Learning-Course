## BME 595A Deep Learning: Homework 3 Report

### Arindam Bhanja Chowdhury

##### Platform and Packages used:
Anaconda 4.3, python 3.6, PyTorch.
Operating System:   Ubuntu 14.04.
PyCharm IDE.

#### Overview of the code:
The objective of this assignment is to train the simple artificial neural network model that was created in the **abhanjac_HW02**.
The python script called **neural_network.py** has a Class called **NeuralNetwork** defined in it, that will create a basic neural network. The number of nodes in the the input, output and hidden layers (if any) has to be passed as arguments while defining an object of this class. The class will assign random weights to the parameter **theta** of the network. The **forward** function in the class takes in an argument as a tensor, that is the input to the network and then evaluates and returns the output in the form of a tensor as well. These basically does the feed forward function in the neural network. Another function called **backward** calculates the backward propagation values of the network. It takes in the actual desired output of the neural network as an input. Using that it generates the **dE_dtheta** values that are used to update the parameters **theta** while training. The **updateParameter** function takes the **theta** and the **dE_dtheta** values and updates the **theta** as per the equation **theta = theta - eta\*dE_dtheta**. The **eta** is the learning rate of the neural network that is supplied as an input argument to the **updateParameter** function.

Another python script class called **logic_gates.py** has four different classes **AND**, **OR**, **NOT** and **XOR** defined inside it. These classes are used to create the respective basic logic gates, based on the neural network. The logic gates classes calls the **NeuralNetwork** class and provides it with the required number of inputs and output. These classes have a function called **train** that trains the network. An object of each class is instantiated and then the corresponding **train** function is called. This function generates a dummy set of data on the fly inside it and passes it into the **forward** function of the network. While training the an object of the **AND** class, this dummy data set will have multiple training examples of all possible combinations of and gate logic along with their corresponding outputs. It then calls the **backward** function with the logic outputs as argument. This is followed by a calling of the **updateParameter** function with the learning rate **eta** as input. In this way with several iterations of this sequence the parameters **theta** of the object of class and gets trained and it will start behaving like an **And** gate.
Similar operations are done to train the **Or**, **Not** and **Xor** gate objects as well.

#### How to run the code:
Put all the python scripts in one directory. Go to that directory using the terminal and then type in the command(s):
$ python3 test.py
(**NOTE:** This might take some time to generate the output.)

#### Results:
```
Layer 1: 
-8.8583  5.7866  5.7866
[torch.FloatTensor of size 1x3]

Number of iterations: 110 
Final Error: 0.000989 

And(True, True):	 True 	;	And(False, True):	 False 	;	And(True, False):	 False 	;	And(False, False):	 False 


Layer 1: 
-2.4996  5.9710  5.9715
[torch.FloatTensor of size 1x3]

Number of iterations: 68 
Final Error: 0.000974 

Or(True, True):		 True 	;	Or(False, True):	 True 	;	Or(True, False):	 True 	;	Or(False, False):	 False 


Layer 1: 
 2.9217 -6.2704
[torch.FloatTensor of size 1x2]

Number of iterations: 64 
Final Error: 0.000972 

Not(True):			 False 	;	Not(False):			 True 


Layer 1: 
 2.7942  5.9668 -5.6038
 3.3364 -6.4733  6.5667
[torch.FloatTensor of size 2x3]

Layer 2: 
 10.4493  -7.1893  -7.1190
[torch.FloatTensor of size 1x3]

Number of iterations: 184 
Final Error: 0.000982 

Xor(True, True):	 False 	;	Xor(False, True):	 True 	;	Xor(True, False):	 True 	;	Xor(False, False):	 False 
```

#### Theta comparisons between homework 2 and homework 3:
**AND gate**

|Layer 1|theta_0 (Bias)|theta_1|theta_2|
|:---:|:---:|:---:|:---:|
|HW2|-200|100|100|
|HW3|-8.8583|5.7866|5.7866|

**OR gate**

|Layer 1|theta_0 (Bias)|theta_1|theta_2|
|:---:|:---:|:---:|:---:|
|HW2|-100|200|200|
|HW3|-2.4996|5.9710|5.9715|

**NOT gate**

|Layer 1|theta_0 (Bias)|theta_1|
|:---:|:---:|:---:|
|HW2|100|-200|
|HW3|2.9217|-6.2704|

**XOR gate**

|Layer 1|theta_01 (Bias)|theta_11|theta_12|theta_02 (Bias)|theta_21|theta_22|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|HW2|100|-200|200|100|200|-200|
|HW3|2.5695|-5.2481|5.6784|4.2724|7.7363|-7.9836|

|Layer 2|theta_0 (Bias)|theta_1|theta_2|
|:---:|:---:|:---:|:---:|
|HW2|200|-100|-100|
|HW3|10.4493|-7.1893|-7.1190|


#### Comments and Observations:
* The network is trained till the mean square error becomes less than **0.001**. This takes about **110**, **68**, **64** and **184** iterations for the **AND**, **OR**, **NOT** and **XOR** gates.
* Similar to HW2, here also the XOR gate takes the most iterations to train.
* The values of the parameters shown above are for one particular test run. They are different each time the network is trained again from scratch. But the over all magnitude of the values stay in more or less the same range.
* As the number of iterations increases, the variations in the value of the **theta** parameters decreases and their values become more stable. 
* Lower the value of the **eta** parameter however slows down the learning process. More iterations are needed to learn with a lower **eta** value.
* The more the number of hidden layers and more the number of nodes in the network, the more time it takes to train the network.

