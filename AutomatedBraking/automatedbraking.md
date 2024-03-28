When a dangerous situation occurs that forces the driver, or the car itself, to perform a
manoeuvre, this can endanger other vehicles. In order to warn other vehicles, the car sends
out a warning message. Nearby cars that are in danger can then react according to the
information provided within the message.
An ECU of the chassis & safety domain detects a danger; this may be the trigger of an airbag,
an obstacle in direction of travel seen by an environmental sensor, or an emergency braking
performed by the driver or an automatic system. The Chassis Safety Controller (CSC) gets
information about the dangerous situation via the Chassis Domain Bus. The CSC will assess
the situation and will take measures to mitigate the danger for the car. The measures will
result in commands to actuator ECUs in the chassis & safety domain and additionally com-
mands to the powertrain domain to get a helpful driving power adjustment. In parallel it
will also send information to the Communication Unit (CU). This information will contain
data about the current vehicle dynamic status and detailed information about the planned
actions (deceleration or acceleration, steering, etc.).
The CU will send out a warning message that contains this information via the DSRC interface to nearby vehicles. The emergency message contains longitude, latitude, altitude,
speed, acceleration and heading of the car, the time of message generation, the expiry time
of the message, an indicator for the reliability of the information, a code that is classifying
the car, an id that is identifying the sender of the message, an event code that is classifying
the emergency situation and the planed acceleration and heading. All this information is
packed in a message frame that adds checksum, information for protocol processing and if
necessary security information.

Functional requirements
- No warning message without a real danger is allowed
- No failure in any single unit may be succeeded by a false message
- No failure of any single communication may be succeeded by a false message
- Any single fault in an ECU has to be detectable
- Information about dangerous events has to be broadcast according to the communica-
tion congestion control algorithms
- Information about the dangers have to be broadcast to other cars with highest priority
- Privacy of the broadcast car information has to be guaranteed
Technical Requirements
- The maximum delay from danger detection to broadcast of the car2X message should
be less than 150 ms
- Additional security information on the busses in the chassis and safety & powertrain
domains should be less than 15% of the net data
Security aspects
- Privacy of the broadcast car information has to be guaranteed

Use between 4 and 10 blocks
