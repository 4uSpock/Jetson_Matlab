
# Steps to be able to execute the Jetson and Deep Learning libraries in MatLab
The following are steps you need to take to install and run the the Deep Learning libraries, and prepare for generating and executing on a Jetson hardware piece.

_Sidenote: during the process I've done a fresh new installation of MatLab R2023b, as I did not have it on the tested computer._

## Step 1 - Downloading Microsft Visual Studio

The visual studio environment contains the required compiler for some of the MATLAB packages we'll install.

According to the official MATLAB [site](https://www.mathworks.com/help/gpucoder/gs/install-prerequisites.html) only the 2017, 2019, 2020 versions are supported. 
Please note that every version of VS (Community, Professional, Enterprise) should be able to provide the necessary compiler.
Personally, I've used the *_2022 Community Edition_*.
- In the package selector, install the *Desktop development with C++* package.

## Step 2 - Downloading and Installing the CUDA toolkit.
- Download the relevant CUDA Toolkit [here](https://developer.nvidia.com/cuda-downloads)

There are two kinds of downloads:

1. **exe(local)** - Downloads all the required files first, and then, subsequently, installs them. I wouldn't recommend this option, as it requires a very reliable browser.

2. **exe(network)** - Downloads a small file, that includes a special helper that downloads all the required (& selected files) from the Nvidia servers. I would recommend this option as it allows for greater control and overall stability.  
(My version is 12.1.66, a.k.a 12.1)

###  TAKE NOTE OF WHERE YOU INSTALL THE CUDA DRIVERS - MAKE SURE YOU SELECT THE DEFAULT LOCATION


## Step 3 - Downloading and Installing cuDNN

- Download the relevant cuDNN library [here](https://developer.nvidia.com/cudnn-downloads?target_os=Windows&target_arch=x86_64&target_version=10). Make sure that the CUDA version you've selected, matches the cuDNN version you download. I would not recommend downloading the latest version. Let it sit for a while. I have v8.9.7.29 downloaded.
- You may check the compatibility [here](https://docs.nvidia.com/deeplearning/cudnn/reference/support-matrix.html).

 _Sidenote: you can access archive installations [here](https://developer.nvidia.com/rdp/cudnn-archive)_.
 - After downloading the matching cuDNN library - it will come in a zip file. Follow the steps:
	1. Extract the zip file into a folder with the same name (or any other folder).
	2. Remind yourself of where you've installed the CUDA Toolkit. 
	3. Copy all the files from the extracted folder, and place them in the same directory as your CUDA Toolkit files (_e.g. C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.1_). If a message asking what to do about the double _LICENSE_ files shows up (skip, replace) choose **skip**. 

## Step 4 - Downloading and Installing the relevant Matlab packages

- All but few *must have* packages are stated in the official MATLAB page [here](https://www.mathworks.com/help/gpucoder/gs/install-prerequisites.html). However, not all are necessary, and it would depend on the intended use.

The following are the packages and software I've installed in MATLAB:

 **SELECT IT** - means I've selected it during the intallation process of MatLab. However, the packages can be also found in the **Home->Add-Ons** menu. I would recommand searching it for all the relevant packages, even those I've added a link to. The link is simply a direct download of the package (which when clicked upon, is followed by the download, and installations of  the package into the MatLab environment).

 1.   MATLAB®  (required) - the basic program installation.
    
2.   MATLAB Coder™  (required) - a package that's selected in the **_Add-On_** menu, or the list when installing MATLAB from scratch. **SELECT IT.**
    
3.   Parallel Computing Toolbox™ (required) - a package. **SELECT IT.**
    
4.   Simulink®  (required for generating code from Simulink models) - didn't install it.
    
5.   Computer Vision Toolbox™ (recommended) - a package. **SELECT IT.**
    
6.   Deep Learning Toolbox™ (required for deep learning). **SELECT IT.**
    
7.   Embedded Coder®  (recommended). **SELECT IT**
    
8.   Image Processing Toolbox™ (recommended). **SELECT IT.**
    
9.   Simulink Coder  (required for generating code from Simulink models) - your choice.
    
10.   GPU Coder Interface for Deep Learning  support package (required for deep learning) - **SELECT IT.** 
Alternatively, can be found [here](https://www.mathworks.com/matlabcentral/fileexchange/68642-gpu-coder-interface-for-deep-learning).
    
11.   MATLAB Coder Support Package for NVIDIA®  Jetson™ and NVIDIA DRIVE®  Platforms  (required for deployment to embedded targets such as NVIDIA Jetson and Drive).

The package names are: 
-  MATLAB Coder Support Package for NVIDIA Jetson and NVIDIA DRIVE Platforms
- NVIDIA Jetson Support from MATLAB Coder

	- Alternatively, install the packages using the links [here](https://www.mathworks.com/matlabcentral/fileexchange/68644-matlab-coder-support-package-for-nvidia-jetson-and-nvidia-drive-platforms) and [here](https://www.mathworks.com/hardware-support/nvidia-jetson.html). Usually, the first one is enough to make it work.

## Step 5 - Checking that Nvidia CUDA and cuDNN software packages are configured correctly.
- To check if all libraries were installed and configured successfully run the following command for the *GPU Coder GUI* to appear.

		gpucoderSetup

	- You may run the command in the *Command Window* as well.

A window opens.

**Do the following:**
1. In the lower half of the window - remap your *cuDNN* directory to the same path as your CUDA library (since you've put them in the same folder). Do this by pressing the button located to the right of the row where the path is written (looks like a folder with an arrow).
2. Tick the box that has - **_Deep Learning Code Generation_** written near it.
3. Select the **Target** as **cuDNN**.
4. Select **Generate and Execute** option.
5. Click **Run Checks** which is situated in the lower half of the window.
6. A report window should pop up saying that all's well.

Now we know that our PC can make complicated _Deep-learning_ calculations.

## Step 5 - Checking that the Nvidia Jetson configuration software is configured correctly - only with a Jetson device present.

1. In the **Select Hardware** option, select **_Jeston_**.
- If you spot any changes in the other configurations - **repeat steps 2-4** of the *Step 3* section.
2. Click the **Run Checks** option.

<br /> <br />

Helpful Guides:
- Installing CUDA and cuDNN on Windows and Linux - [here](https://medium.com/geekculture/install-cuda-and-cudnn-on-windows-linux-52d1501a8805).
- Installing Pytorch, CUDA and cuDNN on Windows - [here](https://medium.com/@harunijaz/a-step-by-step-guide-to-installing-cuda-with-pytorch-in-conda-on-windows-verifying-via-console-9ba4cd5ccbef).
