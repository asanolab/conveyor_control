# converyor_control
## Setup for ufactory conveyor
### Online manual (ufactory conveyor)
- https://github.com/uArm-Developer/ConveyorBelt-Examples/blob/master/doc/ConveyorBelt%20Getting%20Started%20en%20V1.0.pdf
- https://github.com/uArm-Developer/Controller/blob/master/doc/uArmController%20User%20Manual(Geek%20Edition)20181228V1.0.1.pdf

### Setup
- Arduino setup
  1. Install arduino ide
  2. Install libraries
    - u8glib
      - Tools -> Manage Libraries -> search and install u8glib
    - ros_lib
      ```
      cd /home/utokyo/Arduino/libraries
      rosrun rosserial_arduino make_libraries.py .
      ```

  3. Write sketchbook below to controller
    - sketckbook
      - https://github.com/asanolab/Controller/blob/devel/scene_demo/conveyor_belt/src/conveyor_belt/conveyor_belt.ino
    - add permission
    ```
    sudo chmod 666 /dev/ttyACM0
    ```
    - Choose Boad "Arduino Mega" and port (usually /dev/ttyACM0)
    - Click "Upload"
      
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
