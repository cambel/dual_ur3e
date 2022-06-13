# Dual arm set up with Universal Robots (default UR3e)
ROS-Melodic, Gazebo, and MoveIt configuration for dual configuration with UR3e (or any other UR robot)

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



