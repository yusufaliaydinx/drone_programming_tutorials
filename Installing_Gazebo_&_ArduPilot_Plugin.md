# Intalling Gazebo and ArduPilot Pulugin on Ubuntu 20.04

Robot simulation is an essential tool in every roboticist's toolbox.
Gazebo offers the ability to accurately and efficiently simulate populations of robots in complex indoor and outdoor environments.

## Install Required Dependencies
```
sudo sh -c 'echo "deb http://packages.osrfoundation.org/gazebo/ubuntu-stable `lsb_release -cs` main" > /etc/apt/sources.list.d/gazebo-stable.list'
```

## Setup keys and update
```
wget https://packages.osrfoundation.org/gazebo.key -O - | sudo apt-key add -
```
## Reload software list:
```
sudo apt-get update
```
## Install Gazebo 11 (for Ubuntu 20.04)
```
sudo apt-get install gazebo11 libgazebo11-dev
```
## Install Gazebo plugin for ArduPilot
```
cd ~
git clone https://github.com/SwiftGust/ardupilot_gazebo.git
cd ardupilot_gazebo
```
### Build and install plugin
```
mkdir build
cd build
cmake ..
make -j4
sudo make install
```
```
echo 'source /usr/share/gazebo/setup.sh' >> ~/.bashrc
```

### Set paths for models:
```
echo 'export GAZEBO_MODEL_PATH=~/ardupilot_gazebo/models' >> ~/.bashrc
. ~/.bashrc
```

## Run Simulator

### In first Terminal, run Gazebo:
```
gazebo --verbose ~/ardupilot_gazebo/worlds/iris_arducopter_runway.world
```
### In another Terminal, run SITL:
```
cd ~/ardupilot/ArduCopter/
sim_vehicle.py -v ArduCopter -f gazebo-iris --console --map
```