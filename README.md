# sirl_carla_sim
Gazebo is too generic of a tool, needs a lot of work to get it doing what we want it to for simulating vehicles 

Choosing CARLA (https://carla.org/)
- under active development 
- many more vehicle sim tools out of the box
- has ROS bridge ability 

# Install Carla 

```sh 
# upgrade Python 3
pip3 install --upgrade pip

# install pygame
pip install --user pygame numpy &&
pip3 install --user pygame numpy

# installing CARLA
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1AF1527DE64CB8D9
sudo add-apt-repository "deb [arch=amd64] http://dist.carla.org/carla $(lsb_release -sc) main"

sudo apt-get update # Update the Debian package index
sudo apt-get install carla-simulator # Install the latest CARLA version, or update the current installation
cd /opt/carla-simulator # Open the folder where CARLA is installed

apt-cache madison carla-simulator # List the available versions of Carla

sudo apt-get install carla-simulator=0.9.10-1 # In this case, "0.9.10" refers to a CARLA version, and "1" to the Debian revision
# this line didn't work for me for some reason (probably because 0.9.10-1 was not listed as an available version for me) 

# sometimes issues show up if you don't install vulkanutils 
# for me, this caused CARLA to crash often but inconsistently without this package 
# solution as found here: https://github.com/carla-simulator/carla/issues/2138 
sudo apt install vulkan-utils

# Running CARLA server 
# can use WASD and mouse to navigate from floating camera perspective around the simulated world 
cd /opt/carla-simulator/
./CarlaUE4.sh
```

### In a new terminal
```sh
cd PythonAPI\examples

python3 -m pip install -r requirements.txt # Support for Python2 is provided in the CARLA release packages

# this cmd generates traffic and pedestrians in the world 
python3 generate_traffic.py  
```

### In a new terminal
```sh
cd PythonAPI\examples

# this cmd opens the client for CARLA
# can manually control the vehicle with your keyboard 
python3 manual_control.py 
```
