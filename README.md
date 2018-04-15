# Ubuntu-GPU-AI-Setup
Ubuntu CUDA Deep Learning GPU Setup - CUDA, cuDNN, Python 2, Python 3, TensorFlow, Theano, Keras, Pytorch, OpenCV, Dlib and more!


Assuming you are logged into your machine. You could SSH and copy and paste, but do it this way, typing everyting one, builds character, and two, allowing you to beter reackk what the fuck you're doing

## Step #1: Install Ubuntu system dependencies

Close all running applications.  
Press ctrl + alt + F1 .  
Login with your username and password.  
Stop X server by executing  
sudo service lightdm stop

Perform the install instructions.

### make sure the machine is uptodate  
sudo apt-get update  
sudo apt-get upgrade  


### Prep
$ sudo apt-get install build-essential cmake git unzip pkg-config  
$ sudo apt-get install libjpeg-dev libtiff5-dev libjasper-dev libpng12-dev  
$ sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev  
$ sudo apt-get install libxvidcore-dev libx264-dev  
$ sudo apt-get install libgtk-3-dev  
$ sudo apt-get install libhdf5-serial-dev graphviz    
$ sudo apt-get install libopenblas-dev libatlas-base-dev gfortran  
$ sudo apt-get install python-tk python3-tk python-imaging-tk  
$ sudo apt-get install python2.7-dev python3-dev  

### Prepare for Linus Torvalds' distain for nvidia (I'm just guessing)
$ sudo apt-get install linux-image-generic linux-image-extra-virtual  
$ sudo apt-get install linux-source linux-headers-generic  

## Step #2 CUDA 8: Install CUDA Toolkit - READ EVERYTHING!!!

### THESE were instructions I found here https://www.pyimagesearch.com/2017/09/27/setting-up-ubuntu-16-04-cuda-gpu-for-deep-learning-with-python/ - However, it shit the bed on me. So, if you would rather, follow the ALT Step 2. This works

pay close attention to to detail for this one or you may throw your machine out the window :) 

First disable the Nouveau kernel driver by creating a new file:  
$ sudo nano /etc/modprobe.d/blacklist-nouveau.conf  


Setup the ram file and reboot  
$ echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf  
$ sudo update-initramfs -u  
$ sudo reboot  

You will want to download the CUDA Toolkit v8.0 via the NVIDIA CUDA Toolkit website:  

https://developer.nvidia.com/cuda-80-ga2-download-archive  

Once you’re on the download page, select Linux => x86_64 => Ubuntu => 16.04 => runfile (local) .   
Make sure below is cool - and use wget just becuase  
$ wget https://developer.nvidia.com/compute/cuda/8.0/Prod2/local_installers/cuda_8.0.61_375.26_linux-run

### Extract and be patient on the last step
$ chmod +x cuda_8.0.61_375.26_linux-run  
$ mkdir installers  
$ sudo ./cuda_8.0.61_375.26_linux-run -extract=`pwd`/installers  

##  install the NVIDIA kernel driver:
$ cd installers
$ sudo ./NVIDIA-Linux-x86_64-390.48.run

## ALT Step #2 - CUDA 9.1 and WORKING!!:

It's working!! Too much to write at this second. brb 












## old ignore!
## Java - Just because. Open jdk is fine. 

sudo apt-get update

sudo apt-get install default-jdk

## NVIDIA Drivers 
### So you don't stab yourself in the face later
sudo apt-get purge nvidia*

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-396 
(at time of writing for gforce 1080)

#### reboot

### Basic shite
sudo apt install -y chromium-browser  (now we can close Firefox)
sudo apt install zsh

### Gotta write code - might as well use Sublime. Just run these 4 all at once
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -

echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list

sudo apt update

sudo apt install sublime-text

Lauch Ubuntu Software and install Guake Terminal - then everything is an f12 away. 

### Machine Learning Setup

sudo apt-get update

sudo apt-get upgrade

### swag
sudo apt-get install -y build-essential cmake gfortran git pkg-config  

sudo apt-get install -y python-dev software-properties-common wget vim

sudo apt-get autoremove

## CUDA
https://developer.nvidia.com/cuda-downloads - download the file and patches

sudo dpkg -i cuda-repo-ubuntu1604-9-1-local_9.1.85-1_amd64.deb

sudo apt-key add /var/cuda-repo-<version>/7fa2af80.pub
  
sudo apt-get update

sudo apt-get install cuda

## reboot since a new driver might be installed then test it

nvidia-smi 

## cuDNN
https://developer.nvidia.com/rdp/cudnn-download - have to join NVIDIA dev program. It's free and if you're actually reading this, you're registered. Or not. 

### unpack and install
tar xvf cudnn-8.0-linux-x64-v6.0.tgz
sudo cp -P cuda/lib64/* /usr/local/cuda/lib64/
sudo cp cuda/include/* /usr/local/cuda/include/

Update your paths
echo 'export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64:/usr/local/cuda/extras/CUPTI/lib64"' >> ~/.bashrc
echo 'export CUDA_HOME=/usr/local/cuda' >> ~/.bashrc
echo 'export PATH="/usr/local/cuda/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc


## framework dependencies
sudo apt-get update

sudo apt-get install -y libprotobuf-dev libleveldb-dev libsnappy-dev libhdf5-serial-dev protobuf-compiler libopencv-dev

### install python 2 and 3 along with other important packages like boost, lmdb, glog, blas, ass and gas.

sudo apt-get install -y --no-install-recommends libboost-all-dev doxygen
sudo apt-get install -y libgflags-dev libgoogle-glog-dev liblmdb-dev libblas-dev 
sudo apt-get install -y libatlas-base-dev libopenblas-dev libgphoto2-dev libeigen3-dev libhdf5-dev 

sudo apt-get install -y python-dev python-pip python-nose python-numpy python-scipy
sudo apt-get install -y python3-dev python3-pip python3-nose python3-numpy python3-scipy
