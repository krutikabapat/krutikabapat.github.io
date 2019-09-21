---
layout: post
title: "Generative-Vs-Discriminative-Models"
date: 2019-09-21
desc: "This blog post talks about the difference between Generative and Discriminative Models."
keywords: "Blog, Generative, Discriminative"
categories: [Blog, Theory]
tags: [Blog, Theory]
icon: icon-html
---



In this blog post we will be learning about Generative and Discriminiative models. Suppose that we have one model which can
learn things in-depth and thoroughly and we have another model which can learn to identify only the differences between the 
things it sees. 

For example suppose we have model A which can learn features of fruits such as color, texture, shape etc and 
other model B learns only the features which help to easily classify them like their color.

In technical terms, a Generative model learns the joint probability distribution p(x,y) and a Discriminative model learns the 
conditional probability distribution p(x|y) using Bayes theorem. For example, if you have input data x and you want to classify
it into y labels. The geneartive models learn the joint probability distribution p(x,y) and a discriminative model basically learns
the conditional probability distribution p(y|x).

##Generative Models
Since generative models model each class separately they can be trained on an individual class basis. Some of the 
examples include Naïve Bayes, Hidden Markov Models (HMM), Markov random fields

##Discriminative models 

The main aim of dicriminative models is to distinguish between classes, it needs to be trained on a
single traning set with examples of all of them. Some of the discriminative models include Conditional Random Fields (CRF)s, Logistic regression, 
Traditional neural networks and Nearest neighbour. These models are more complex than generative models. 


Also we can say that lower layers of deep neural networks can be called as generative and the upper layers often as discriminative.
