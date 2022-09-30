# Introduction

In this work, I aim to predict the traffic flow conditions in order to identify queues and potential bottlenecks. I intend to accomplish that by employing a full harvesting device, and I need to use sub-sampling of the traffic flow in order to achieve this goal because we cannot use an acquisition device that runs continuously (2 images 1 sec sampling rate). We agree that there are roughly three levels of traffic conditions. Even though a more precise classification could be the next goal for future work, this is sufficient.

# Motivation

So far, the Uield of trafUic estimation is governed mostly by RADAR, LIDARS, GPS, and section speed measurements, but those techniques are not able to provide semantic information and they are usually expensive. Conversely, nowadays cameras are cheap and with the help of Deep Learning and computer vision techniques we are able to extract many useful information from videos or images captured by those cameras such as type of the vehicle or estimating distance between vehicles.

However, implementing Deep Learning models require a lot of resources and most projects have been tested on the servers in which there were enough GPUs and memories to run Deep Learning models. On the contrary, in this thesis we are interested in implementing Deep Learning models on small and cheap devices that are limited by the hardware and power supply and software dependencies/compatibilities.



# Platforms
Currently, this project is primarily developed for the Z2 board which has an ARM Cortex-A series processor, though it has also been tested on macOS and Linux desktop distributions such as Ubuntu and Debian. With a C++11-capable compiler, it should run on any of these. Before installing the project, you should pay attention to the list of prerequisites for the build system.

# Installation

### Build requirements for the Z2 board:

Make sure your Z2 board has all the required development libraries. If you don’t plan to use GTK+, ignore the first line from the next commands. Most of these libraries should be already installed if you are using a Z2 board or Raspberry Pi:
```cpp
sudo apt install libgtk-3-dev libcanberra-gtk3-dev
sudo apt install libtiff-dev zlib1g-dev
sudo apt install libjpeg-dev libpng-dev
sudo apt install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
sudo apt-get install libxvidcore-dev libx264-dev
```
Next, clone this repository in your local host:
```cpp
git clone https://github.com/vfarjood/traffic_estimator.git
```
Then you can use the script file to install the project:
```cpp
cd traffic_estimator
cd scripts
./install.sh
```
### Build requirements for MacOS or Linux

The only prerequisite is that your machine already includes the OpenCV library installed. After that, you just need to install the project:
```cpp
cd traffic_estimator
cd scripts
./install.sh
```

# Run

An executable file will automatically be created in the same directory, scripts, after the project has been installed using the *install.sh* script. The simplest way of running the program is to type:
```cpp
./estimate
```
You can view all the possible arguments that you can use to modify the behavior of the program by passing *-h or —help*:
```cpp
./estimate
```

With *-d or --detector* you can choose object detection model( YOLOv5n, or MobileNet_SSDv2). by defult program uses Yolo model:
```cpp
./estimate -d=mobilenet
```
With *-i or --input* you can pass input path to the program:
```cpp
./estimate -i=../media/dataset/road_1/1/
```
With *-e or --evalute* you can set the program into evaluation mode:
```cpp
./estimate -i=../media/dataset/ -d=yolo -e=true
```