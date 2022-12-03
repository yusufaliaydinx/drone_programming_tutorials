# Installing Ardupilot and MAVProxy on Ubuntu 20.04

## Installing Git
```
sudo apt update

sudo apt install git

git --version
```

## Clone ArduPilot
```
git clone https://github.com/ArduPilot/ardupilot.git

cd ardupilot
```

## Install dependencies:
```
cd ardupilot

Tools/environment_install/install-prereqs-ubuntu.sh -y

git submodule update --init --recursive
```

## reload profile
```
. ~/.profile
```

## Check SITL (Software In The Loop):
```
cd ~/ardupilot/ArduCopter

sim_vehicle.py -w --console --map
```