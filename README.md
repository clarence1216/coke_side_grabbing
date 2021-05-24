# MAEG5755 Robotics project - grab coke side approach

## Demo video: https://youtu.be/nHb8g3WbcAM

## To start, please follow the step: 

#### Initial setup for create a new workspace (grabcoke_ws): 
```
source /opt/ros/noetic/setup.bash
cd
mkdir -p ~/grabcoke_ws/src
cd ~/grabcoke_ws/
catkin_make
source ~/grabcoke_ws/devel/setup.bash
```

#### Git clone coke_side_grabbing package to the src directory: 
```
cd ~/grabcoke_ws/src
git clone https://github.com/clarence1216/coke_side_grabbing.git
cd ~/grabcoke_ws/
catkin_make
source ~/grabcoke_ws/devel/setup.bash
```

#### Moving the baxter.sh file from src directory to workspace directory: 
```
cd ~/grabcoke_ws/src/coke_side_grabbing/
mv baxter.sh ../../
```

#### Add permission, run and setup network configuration for Baxter simulation: 
```
cd ~/grabcoke_ws/
chmod +x baxter.sh
./baxter.sh sim
export ROS_HOSTNAME=localhost
export ROS_MASTER_URI=http://localhost:11311
```

## To run the simulation, please open 3 terminals and follow the step: 

#### Terminal 1: Launch Baxter urdf model into Gazebo simulator: 
```
cd ~/grabcoke_ws/
./baxter.sh sim
export ROS_HOSTNAME=localhost
export ROS_MASTER_URI=http://localhost:11311
roslaunch baxter_gazebo baxter_world.launch
```

#### Terminal 2: Append table and coke can sdf model into Gazebo simulator: 
```
cd ~/grabcoke_ws/
./baxter.sh sim
export ROS_HOSTNAME=localhost
export ROS_MASTER_URI=http://localhost:11311
roslaunch exmpl_models add_table.launch
roslaunch exmpl_models add_can.launch
```

#### Terminal 2: Launch object grabber action server node: 
```
roslaunch baxter_launch_files baxter_object_grabber_nodes.launch
```

#### Terminal 3: Run object grabber action client to perform coke can side approach grasping: 
```
cd ~/grabcoke_ws/
./baxter.sh sim
export ROS_HOSTNAME=localhost
export ROS_MASTER_URI=http://localhost:11311
rosrun object_grabber example_object_grabber_action_client
```

## To download the original repo: learning_ros_noetic & learning_ros_external_packages_noetic, please run: 

```
git clone https://github.com/rojas70/learning_ros_noetic.git
git clone https://github.com/rojas70/learning_ros_external_pkgs_noetic.git
```
