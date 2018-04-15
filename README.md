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

## Basic shite
sudo apt install -y chromium-browser
sudo apt install zsh

### Gotta write code - might as well use Sublime. 
