# converyor_control
## Setup for ufactory conveyor
### Online manual (ufactory conveyor)
- https://github.com/uArm-Developer/Controller/blob/master/doc/uArmController%20User%20Manual(Geek%20Edition)20181228V1.0.1.pdf

### Setup
- Arduino setup
  1. Install arduino ide
  2. Install u8glib
  3. Write sketchbook to controller
    - 以下のsketchbookをcontroller (arduino mega)へ書き込む
    - https://github.com/asanolab/Controller/blob/devel/scene_demo/conveyor_belt/src/conveyor_belt/conveyor_belt.ino

- ros_lib setup
  ```
  cd /home/utokyo/Arduino/libraries
  rosrun rosserial_arduino make_libraries.py .
  ```

### converyor demo
```
roscore
rosrun rosserial_python serial_node.py /dev/ttyACM0 _baud:=115200
```

start conveyor
```
rostopic pub -1 /start_conveyor std_msgs/Bool "data: true" 
```

stop conveyor
```
rostopic pub -1 /stop_conveyor std_msgs/Bool "data: true"
```

topic
  - /is_conveyor_on: on/off status of the conveyor
