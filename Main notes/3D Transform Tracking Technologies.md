2026-01-04 10:27

#Extended-Reality  #HCI 

Capture transform of:
- Head => FOV to display and framing.
- Pupils => POV to optimize display.
- Hands, other organs and other objects => transfer action to VE.
- Anything => animation, modeling,...

Accuracy:
- Position tracking: Cellular network 100m; GPS 10m; Wifi 1m.
- Orientation tracking: Gravimeter + magnetometer a few degrees; Accelerometer/gyroscope for acceleration and angular velocity.
# Old
## Magnetic tracker
Uses orthogonal magnetic antennas in a transmitter and receiver to determine the receiver’s position and orientation from the received magnetic field. Bad because can be interfered by another ferromagnetic object.
## Ultrasound (acoustic) tracker
Uses ultrasonic speakers and microphones to compute position, is low-cost, but is sensitive to ambient noise and requires direct line of sight between emitter and receiver.
## GPS
# Vision tracker
## Inside out (in/outdoor)
An optical tracker uses photodiodes (often on the ceiling) and a head-mounted camera to track position, offering high precision but sensitivity to lighting conditions.
## Outside in (indoor)
Marker-based optical tracking uses passive (retro-reflective) or active (IR LED) markers detected by infrared cameras, enabling wireless tracking of many targets but at high cost.
![[Outside-in Tracking.png]]
## Camera tracker
Image-based tracking requires visual patches, known 3D models (patch <=> augmentation is called Proto Tangible Interface), (may be placed on the operator) for detection, [[Image Object Tracking]] and [[Camera Models|calibration]].
# Ubiquitous tracking
Combines many tracking techs.
# Mechanical tracker
Mechanical trackers measure movements via cables and potentiometers attached to the operator, offering good precision at low cost but with bulky hardware.
![[Mechanical Tracking.png]]
Mechanical arm tracking uses optical encoders or variable resistances and geometric equations (homogeneous matrix composition) to compute position, with calibration typically at the probe.
![[Mechanical Arm.png]]
# 3D acquisition
Depth-sensing devices use infrared projectors and cameras with time-of-flight or pattern matching for long to short distances, respectively, enabling hands-free interaction, from low-cost Kinect/PrimeSense to high-end LiDAR scanners.
# 3D mouse (force sensing)
Force sensing can be done using optical force sensors or strain-gauge–based force sensors.
# 3D modeling by laser
Image processing and reconstruction algorithms are generally complex and difficult to implement: Real object > Point cloud > Model.
![[3D Modeling Laser.png]]
# Hand tracking
> Needs to track transform, configuration, force. Needs force sensation (reaction of the object) and haptics (the object surface).

## Power/Cyber glove
Either user conductive ink; or fiber optics; or strain gauges are attached to elastic nylon, typically with 16–24 sensors; Mechanical tracking can use optical encoders, variable resistances, or Hall-effect sensors and geometric equations of the mechanical structure to calculate the angular flexion of each phalanx to recognize gestures.
## Hand tracking
Leap Motion: A 30×30×30 cm volume uses 2 IR cameras and 3 IR LEDs for skeleton matching.