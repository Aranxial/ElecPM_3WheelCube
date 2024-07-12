# Three-Wheel Cube
In this model, the Cube uses three actuator wheels (colored in <span style="color: red;">red</span>, <span style="color: yellow;">yellow</span> and <span style="color: green;">green</span>). The .SDF file creates a world with ground and the cube placed on top of it. To run, use ``ign gazebo 3wc_v1.sdf`` for ignition gazebo.

To control the speeds of each wheels, in another terminal, use the command: ``ign topic -t "/cmd_vel_$(color)" -m ignition.msgs.Double -p "data: $(velocity)"``, instead of 'color' use 'r','y' or 'g' and instead of 'velocity' use the speed you need for the wheel in 'color'.

### Viewing the .xacro file in rviz2
* Open a terminal and use the command: ``ros2 run joint_state_publisher joint_state_publisher`` (without this, the continuous/revolute joints won't work)
* In another terminal, use the command: ``ros2 run robot_state_publisher robot_state_publisher --ros-args -p robot_description:="$( xacro path/to/robot.xacro )"``. This will create a topic named 'robot_description' (can be changed).
* In another terminal, use the command: ``rviz2 view_cube.rviz`` to open the .rviz file (settings are all set).

### Spawning the cube in gazebo using the xacro file
* Open the .sdf file for creating a ground in gazebo for our cube to rest on: use ``ign gazebo ground.sdf`` (comes with lighting xD)
* Do the first two steps in the above section to create the topic 'robot_description', and then use: ``ros2 run ros_gz_sim create -topic robot_description -n my_bot`` (Note: this code is for ignition, for classic the changes are: 'ros_gz_sim' => 'gazebo_ros', 'create' => 'spawn_entity.py' and 'n' => 'entity')
* Use the command: ``ign topic -t "/cmd_vel_$(color)" -m ignition.msgs.Double -p "data: $(velocity)"`` for moving the wheels (mentioned above).
[Gazebo Classic ROS 2 Packages Migration Documentation](https://gazebosim.org/docs/fortress/migrating_gazebo_classic_ros2_packages) provides the differences in both classic and ignition commands.
