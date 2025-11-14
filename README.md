# MobileRobot-Openloopcontrol
## Aim:

To develop a python control code to move the mobilerobot along the predefined path.

## Equipments Required:
1. RoboMaster EP core
2. Python 3.7

Here is a **simple algorithm** in the exact format you asked:

---

## **Procedure**

**Step 1:** Initialize the robot and connect using AP mode. <br/>

**Step 2:** Get the chassis, LED, and camera modules from the robot. <br/>

**Step 3:** Start the video stream in 360P resolution. <br/>

**Step 4:** Execute each movement in the sequence and turn on the LED after every move. <br/>

**Step 5:** Stop the video stream and close the robot connection. <br/>

---


## Program
```python
from robomaster import robot
from robomaster import camera
import time

if __name__ == '__main__':
    # Initialize robot connection
    ep_robot = robot.Robot()
    ep_robot.initialize(conn_type="ap")

    # Get robot modules
    ep_chassis = ep_robot.chassis
    ep_led = ep_robot.led
    ep_camera = ep_robot.camera

    print("Video streaming started...")
    ep_camera.start_video_stream(display=True, resolution=camera.STREAM_360P)

    # Movement and LED sequence
    sequence = [
        (2.3, 0, 0),
        (0.5, 0, 45),
        (0.5, 0, 30),
        (0.4, 0, 30),
        (0.4, 0, 45),
        (0.4, 0, 45),
        (0.7, 0, -35),
        (0.3, 0, 0),
        (0.6, 0, -45),
        (0.6, 0, 0),
        (0.3, 0, 45),
        (0.9, 0, 0),
        (0, 0, 55),
        (0.2, 0, -35),
        (0.4, 0, 45),
        (0.3, 0, 45),
        (0.8, 0, 0),
        (0.3, 0, 35),
        (0.1, 0, -45),
        (0.1, 0, 40),
        (0.2, 0, -30),
        (0.3, 0, 45),
        (0.4, 0, -25),
        (0, 0, 40),
        (0, 0, 5),
        (0.4, 0, 10),
        (0, 0, 0)
    ]

    for (x, y, z) in sequence:
        ep_chassis.move(x=x, y=y, z=z, xy_speed=1).wait_for_completed()
        ep_led.set_led(comp="all", r=255, g=100, b=0, effect="on")

    # Stop camera and close connection
    time.sleep(4)
    ep_camera.stop_video_stream()
    print("Stopped video streaming...")

    ep_robot.close()
```

## MobileRobot Movement Image:

![robo](./img/robomaster.png)




## MobileRobot Movement Video:

https://youtu.be/9OXFohHN7OM?si=2RgLiG3SXginb7Tc


## Result:
Thus the python program code is developed to move the mobilerobot in the predefined path.


```
Mobile Robotics Laboratory
Department of Artificial Intelligence and Data Science/ Machine Learning
Saveetha Engineering College
```
