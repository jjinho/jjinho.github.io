---
layout: post
title: Diving Into Deep Learning
subtitle: Getting the system setup
---

# Building the System

After deciding to take the plunge into [Deep Learning](https://en.wikipedia.org/wiki/Deep_learning)
I used [Tim Dettmers](http://timdettmers.com/2015/03/09/deep-learning-hardware-guide/) fantastic 
post as a guide to build my machine. I ended up using the following parts:

* CPU: Intel Core i5-6500
* RAM: 16 GB
* HD: Samsung 840 Pro 128 GB SSD
* GPU: NVIDIA GTX 960 4 GB

With the hardware done I then installed the following:

* [Ubuntu 14.04 LTS](http://www.ubuntu.com/download/desktop)
* [CUDA 7.5](https://developer.nvidia.com/cuda-toolkit) [^1]
* [cuDNN R4](https://developer.nvidia.com/cudnn) [^2]

With the OS and base system then installed, Then I installed
[Torch 7](http://torch.ch/docs/getting-started.html#_). This was surprisingly
not as painful as I imagined it could have been. All software was installed in
the order described, which may have made things easier for me.



---

#### Footnotes:

[^1]: Use the directions given by [NVIDIA](http://developer.download.nvidia.com/compute/cuda/7.5/Prod/docs/sidebar/CUDA_Installation_Guide_Linux.pdf) for installing CUDA 7.5 on Ubuntu 14.04. Do not use `sudo apt-get install cuda`

[^2]: This requires registering with the NVIDIA Accelerated Computing Developer Program

