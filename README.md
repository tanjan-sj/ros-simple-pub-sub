# Publisher Subscriber with ROS

## Environment setup for Ubuntu 20.04

This repo follows ROS Noetic.

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt install curl # if you haven't already installed curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
sudo apt update
sudo apt install ros-noetic-desktop-full
```
If you're using bash:

```
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
For zsh:
```
echo "source /opt/ros/noetic/setup.zsh" >> ~/.zshrc
source ~/.zshrc
```

```
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
sudo apt install python3-rosdep
sudo rosdep init
rosdep update
```

Check to ensure if all environment variables are set up :
```
printenv | grep ROS
```

We'll use catkin for this project. Create and build a catkin workspace by running the following commands :

```
mkdir -p ~/catkin_ws
cd ~/catkin_ws/
catkin_make
```

## Run the code

```
roscd beginner_tutorials
cd scripts
chmod +x talker.py
chmod +x listener.py
```

Navigate to <tt>catkin_ws/src/beginner_tutorials</tt> and add the following lines to <tt>CMakeLists.txt</tt> :
```
catkin_install_python(PROGRAMS scripts/talker.py scripts/listener.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
```

Now navigate to the catkin workspace and build : 
```
cd ~/catkin_ws
catkin_make
```

Now, run the code using following steps :

1. Open a terminal, run <tt>roscore</tt>
2. Open a new terminal, run <tt>source ./devel/setup.bash && rosrun beginner_tutorials talker.py</tt>
3. Open another terminal, run <tt>source ./devel/setup.bash && rosrun beginner_tutorials listener.py</tt>


