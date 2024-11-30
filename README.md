# AstraBot 
Hardware:
- SBC: Jetson Nano B01
- MiC: Arduino Uno
- 2x Motors with wheel encoders
- IMU BNO055 
- Lidar Okdo LD06
- RPi V2 Camera 8MP
- 2DOF Pan/Tilt Camera Platform

## LIDAR LD06
### Wiring:
- LIDAR <=> SBC
- DATA (TX) <=> UART(RX) Pin 10
- P5V <=> 5V
- GND <=> GND
### Run
```bash
chmod 777 /dev/ttyTHS1
ros2 launch ldlidar_ros2 ld06.launch.py
```