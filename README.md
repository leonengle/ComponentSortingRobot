###Component Sorting Robot Design Specification
#Project Goal: 
This is the github repository for the Component Sorting Robot (CSR). The goal of this project is to build a robot that automatically sorts resistors, capacitors and inductors and places them in a toolbox. 

#Current Design: there shall be a 3-axis gantry that moves a claw mechanism around to pick up the components and drop them in the corresponding bin. The claw mechanism will have a main pincher that is insulated which shall pick up the components. 

The user shall be responsible for fully extending the component leads and placing it on a conveyor belt. The conveyor belt shall have a sensor that determines when a component has reached the end and will stop at this point. There shall be a set of electronic contacts at the end of the conveyor belt that connect the component to a circuit that will determine the component type and measure its corresponding capacitance, inductance or resistance. The conveyor belt shall detect when a component has been picked up by the claw and move a new component into position. The pick-up position shall be the zero-point of the gantry, so the gantry may recalibrate itself when picking up each new component. 

The component type and value shall be determined with a circuit that places the mystery component in series with a resistor Rtest and detects whether there is a change in voltage across Rtest. If the voltage across Rtest is transient, the mystery component is not a resistor. In this case, a microcontroller shall measure the rate of change of the voltage across Rtest and determine the time constant of the circuit. Knowing the value of Rtest, the microcontroller shall perform the calculations required to find the value of the mystery component. If the voltage across Rtest converges to 0, the mystery component is a capacitor. If the voltage across Rtest converges to the reference voltage, the component is an inductor. There shall be a feedback circuit that keeps the reference voltage at a set value.

The tool box used shall be an off-the-shelf plastic box with dimensions chosen to fit a component with leads fully extended. In a future version there shall be an option to cofigure the CSR for different toolboxes based on their bin dimensions and divider widths.

The desired timing for the whole sorting operation shall be 2 seconds, or the approximate amount of time it would take for a user to straighten a component and place it on the converyor belt. This way the user shall be able to seemlessly place components on the conveyor belt without waiting for the robot to finish sorting each time. 

There shall be an algorithm that determines the optimal path for the claw to take from the pick-up location to the sorted bin the component shall be dropped at. This path shall be optimized for speed and to minimize mechanical oscillations that must be damped. 

There shall be a series of motor driver ICs to offload the computation of driving each stepper motor from the microcontroller to a separate chip. 

There shall be a PCB or breadboard that integrates the motor drivers, microcontroller, and sensor inputs to ensure proper operation.

#Bill of Materials:
- https://www.digikey.com/en/products/detail/sparkfun-electronics/ROB-12779/5318750
- https://www.amazon.com/STEPPERONLINE-Pancake-Stepper-Bipolar-Extruder/dp/B0B93HTR87/ref=sr_1_5?dib=eyJ2IjoiMSJ9.hN-9QQUUabt-Xybqh_2hebgriL6Zzkv_V1gXn0FD0FwS7fR9O_f-G0o3gRZWOE1AL6bmydGmJAWXUmSaQWetZJcuDC3ChmM5a0kWTG5J3W3T6OjF_6miJqOTtp4FTtQHugpGS916vktJZ-N0BwQwsyEVhsoW7UvSuApCrmtSGr2x2XP2IrhQojPBGSFqSljTRcVOWGTRwqQ9Z0UZircDr_3WHQZtApGGG9pKvGEntBM.N5PIQQnK0bKrHVDN0UR9i0Z0-S4Nwk-JPPHxXFGHKBQ&dib_tag=se&hvadid=631491241650&hvdev=c&hvlocphy=9216518&hvnetw=g&hvqmt=e&hvrand=13298237334718594531&hvtargid=kwd-362257952102&hydadcr=7473_13294095&keywords=amazon%2Bstepper%2Bmotor&qid=1734376079&sr=8-5&th=1
