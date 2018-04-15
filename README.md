# Ubuntu-GPU-AI-Setup
Ubuntu Deep Learning GPU Setup - CUDA, cuDNN, Python 2, Python 3, TensorFlow, Theano, Keras, Pytorch, OpenCV, Dlib and more!


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

SETUP --
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

test it

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
