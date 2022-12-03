# Intalling QGroundControl on Ubuntu 20.04

It is Ground Control Station for the MAVLink protocol.

Before installing QGroundControl you should remove the modem manager and grant yourself permissions to access the serial port. \
You also need to install GStreamer in order to support video streaming.
```
sudo usermod -a -G dialout $USER
sudo apt-get remove modemmanager -y
sudo apt install gstreamer1.0-plugins-bad gstreamer1.0-libav gstreamer1.0-gl -y
sudo apt install libqt5gui5 -y
sudo apt install libfuse2 -y
```

## Download QGroundControl.AppImage
```
wget https://s3-us-west-2.amazonaws.com/qgroundcontrol/latest/QGroundControl.AppImage
```

## Change permissions and run
```
chmod +x ./QGroundControl.AppImage 
./QGroundControl.AppImage
```

## Run SITL and connect with QGroundControl
```
cd ~/ardupilot/ArduCopter/
sim_vehicle.py -w --console --map
```