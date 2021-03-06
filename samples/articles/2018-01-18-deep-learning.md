---
layout: post
title: "Deep Learning"
excerpt: "Notes on deep learning methods."
categories: articles
tags: [batch-normalization, deep-learning, machine-learning]
author: jared_wood
comments:
share: true
modified: 2018-01-18
---

Table of Contents:

- [Introduction](#intro)
- [Batch normalization](#batchnorm)

<a name='intro'></a>

## Introduction

This article is a work in progress (maybe) that I'll add to here and there if I ever find the time. The overarching theme is deep learning details.

<a name='batchnorm'></a>

## Batch Normalization

### Fully-connected layer

Batch normalization for fully-connected layers is simple. Normalize the output elementwise over the minibatch. Then add two parameters for each output to scale and offset the normalized output. This scale and offset of the normalized output enables the networks to learn un-normalized featured.

### Convolutional layer

In a fully-connected layer there are two parameters (scale and offset) for each activation. It's tempting to do the same for convolutional layers. However first think what the objective of each layer is.

A fully-connected layer performs a mapping for each output unit. So if there are N outputs then there are N mappings. Batch normalization normalizes each and then scales and offsets each. As such there is one scale parameter and one offset parameter for each mapping.

A convolutional layer performs convolutions for each of the layer's convolution kernels. So if there are N convolution kernels then there are N output channels. Batch normalization normalizes each output channel and then scales and offsets each. As such there is one scale parameter and one offset parameter for each output channel of a convolutional layer (i.e. not the size of the output tensor).

