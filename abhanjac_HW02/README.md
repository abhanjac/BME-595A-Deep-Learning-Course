## BME 595A Deep Learning: Homework 2 Report

### Arindam Bhanja Chowdhury

##### Platform and Packages used:
Anaconda 4.3, python 3.6, PyTorch.
Operating System:   Ubuntu 14.04.
PyCharm IDE.

#### Overview of the code:
The objective of this assignment is to create a very simple artificial neural network model.
The python script called **neural_network.py** has a Class called **NeuralNetwork** defined in it, that will create a basic neural network. The number of nodes in the the input, output and hidden layers (if any) has to be passed as arguments while defining an object of this class. The class will assign random weights to the parameter **theta** of the network.
The **getLayer** function inside the class returns the values of the parameters (**theta**) in the form of tensor. The **forward** function in the class takes in an argument as a tensor, that is the input to the network and then evaluates and returns the output in the form of a tensor as well.

Another python script class called **logic_gates.py** has four different classes **AND**, **OR**, **NOT** and **XOR** defined inside it. These classes are used to create the respective basic logic gates, based on the neural network. The logic gates classes calls the **NeuralNetwork** class and provides it with the required number of inputs and output. However the values of the parameter **theta** are not learned in this case, they are assigned directly by the logic gate classes. These classes gets the weights using the **getLayer** function and modifies them.
The inputs to these classes are passed using the **__call__** function.
These classes also has a **forward** function of their own that calls the forward function of the neural network to evaluate the output.

The **test.py** script has objects of class **AND**, **OR**, **NOT** and **XOR** defined in it. Boolean values like **True** and **False** are passed into these objects as inputs, and they in turn return the output in the form of boolean variables as well.

#### How to run the code:
Put all the python scripts in one directory. Go to that directory using the terminal and then type in the command(s):
$ python3 test.py

#### Results:
The results obtained by running the **test.py** script is the following (output in the terminal):

And(True, True):	 True 	;	And(False, True):	 False 	;	And(True, False):	 False 	;	And(False, False):	 False

Or(True, True):		 True 	;	Or(False, True):	 True 	;	Or(True, False):	 True 	;	Or(False, False):	 False

Not(True):			 False 	;	Not(False):			 True

Xor(True, True):	 False 	;	Xor(False, True):	 True 	;	Xor(True, False):	 True 	;	Xor(False, False):	 False

#### Comments and Observations:
* Other than **XOR** gate none of the networks needed for the other gates needed any hidden layer. The **XOR** gate network needed one hidden layer with two nodes.
* If the values of the tensor **b** are to be copied to **a** without creating any new tensor, then **a.copy\_(...)** function comes in handy. This is specially useful for modifying the values to the entire **theta** tensor in one shot.

