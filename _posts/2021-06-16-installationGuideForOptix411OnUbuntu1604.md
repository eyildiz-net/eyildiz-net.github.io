---
id: 1
title: 'Installation guide for OptiX 4.1.1 on Ubuntu 16.04'
date: 2021-06-16
author: Ersin
excerpt: This post is a guide which would help you to save your time while installing Optix on your system.

permalink: /posts/2023/1/installationGuideForOptix411OnUbuntu1604// 
redirect_from:
  - /wordpress//2023/1/installationGuideForOptix411OnUbuntu1604/
  - /wordpress/?p=1
categories:
  - category1
  - category2
tags:
  - tag1
  - tag2
---
This post is a guide which would help you to save your time while installing Optix on your system. It is assumed that you have a Linux distribution Ubuntu 16.04. Installation Optix has several main steps. First, NVIDIA graphic driver has to be installed. Then, a compatible version of CUDA (here, version 10.1) and a compatible version of OptiX (here, version 4.1.1) will be installed. It is necessary that versions of display driver, CUDA and Optix are compatible in between and with your graphic card architecture. To get information regarding this, you can check out their release notes.

**Graphic Card Driver Installation**

Mostly, old versions of Cuda and Optix are compatible with the latest versions of NVIDIA graphic card driver. Find the latest driver for your graphic card [here](https://www.nvidia.com/Download/index.aspx?lang=en-us) and download it. Do not forget to chose correct operating system.

Go to Download directory in terminal and follow the commands.

```
cd Downloads
ls
NVIDIA-Linux-x86_64-450.57.run # output of ls
chmod +x NVIDIA-Linux-x86_64–410.57.run # get permission to execute it
```

Now we will switch text console by pressing ctrl+alt+F4. Log in there and change directory into Downloads again. Run the driver file as follows.

```
sudo ./NVIDIA-Linux-x86_64–410.57.run — no-x-check
```

If you omit --no-x-check it will throw you an error saying that X-Server needs to be disabled before installing the drivers. Mostly you did not have an installed graphic driver on Ubuntu 16.04 before installation, everything is okey. However, if you had an installed graphic driver somehow (e.g if you are on Ubuntu 18.04), you need to uninstall that and reboot by sudo nvidia-uninstall and reboot.

In installation process you encounter with some questions. Choose *Yes* to install Nvidia 32-bit compatible libraries. Choose *Continue installation* when it says “*The distribution-provided pre-install script failed!*“. Choose *No* when it asks *to run nvidia-xconfig utility to automatically update* bla bla bla. Then, driven should have been installed successfully. Verify installetion by running the nvidia-smi command on a terminal. You should see your installed version as an output.

## Installing CUDA 10.1

Go to [CUDA web site](https://developer.nvidia.com/cuda-10.1-download-archive-base). Choose Linux operating system. Choose your architecture, most probably *x86_64*. Then choose Ubuntu 16.04.

![https://static.wixstatic.com/media/b335a8_e8e5c53708694f80a293f7d817236e09~mv2.png/v1/fill/w_740,h_193,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/b335a8_e8e5c53708694f80a293f7d817236e09~mv2.png](https://static.wixstatic.com/media/b335a8_e8e5c53708694f80a293f7d817236e09~mv2.png/v1/fill/w_740,h_193,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/b335a8_e8e5c53708694f80a293f7d817236e09~mv2.png)

Installer type for CUDA installation.

There are 4 types of installation ways provided by NVIDIA. The choice is yours but here we prefered runfile (local) type. Download the installer file after you choose it. Once download is done, go to Downloads directory, run the file and follow the instructions in the command line prompt.

```
cd Downloads
sudo sh cuda_10.1.105_418.39_linux.run
```

To verify CUDA installation, we may try to run CUDA tutorials. Another thing is, after CUDA installation, CUDA version should appear in the output of nvidia-smi.

## Building OptiX 4.1.1

OptiX version 4.1.1 is released in 2017, so it is old. [This](https://developer.nvidia.com/designworks/optix/downloads/legacy) page includes both current and old versions of OptiX. Select 4.1.1 and choose Linux distribution. At that point, you must login with your NVIDIA account. The file *NVIDIA-OptiX-SDK-4.1.1-linux64-22553582.sh* is going to be downloaded.

It does not matter where you download and build OptiX, but for convenience, download it to home directory. Get it run permission if it has not. Then run *.sh* file.

```
sh NVIDIA-OptiX-SDK-4.1.1-linux64-22553582.sh
```

Once it is finished, you get a folder named *NVIDIA-OptiX-SDK-4.1.1-linux64*. The installation instructions are given in *INSTALL-LINUX.txt* file at directory *~/NVIDIA-OptiX-SDK-4.1.1-linux64/SDK*.

You need to have Cmake 3.0 (minimum) and C++ compiler built in your system. Cmake can be downloaded and installed from its [website](https://cmake.org/download/) or from a terminal by sudo apt-get install cmake command. C++ compiler should have been built in your environment by default. Following instructions for building OptiX are pretty straigthforward and codumented step by step in *INSTALL-LINUX.txt* file.

To verify OptiX built and run the tutorials, in terminal, go to the directory that you have created at step 1 in *INSTALL-LINUX.txt*. Then go to bin directory. Run anyone of the executables in bin directory from the terminal.

**Note:** This post will be improved by screenshots and detailed explanations.