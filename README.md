# Dual arm set up with Universal Robots (default UR3e)
<img src="https://github.com/cambel/dual_ur3e/blob/main/docs/dual_ur3e.png?raw=true" alt="Dual UR3e & Robotiq Hand-e" width="500">


ROS-Melodic, Gazebo, and MoveIt configuration for dual configuration with UR3e (or any other UR robot)

## Installation
### Prerequisites
- Install Docker
- Install Docker-compose
- Install nvidia-docker2

Detailed instruction can be found [here](https://github.com/cambel/ur3/wiki/Install-with-Docker)

### Clone and build

Clone this repository
```shell
git clone https://github.com/cambel/dual_ur3e.git
```

Build Docker container
```shell
cd dual_ur3e
./BUILD-DOCKER-IMAGE.sh
```

Run container (reconnect to container with new terminals with this same script)
```shell
cd dual_ur3e
./RUN-DOCKER.sh
```

## Example
### Launch the Gazebo environment (Environment is a custom build of my lab)
Execute the following command
```shell
roslaunch ur3e_dual_gazebo dual_ur3e_hlab.launch 
```

By default the robot used are the UR3e, but other UR robots can be easily set up by changing the argument `ur_robot`, valid option (ur3, ur5, ur10, ur3e, ur5e, ur10e)
```shell
roslaunch ur3e_dual_gazebo dual_ur3e_hlab.launch ur_robot:=ur5e
```

### Launch MoveIt
Execute the following command
```shell
roslaunch ur3e_dual_moveit_config start_sim_dual_ur3e_moveit.launch 
```

### Change the simulation environment
Update the URDF description of the environment `ur3e_dual_gazebo/urdf/dual_ur_gripper_hande.xacro` or create your own one 



