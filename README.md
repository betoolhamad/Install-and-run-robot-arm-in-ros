# Install ROS and run robot arm pakage
Fisrt we need to insatll ROS in ubuntu which this robot arm pakage tesetd in ROS meldoic and Ubuntu 18.04 .  
## Dependencies
 after configuration your Ubuntu, run this in terminal to accept the software from ros.org   

`sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'`    

Then run   

`curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -`

To install ROS, first you should make update of debian pakage :     

`sudo apt update` 

after that install ros Desktop-Full :  


`sudo apt install ros-melodic-desktop-full`


then enviroment setup step , run this command :

```
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc. 
source ~/.bashrc
```
and   

`source /opt/ros/melodic/setup.bash`

**Now, ROS is installed. but to install tools for building ROS pakages run :**

`sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential`. 

To use the tools of ROS, you need first to initialize rosdep, which is enable you to install the system requirments that require to run the ROS. 
run install rosdep command   :  

`sudo apt install python-rosdep`

then initialize rosdep  :  
```
sudo rosdep init
rosdep update
```

# Install and run robot arm pakage in ros

first Installing the package arduino_robot_arm by add rduino_robot_arm in src file :  
```
 $ cd ~/catkin_ws/src
 $ sudo apt install git
 $ git clone https://github.com/smart-methods/arduino_robot_arm 
```
second you must install all the dependencies to run this pakage :
	
  ```
    $ cd ~/catkin_ws
	$ rosdep install --from-paths src --ignore-src -r -y
	$ sudo apt-get install ros-melodic-moveit
	$ sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui
	$ sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher
	$ sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control
   ```
   
   **In two last commands i have problem with it, its dont't run and the soluation was run this command first to update :**
   
   `sudo apt update`
   
   and compile the package :
  
   `$ catkin_make`
   
  **Now the pakage is installed , to run robot arm pakage by Rviz, run :**
   
   `roslaunch robot_arm_pkg check_motors.launch`
   
  
   
   and to run robot arm by gazebo, run :
   
    `roslaunch robot_arm_pkg check_motors_gazebo.launch `
    
  
   **Now to control the arm by Rviz and gazebo at the same time we need to run the joint_state but may need first change the permitios :**
  
   ```
   $ cd catkin_ws/src/arduino_robot_arm/robot_arm_pkg/scripts
   $ sudo chmod +x joint_states_to_gazebo.py
   ```
   
   Then run it :
   
   `rosrun robot_arm_pkg joint_states_to_gazebo.py`
   
  







