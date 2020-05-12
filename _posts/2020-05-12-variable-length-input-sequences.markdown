---
layout: post
title:  "The problem of variable-length input sequences in neuronal networks"
date:   2020-05-12 20:45:37 +0100
categories: technical cover-song-identification
comments: true
feature_image: "/aiblog-timo/assets/length.jpg"
---

In this blog-post, I'm going to write about the content of the paper [Temporal Pyramid Pooling Convolutional Neural Network for Cover Song Identification](https://www.ijcai.org/Proceedings/2019/0673.pdf). In the previous blog-post, I analyzed the general writing style of the paper. This time, I will walk you through the technical details of the paper and also explain the related topics.


### Required Previous Knowledge

Before I talk about the content of the paper, I have to explain the concept of [Spatial Pyramid Pooling](https://arxiv.org/pdf/1406.4729.pdf) used in Convolutional Neuronal Networks (CNN) for image processing:
Usually, CNN architectures apply a series of convolutional layers, followed by a few fully connected layers. The convolutional layers could, in theory, work with any input size, since it is just sliding a window across the input and a calculation of the dot product. However, the fully connected layers need a fixed-size input, and therefore the input size of the whole network is usually also fixed. The idea of Spatial Pyramid Pooling (SPP) is to insert a new layer between the convolutional layers and the fully connected layers, that will output a fixed-size representation. 

> SPP works by dividing the feature maps output by the last convolutional layer into a number of spatial bins with sizes proportional to the image size, so the number of bins is fixed regardless of the image size. Bins are captured at different levels of granularity – for example, one layer of 16 bins dividing the image into a 4×4 grid, another layer of 4 bins dividing the image into a 2×2 grid, and a final layer comprising the whole image. In each spatial bin, the responses of each filter are simply pooled using max pooling. Since the number of bins is known, we can just concatenate the SPP outputs to give a fixed-length representation.
([source](https://blog.acolyer.org/2017/03/21/convolution-neural-nets-part-2/))

The idea can be visualized with the following picture from their paper:

![](/aiblog-timo/assets/spatial.jpeg)

Spatial pyramid pooling had a pretty big impact on the field of image recognition. The paper has been cited over 4000 times. Side note: In my previous blog-post, I linked to a different, less known, paper regarding pyramid pooling and blamed the authors of the analyzed paper for assuming that the readers are familiar with the topic. Having found the correct paper now, I revise my statement, and I think their assumption is fair.

### Temporal pyramid pooling for sound files

Now that we know what spatial pyramid pooling is, we can look at the content of the paper I'm analyzing during this semester.

Neuronal networks that analyze songs suffer from a similar problem like neuronal networks that analyze images: The input sizes are varying; for example, multiple images have different resolutions and multiple sounds different durations. Conventional solutions for cover song identification just cropped or stretched the songs to a fixed size. The authors of the paper at hand have instead transferred the idea of spatial pyramid pooling into the temporal domain. The following picture from their paper illustrates the idea:

![](/aiblog-timo/assets/temporal.png)

Feature maps from different time intervals are max pooled into bins. Like in the case of SPP, bins are captured at different levels of granularity, and the sizes of the bins are proportional to the duration of the input song. As output, the temporal pyramid pooling layer yields a fixed-size representation of a song.

The application of pyramid pooling to generate fixed-size representations of a song is the novelty and contribution of this paper. The authors also show how to ensure the trained network becomes invariant of the input length. Of course, there are other things around it, like how to prepare the data and how to compute the similarity of song representations. However, there are many papers about that, and the paper at hand does not provide much new insight there. The authors show that their approach performs much better than other state-of-the-art methods on public datasets and is also pretty robust against musical variations. The section about the experimental results and their analysis is pretty thorough, and it becomes clear that the paper does indeed provide quite some scientific value. The paper was published in August 2019, and since then, four other papers have cited it, and I think more are to follow.

I can clearly recommend reading the paper if you have some spare minutes. The topic of cover song identification is nicely explained, and also the rest is easy to understand once you have the required previous knowledge about SPP. 
