---
layout: post
title: "Learn CUDA Programming using Google Colab"
date: 2019-12-22
desc: "This blog post talks about CUDA programming using Google Colabs."
keywords: "Blog, CUDA, Google Colab, NVIDIA CUDA"
categories: [Blog, Theory]
tags: [Blog, Theory]
published: true
icon: icon-html
---

In this blog post we will learn about CUDA programming, difference between C and CUDA programming and how it is efficient. Generally these days laptop and computers have shared CPUs and GPUs in-built, but we will learn how to use Google Colabs for CUDA programming.  

## What is CUDA?  

CUDA is NVIDIA's parallel computing architecture that enables increase in computing performance by utilizing the power of GPU (Graphical Processing Unit). CUDA provides C/C++ language extension for programming and managing GPUs.  


## Structure of CUDA programming  

1. Both CPUs and GPUs are used for computations.  
2. CPU systems are referred as host and GPU systems as device.  
3. Both CPU and GPU have completely separate memory space.  
4. Serial workload is performed on CPUs and parallel computations on GPUs.  


## Difference between CUDA and C Programming

![png](https://raw.githubusercontent.com/krutikabapat/krutikabapat.github.io/master/assets/CUDA_C.png)


There are various differences between CUDA programming and C programming. Some of the following are listed below.  

1. In C programming we use general functions to perform particular tasks where as in CUDA programming __global__ specifier function is used that runs on device (GPU). It is generally invoked via host code, for example the main function in the above example, and is called as "kernel".  

2. When a kernel is invoked, its execution is provided via  <<<1,1>>>(variables) also called kernel launch. 


## Workflow in CUDA Programs  

1. Allocate memory to host and initialize the data of the host.  
2. Allocate memory to the device.  
3. Transfer the input data from host memory to device memory.  
4. Invoke or execute the kernel.  
5. Transfer the output from device memory to host memory.  


## Understanding CUDA programming with an sample code on Google Cloud  

1. Open a new file in Google Colab and change the runtime to "GPU".    

2. Uninstall any previous versions of CUDA, if any completely using below commands.        

      ```
                  !apt-get --purge remove cuda nvidia* libnvidia-*
                  !dpkg -l | grep cuda- | awk '{print $2}' | xargs -n1 dpkg --purge
                  !apt-get remove cuda-*
                  !apt autoremove
                  !apt-get update
       ```

3. Install CUDA 9.0/10.0         

```
!wget https://developer.nvidia.com/compute/cuda/9.2/Prod/local_installers/cuda-repo-ubuntu1604-9-2-local_9.2.88-1_amd64 -O cuda-repo-ubuntu1604-9-2-local_9.2.88-1_amd64.deb
!dpkg -i cuda-repo-ubuntu1604-9-2-local_9.2.88-1_amd64.deb
!apt-key add /var/cuda-repo-9-2-local/7fa2af80.pub
!apt-get update
!apt-get install cuda-9.2
```

4. Check version of CUDA installed with the following command:     

```
!nvcc --version
```

The shell result would look like as follows:    

![png](https://raw.githubusercontent.com/krutikabapat/krutikabapat.github.io/master/assets/CUDA_version.png)

5. Execute the given command to install a small extension to run nvcc from Google Colab notebook cells.  

```
!pip install git+git://github.com/andreinechaev/nvcc4jupyter.git
```

6. Load the extension using the following command:  

```
%load_ext nvcc_plugin
```

7. Now we will look on a simple CUDA code to understand the workflow.  

   7.1)  To run CUDA C/C++ code in google colab notebook, add the %%cu extension at the beginning of your code.
   
   ![png](https://raw.githubusercontent.com/krutikabapat/krutikabapat.github.io/master/assets/CUDA_libraries.png)
   
   7.2) __global__ function device (GPU) to execute the multiplication of two variables.  
   
   ![png](https://raw.githubusercontent.com/krutikabapat/krutikabapat.github.io/master/assets/CUDA_global.png)
   
   7.3) Declare variables for host and device.  
   
   ![png](https://raw.githubusercontent.com/krutikabapat/krutikabapat.github.io/master/assets/CUDA_host.png)
   
   7.4) Allocate memory for device variables and define variable values.  
   
   ![png](https://raw.githubusercontent.com/krutikabapat/krutikabapat.github.io/master/assets/CUDA_space.png)
   
   7.5) Copy input variables from host to device.    
   
   ![png](https://raw.githubusercontent.com/krutikabapat/krutikabapat.github.io/master/assets/CUDA_input_device.png)
   
   7.6) Launch the kernelto carry out the operations.  
   
   ![png](https://raw.githubusercontent.com/krutikabapat/krutikabapat.github.io/master/assets/CUDA_kernel.png)
   
   7.7) Copy the result back from device to host.  
   
   ![png](https://raw.githubusercontent.com/krutikabapat/krutikabapat.github.io/master/assets/CUDA_copyback.png)
   
   7.8) Free up the memory.   
   
   ![png](https://raw.githubusercontent.com/krutikabapat/krutikabapat.github.io/master/assets/CUDA_freeup.png)
   

## Advantages of CUDA Programming:  


1. CUDA is majorly parallel hardware designed to run generic (non-graphic) code, with appropriate drivers for doing so.  

2. CUDA is programming language based on C for programming and an assembly language that other programming languages can use as a target.  

3. A software development kit that includes libraries, various debugging, profiling and compiling tools, and bindings that let CPU-side programming languages invoke GPU-side code.   

4. The point of CUDA is to make us enable to write compatible massive parallel codes for SIMD architectures.  


## References:  

1. [CUDA C/C++ Basics by Cyril Zeller, NVIDIA](http://www.int.washington.edu/PROGRAMS/12-2c/week3/clark_01.pdf)
2. [Stack overflow](https://stackoverflow.com/questions/9846523/explanation-of-cuda-c-and-c)
3. [Documentation](https://cuda-tutorial.readthedocs.io/en/latest/tutorials/tutorial01/)


   
   
   
   
   



  `








