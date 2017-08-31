# ** BME 595A Deep Learning: Homework 1 Report**

### ** Arindam Bhanja Chowdhury **

##### Platform and Packages used:
Anaconda 4.3, python 3.6, PyTorch.
Operating System:   Ubuntu 14.04.
Machine:    Intel core i7, 16 GB ram.

##### Overview of the code:
In part A, I wrote a python script that performs convolution on an input image using a kernel. The image is first converted into a tensor by the main.py script and then send into the forward function of the Conv2D class. This function then performs the convolution operation. The output is also obtained in the form of a tensor that is returned by the forward function along with a count of the total number of additions and multiplication  operations performed. I have also added another function called normalize_and_save, inside the class Conv2D. The main function sends the output image tensor from the forward function into this function. This function converts the tensor back to an image and normalizes it and saves it. Copies of these grayscale saved images are included in the report as well. The same is true for The original images (*original_1280x720.png* and *original_1920x1080.png*) are also included with the report.
The main python script has got all the parts A, B and C included in it. But while I am running part A, I commented out the other parts, so that the code can run faster. Same thing is done while running the other parts.
So by default, some part of the code will stay commented in the report as well. The user has to uncomment them as required. Comments in the code will help the user to find what parts to comment.

##### Observations:
* The kernel K1 is a horizontal edge filter. So the output image of the task 1 of part A (`partA_task1_K1_1280x720.png` and `partA_task1_K1_1920x1080.png`), has its horizontal edges more highlighted in the image. 
* The kernel K4 is also a horizontal edge filter, but it has a larger size. Hence the corresponding convoluted image (`partA_task2_K4_1280x720.png` and `partA_task2_K4_1920x1080.png`) also has highlighted horizontal edges, but the edges in them are thicker compared to those of K1.
* K5 is a vertical edge filter so it highlights the vertical edges of the images when they are convoluted with K5 (`partA_task2_K5_1280x720.png` and `partA_task2_K5_1920x1080.png`).
* In task 3, K2 is also a vertical edge filter, but creates thinner edges than K5 as it is a smaller kernel. (`partA_task3_K2_640x360.png` and `partA_task3_K2_960x540.png`).
* K3 has all its elements as 1. So it behaves as an averaging filter. So the corresponding image is a uniform grayscale image (`partA_task3_K3_640x360.png` and `partA_task3_K3_960x540.png`).
* In task 3 the stride used for the convolution is 2 unlike the strides in task 1. So while convolution is performed, the kernel is shifted by 2 pixels instead of 1. So the overall output image gets scaled in size, both in height and width. So the output images of task 3 are smaller in size than the original images. The 1280x720 image becomes 640x360 image and the 1920x1080 image becomes 960x540 image.
* Because we are no performing zero padding, so the output images have got a thin black border indicating a row and column of 0 pixels.

* In part B, I did a comparison of the time taken by the convolution script for different numbers of output channels. It shows that the time taken by the the script (in seconds) grows exponentially as the number of output channels increases. The plot is shown in the figure `Part_B_Time_vs_i_1280*720.png` and `Part_B_Time_vs_i_1920*1080.png`. The script however takes a very long time to run.

* In part C, I did a comparison of the number of computations performed by the convolution script for different size of kernels. It shows that the time taken by the the script (in seconds) grows exponentially here as well, as the size of the kernel increases. The plot is shown in the figure `Part_C_Number_of_computations_vs_Kernel_size_1280*720.png` and `Part_C_Number_of_computations_vs_Kernel_size_1920*1080.png`.

* In part D, I implemented the same convolution algorithm in C language. Though C does not have the advantage of the flexibility of coding that python has, but it is a compiled code. Hence it is much faster than python. I have not used the image files in C. But I have created a random array of the same sizes (1280x720 and 1920x1080) as the images used in python. The plots show that the overall time taken by the C code for different values of the output channel, is much lower than python. Although this plot also shows that the time taken grows exponentially with the increase of output channels.
* The c_conv(...) function performs the convolution. But for that I have to send the input array into this function. So along with the given arguments, I also sent the input array pointer and the array sizes as a few more parameters into the function. The overall function declaration is like this: `double c_conv(int in_channel, long int o_channel, int kernel_size, int stride, float*** input_array, int rows, int cols)`. The return type is also double here as int cannot handle the large values corresponding to the numbe of computations measured.
* I have used a separate simple python script to plot the output data from the C code. This script being very simple is not included with the report.


