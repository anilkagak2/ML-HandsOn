## System Requirements

+ RAM and Storage
Typically your system should have >= 16GB RAM and have enough storage to store datasets and trained models (for small datasets and casual learning you should be fine with <100GB storage). For large datasets, your personal computing PC/laptop may not be enough, in which case you'll need to rent some appropriate configuration server from cloud services like Azure/AWS/Google compute. For now, we'll go with smaller datasets and will only deal with setting that up. When we come to the large datasets, I'll setup steps.

+ Operating System 
I'll be going to use Python/Scikit-learn/Tensorflow/Pytorch combination to train models on publically available datasets. So, the choice of operating system is not that big a barrier, whatever you are comfortable with should do the job. All of these tools have sufficient documentation to setup on the choice of your operating system. The fact that you are comfortable with some operating system means that you can navigate around the documentation for these tools to install the correctly. I'll be using Ubuntu for my experiments and I would recommend using the same in case you don't have a preference.

+ Compute : CPU vs GPU
Most of the functionality offered by scikit-learn uses CPU compute only and in this case you should have no trouble using this. Although tensorflow/pytorch have support for both CPU/GPU compute, the difference between the two resources is significant, for example, training a convolutional network on CPU could take about 1 day vs the same can be done in less than an hour on GPU or may be in minutes. So if you can afford to have a GPU, please do so (for the later part where most of the training procedures are in tensorflow/pytorch). 

## Tools Installation 
+ Nvidia Driver
+ Conda Setup
+ Conda Init
+ Conda create new tensorflow and pytorch environments
+ Package installation
+ Pip usuage
+ Check if tensorflow works (cpu/gpu)
+ Check if pytorch works (cpu/gpu)
