# Density-Based-Traffic-Management

Overview:

This project simulates a traffic signal system that adjusts signal timings based on real-time traffic density. Four lanes are equipped with infrared (IR) sensors to measure vehicle presence. The system displays "High Density" or "Normal Density" on an LCD screen, corresponding to the sensor input.

Signal Timing Adjustment:

Normal Density: When the IR sensor is unobstructed (indicating low traffic), the green signal duration is set to 7 seconds.

High Density: If the IR sensor is blocked (indicating high traffic), the green signal duration is extended to 15 seconds.

The system manages four sets of traffic lights (green, yellow, red) and allocates appropriate signal times to each lane based on the detected traffic density. This dynamic approach aims to optimize traffic flow and reduce congestion.




Components:

IR Sensors: Each lane has an IR sensor to detect traffic density.

irSensorPin1, irSensorPin2, irSensorPin3, irSensorPin4: Pins where IR sensors are connected.

Traffic Lights: Each lane is controlled by a set of three LEDs representing green, yellow, and red lights.

Lane 1: greenPin1, yellowPin1, redPin1

Lane 2: greenPin2, yellowPin2, redPin2

Lane 3: greenPin3, yellowPin3, redPin3

Lane 4: greenPin4, yellowPin4, redPin4

LCD Display: Used to display real-time information about the current lane's traffic density and countdown for the next signal.

LCD Interface: Controlled by the LiquidCrystal_I2C library.



Logic:

Setup

Initializes the LCD screen with the message "Density Based Traffic Signal".
Defines pins for all traffic lights and IR sensors.
Initially sets the yellow light on for lane 1 to signal the beginning of the system.
Main Loop:

Lane 1 Sequence:

Turns on the green light for lane 1.
Checks the IR sensor (irSensorPin1) to determine traffic density.
If  high density is detected, the green light remains active for 15 seconds, and "L1: High Density" is displayed on the LCD.
If normal density is detected, the green light remains active for 8 seconds, and "L1: Normal Density" is displayed.
After this, lane 1's green light is turned off, and the yellow light is shown, preparing lane 2 to be green.

Lane 2 Sequence:

Similar to lane 1, lane 2 turns green, checks for traffic density using its IR sensor (irSensorPin2), and adjusts the timing accordingly.
Displays "L2: High Density" or "L2: Normal Density" based on sensor data.
After this, it proceeds to lane 3.

Lane 3 and Lane 4 Sequences:

The same logic is applied for lane 3 and lane 4, adjusting the green signal timing based on their respective IR sensor readings (irSensorPin3, irSensorPin4).

Signal Transition:

Before transitioning to the next lane, the system gives a 5-second warning by turning on the yellow lights and displaying "Next Green Light in Lane X in Y seconds" on the LCD screen.

Adjustable Timings:

High Traffic Density: 15 seconds for green light.
Normal Traffic Density: 8 seconds for green light.

Transition Warning: 5 seconds for each lane before switching to green light.



Key Functions:
Traffic Density Detection: The IR sensors detect whether there is a blockage (traffic) in the lane. A LOW signal indicates the lane has traffic.

LCD Display: Shows the current lane, density level, and the countdown for the next red light or green light.
