## System Requirements

#### RAM and Storage
Typically your system should have >= 16GB RAM and have enough storage to store datasets and trained models (for small datasets and casual learning you should be fine with <100GB storage). For large datasets, your personal computing PC/laptop may not be enough, in which case you'll need to rent some appropriate configuration server from cloud services like Azure/AWS/Google compute. For now, we'll go with smaller datasets and will only deal with setting that up. When we come to the large datasets, I'll setup steps.

#### Operating System 
I'll be going to use Python/Scikit-learn/Tensorflow/Pytorch combination to train models on publically available datasets. So, the choice of operating system is not that big a barrier, whatever you are comfortable with should do the job. All of these tools have sufficient documentation to setup on the choice of your operating system. The fact that you are comfortable with some operating system means that you can navigate around the documentation for these tools to install the correctly. I'll be using Ubuntu for my experiments and I would recommend using the same in case you don't have a preference.

#### Compute : CPU vs GPU
Most of the functionality offered by scikit-learn uses CPU compute only and in this case you should have no trouble using this. Although tensorflow/pytorch have support for both CPU/GPU compute, the difference between the two resources is significant, for example, training a convolutional network on CPU could take about 1 day vs the same can be done in less than an hour on GPU or may be in minutes. So if you can afford to have a GPU, please do so (for the later part where most of the training procedures are in tensorflow/pytorch). 

## Tools Installation 
+ Nvidia Driver

Installation on a Windows device should be very easy as the Nvidia driver installer takes care of most of the issues. For installation on Linux destro like Ubuntu, the newer versions of the destro makes sure you have the latest drivers installed (I would recommend using Ubuntu 20.04 or the newer version). Otherwise you are out of luck, please follow these steps 

Download the link to the nvidia driver compatible with your GPU from the official website [nvidia-drivers](https://www.nvidia.com/Download/index.aspx). 
```bash
wget <link-to-nvidia-driver-installer-sh-script>
bash <nvidia-driver-installer-sh-script>
```

Just pray that the above steps work, if not you are in for a whole day of debugging :P (I will link to places where you can look for help).

+ Conda Setup

Download the individual conda linux installer from the website [anaconda](https://www.anaconda.com/products/individual). If you are not using Linux, download the installer corresponding to your operating system.

```bash
wget <link-to-conda-installer-sh-script>
bash <conda-installer-sh-script>
```

+ Conda Init

Ideally, once the above installation is successful, you do not need to perform the conda init (at the last step the installer asks for your permission to do conda init), otherwise you need to log off from the shell and re-login. In some instances you need to edit the .bashrc to include the conda init steps (you'll need to include the conda binaries in the PATH shell variable).

+ Conda create new tensorflow environments

I am specifically installing a certain version of the tensorflow i.e. 1.15 (you can go ahead and install the latest or change the version number to your desirable version)
```bash
conda create --name tensorflow-gpu-1.15 python=3.7 tensorflow-gpu=1.15 jupyter  
conda activate tensorflow-gpu-1.15
pip install sklearn
conda deactivate 
```

+ Conda create new pytorch environments

I am specifically installing a certain version of the pytorch i.e. 1.6 (you can go ahead and install the latest or change the version number to your desirable version)
```bash
conda create --name pytorch-1.6 python=3.7 jupyter  
conda activate pytorch-1.6
conda install pytorch torchvision cudatoolkit=10.2 -c pytorch
pip install sklearn
conda deactivate 
```

+ Package installation (using conda or pip)
```bash
conda install package-name
```

```bash
pip install package-name
```

+ Check if tensorflow works (cpu/gpu)

If the following import works, then at least tensorflow installation works on cpu
```bash
conda activate tensorflow-gpu-1.15
python
import tensorflow as tf
```

If the following command works in the python shell, then your installation is using gpu
```bash
sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))
```

+ Check if pytorch works (cpu/gpu)
If the following import works, then at least tensorflow installation works on cpu
```bash
conda activate pytorch-1.6
python
import torch
```

If the following command results in True in the python shell, then your installation is using gpu
```bash
torch.cuda.is_available()
```


+ Start Jupyter notebook (local)
```bash
~/anaconda3/envs/tensorflow-gpu-1.15/bin/jupyter notebook
```

+ Start Jupyter notebook (server)
On the server machine, start the jupyter notebook server without browser and appropriate port (whatever is enabled on the server and is available for the server)
```bash
~/anaconda3/envs/tensorflow-gpu-1.15/bin/jupyter notebook --no-browser --port=8999     
```

+ Connect to server Jupyter notebook
Use the ssh to connect to the port from the server to the local port via logging into your server account
```bash
ssh -f user@server-ip-address -L 8999:localhost:8999 -N
```

Once the above step works, try connecting to the local host on the above port (you will need the token id generated by the server account)
```bash
http://localhost:8999/
```
