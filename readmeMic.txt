In NON-ROS environment:
	==>make px4_sitl_rtps gazebo [jmavsim]
	====>>commander takeoff
	====>>micrortps_client start
	==>make px4_sitl jmavsim
	====>>with version master is ok
	====>>with version v1.10.2: doesn't work
	====> Issue with java - Solve with https://github.com/PX4/jMAVSim/issues/96


micrortps_client start -t UDP

In test directory, there is rostest_px4_run.sh in order to work with ROS and gazebo

create application from idl:
cd ~/Firmware/build/px4_sitl_rtps/src/modules/micrortps_bridge
mkdir micrortps_listener
cd micrortps_listener
fastrtpsgen -example x64Linux2.6gcc ../micrortps_client/micrortps_agent/idl/sensor_combined.idl
make -f makefile_x64Linux2.6gcc
bin/x64Linux2.6gcc/sensor_combined_PublisherSubscriber subscriber
