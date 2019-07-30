---
layout: post
title: "Introduction to MobileNet v1 using Separable Convolution"
date: 2019-07-09
desc: "This blog post talks about MobileNet v1 and the differences between simple convolution and depth wise separable convolution"
keywords: "MobileNet, Blog, Depth wise separable convolution, CNN"
categories: [Blog, Theory]
tags: [Blog, Theory]
icon: icon-html
---


In this blog post we will be focusing on MobileNet v1 using Separable Convolutions. Also we will focus on the differences between normal convolutions and separable convolutions and differences between their memory consumptions.

There are two types of CNN:-

1. Simple Convolutional neural netwroks
2. Depth wise separable convolutional networks

In most of the cases we use simple convolutional networks, but in wide range of cases we require to deploy them into mobile applications, for which we need to reduce the computations.

There are majorly two dis-advantages of simple convolutional networks:-

1. It contains much more number of parameters, which increases overfitting in most of the cases.
2. They are computationally expensive because of large number of computations and hence cannot be used for mobile applications.

To overcome these advantages, Google proposed two networks namely MobileNet and Xception. In this blog, we will focus on the type of convolutions used in MobileNetv1 i.e depth wise separable convolutional networks.

First, we will find how computationally expensive simple convolutional networks are:-

Suppose, we have input data of size PxPxM, where PxP is the image width and image height and M is the number of channels. Also suppose we have N kernels of size KxKxM. After convolution operation is done, the output size will be RxRxN where R is the output image width and height of the image.






The number of operations performed per convolution will be KxKxM, which is the size of the filter itself.
Total number of operations is (Number of operations per convolution)* (RxRxN) = (KxKxM)*(RxRxN).

Depth Wise Separable Convolutions:- It has two major components. The first one is Depth-wise convolution and the second one is Point-wise convolution.

1. Depth-wise convolution

In this type, convolution is applied to a single channel at a time and not like the simple convolutions in which it is done for all the channels together.
So here for each convolution,the kernel used is of size K x K x 1. If the number of channels in input image is M, then M such kernels will be used. The output size will be of size R x R x M.










A single convolution would require KxK operations.
Since the filter is slided R x R x M, times total cost of operation is RxRxMxKxK.



2. Point-wise convolution

In point-wise operation, a 1 × 1 convolution operation is applied on the M channels. So the filter size for this operation will be 1 x 1 x M. Say we use N such filters, the output size becomes R x R x N.
A single point-wise convolution require 1xM operations
Since the filter is slided  PxP times, total number of multiplications is MxPxPxN.



Total time complexity for Depth separable convolutions is sum of computations required in depth wise and point wise convolutions.
MxPxPx(RxR + N)

Total complexity for standard convolutions is NxPxPxRxRxM.

From the above we can find that depth wise convolution network performs 100 times lesser multiplications as compared to standard convolutions.

MobileNet v1:











MobileNet released by Google, is majorly used for mobile applications. The following figure shows the comparison between different netwroks and how MobileNet outperforms it.











