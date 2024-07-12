# Three-Wheel Cube
In this model, the Cube uses three actuator wheels (colored in <span style="color: red;">red</span>, <span style="color: yellow;">yellow</span> and <span style="color: green;">green</span>). The .SDF file creates a world with ground and the cube placed on top of it. To run, use ``bash ign gazebo 3wc_v1.sdf`` for ignition gazebo.

To control the speeds of each wheels, in another terminal, use the command: ``bash ign topic -t "/cmd_vel_$(color)" -m ignition.msgs.Double -p "data: $(velocity)"
``
