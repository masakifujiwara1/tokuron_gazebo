# tokuron_gazebo
## usage with dokcer 
- Initial
```
git clone -b tokuron https://github.com/masakifujiwara1/ros2_docker.git
cd ros2_docker
./run.sh
```
- After the first time
```
docker start my-tokuron
./login.sh
```
- Docker Inside
※Use multiple terminals and execute the following commands in each terminal. (tmux is available. However, you can use a new terminal to run ros2_docker's . /login.sh on the new terminal).
```
ros2 launch tokuron_gazebo multi_turtlebot3_world_4.launch.py 
ros2 run apriltag_ros apriltag_node --ros-args -r image_rect:=/camera/image_raw -r camera_info:=/camera/camera_info --params-file `ros2 pkg prefix apriltag_ros`/share/apriltag_ros/cfg/tokuron.yaml
ros2 run tf2_ros static_transform_publisher 0 0 1.7 0 3.14 0 map link
```
To operate multiple robots, use the following commands or rewrite the contents of the robot.
```
ros2 run multi_twist multi_twist_node
```
