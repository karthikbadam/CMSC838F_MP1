# CMSC838F_MP1 Ring Controller

Sriram Karthik Badam, Raul Guerra

The idea behind Ring Controller is to use a magnet and a compass to interact over the surface of a table. We decided to test this interaction style by playing Space Invaders/Galaga, a fixed shooter game.

Our prototype of the tangible input device is quite simple. We got a [triple-axis magnetometer](http://www.adafruit.com/product/1746) and hooked it to an [Arduino](https://learn.adafruit.com/adafruit-hmc5883l-breakout-triple-axis-magnetometer-compass-sensor/overview). We started off by placing a magnet in front of the sensor and used the Arduino visualizer from IA2 to observe the readings. These readings represent the magnetic field strength along x, y, z directions, which is dependent on the cube of the distance along the respective axis. Therefore, we used the cube root of these readings and mapped its gradient to movement on the screen. Furthermore, we defined a tap-style gesture to identify when to shoot. Once we had the algorithms in place, we modified the source code of a [space invaders game](http://www.openprocessing.org/sketch/6572) to give it a Galaga-style look and read input from the magnetometer (fixed on a wearable ring) through Arduino.

##Applications:

The goal of this project was to test if the magnetic compass based input mechanism will work for precise 3D motion tracking. This can have wide applications in gaming both 2D and 3D and design processes (for instance, modeling).

Our prototype currently uses one sensor, however, this can be easily scaled to multiple sensors on all fingers (as each sensor readings are independent of others).

##Difficulties:

The major difficulty was with mapping the motion in 3D to the game. Our algorithm used the gradient of the cube root of magnetic strength along the y-axis of the sensor to decide whether to move left or right on the screen (and by how much). However, the result was extremely jumpy. To counter this, we applied the gradient after averaging the values using a window function, thus creating a smoothing effect. We played window sizes to overcome the jumpiness. This does have a side effect as the smoothing now causes a perceivable lag when the user changes direction.

The tap gesture to shoot in the game was identified by performing a double derivative on the readings to find spikes in the magnetic field strength magnitude. We tested different thresholds to see when the tap gesture should be triggered (and reduced false positives).

##Components:

Arduino
Triple-axis Magnetometer HMC5883l
Arm band
Neodymium Magnets
Ring (to place the sensor)


