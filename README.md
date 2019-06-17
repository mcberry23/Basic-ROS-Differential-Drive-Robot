# Basic-ROS-Differential-Drive-Robot
This ROS configuration is for a basic differential drive robot. It allows input from a joystick or keyboard. The only sensors are quadrature encoders, one on each motor.  The encoders used are [CUI 103 encoders](https://www.digikey.com/product-detail/en/cui-inc/AMT103-V/102-1308-ND/827016).  They are being read by a Teensy 3.2 microcontroller utilizing the hardware interrupt feature of the encoder library.  The motor controller used is the [Smart Drive Duo-30 80 amp](https://ozrobotics.com/shop/smart-drive-duo-30-drive-power-brushed-dc-motor-with-current-up-to-80a/?gclid=CjwKCAjw0ZfoBRB4EiwASUMdYXAI7zVw-jdKr1idC6ViFQfYpFjaGuqhP0QkwR58nrPpzUs6zKsCcxoCR60QAvD_BwE).  It is being controlled by an Arduino Nano microcontroller.  The two microcontrollers are connected via USB serial to an Intel NUC 8i5.   

## Arduino Setup
Arduino Used: https://www.amazon.com/Longruner-ATmega328P-Controller-Module-Arduino/dp/B01MSYWE6B/ref=sr_1_2_sspa?keywords=arduino+microphone&qid=1559157394&s=gateway&sr=8-2-spell-spons&psc=1
Download IDE: https://www.arduino.cc/en/Main/Software
Board: Arduino Nano
Port: ttyUSBx
Processor: ATmega328P(old bootloader)
Programmer: AVRISP mkll

## Setting it up
There may be some packages that need to be installed not listed here in addition to ROS Melodic, the Arduino IDE, and Teensy loader.
1. Make the ROS source code
```
cd catkin_ws
catkin_make
```
1. Load the firmware on the Arduino and Teensy
1. Make sure Arduino is on /dev/ttyUSB0 and the Teensy is on /dev/ttyACM0.  If not update the launch/teensy.launch and launch/arduino.launch files.
1. If you are using a USB joystick controller, ensure the port is /dev/input/js0 and customize a config file for the specific controller in catkin_ws/teleop_twist_joy/config.
1. If needed you can adjust the PID constants in /catkin_ws/src/differential_drive/launch/diff-drive.launch

## Running the drive programs
Use the desired bash script in the /launches folder.  The drive-odom-* files require the encoders to be wired and configured.
