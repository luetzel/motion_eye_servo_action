# motion_eye_servo_action
Python scripts to add pan-tilt action buttons to motionEye using an Adafruit PCA9685 servo controller

# Purpose and features

Collection of Python scripts to add pan-tilt action buttons to [motionEye](https://github.com/ccrisan/motioneye/wiki).

A pan-tilt bracket, equipped with two SG90 standard servos is wired to an [Adafruit PCA9685 16-channel servo driver](https://learn.adafruit.com/adafruit-16-channel-servo-driver-with-raspberry-pi)
to control a Raspberry Pi Cam.

![Image](https://github.com/luetzel/motion_eye_servo_action/blob/master/pan-tilt.jpg)

The scripts add action buttons (up/down, lef/right) to the camera overlay, in order to pan/tilt the camera.
Current servo positions are stored as integer values in file vert_pos and horz_pos.

# Wiring

Adafruit Shield -> Raspberry Pi

V+                 +5V
Vcc                +3V
SDA                SDA
SCL                SCL
EO                 BCM_GPIO18
GND                GND

Vertical servo -> Channel 0
Horizontal servo -> Channel 1

Since micro servos tend to make some noise, when idle, they can be powered-off by
pulling the Enable Output (EO) Pin to HIGH.

# Installation

The scripts require the Adafruit PCA9685 Python library, available from:
´´´
git clone https://github.com/adafruit/Adafruit_Python_PCA9685.git
cd Adafruit_Python_PCA9685
sudo python setup.py install
´´´

Files must be copied into the motionEye configuration directory, which is usually located at

´´´
/etc/motioneye
´´´

Pyhton scripts must be made executable with:

´´´
sudo chmod 755 /etc/motioneye/up_1
´´´

In case that you have multiple cameras connected, you may have to rename the files to match your
[camera_id](https://github.com/ccrisan/motioneye/wiki/Action-Buttons)

Please note that you have to adjust servo_min/servo_max value for both, the vertical and horizontal
servo.

# Credits

* [motionEye](https://github.com/ccrisan/motioneye/wiki)
* [Adafruit](https://learn.adafruit.com/adafruit-16-channel-servo-driver-with-raspberry-pi)
* [raspberryblog.de](https://raspberryblog.de)
