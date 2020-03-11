---
layout: post
title:  "Cover Song Identifcation"
date:   2020-03-04 13:45:37 +0100
categories: introduction cover-song-identification
comments: true
feature_image: "/aiblog-timo/assets/stage.jpg"
---

Cover song identification is the task of identifiying the original song, given an arbitary cover song of it. Or a more general definition would be: Given a query song, find other songs of the same composition. 

Take "twinkle twinkle little star" as an example. If someone sings or humms this melody, humans will most likely be able to identify it without doubt. However, for computers this is a really hard task. Recordings of covers might differ in tempo, key or structure. Also the quality of the recording might differ and all kinds of noise can make it even harder to correctly identify the recording.

The MIREX conference hosts a yearly [competition for cover song identification](https://www.music-ir.org/mirex/wiki/2019:Audio_Cover_Song_Identification) that provides some interesting problems and solutions.

In this seminar I'll be looking at the paper [Temporal Pyramid Pooling Convolutional Neural Network for Cover Song Identification](https://www.ijcai.org/Proceedings/2019/0673.pdf), that was chosen as winner of the MIREX 2019 Cover Song Identification challenge.

In the coming weeks I will blog about the topic of cover song identification in general and about the mentioned paper and the solution described in it. Also I have some ideas, on what to build with this technology...
