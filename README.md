Goal: This is the github repository for the Component Sorting Robot (CSR). The goal of this project is to build a robot that automatically sorts resistors, capacitors and inductors and places them in a toolbox. 

Current Design: there shall be a 3-axis gantry that moves a claw mechanism around to pick up the components and drop them in the corresponding bin. The claw mechanism will have a main pincher that is insulated which shall pick up the components. On either side of the main pincher there shall be two smaller pinchers that close around the leads of the component once it has been secured by the main pincher. The smaller pinchers shall provide electronic contacts that connect the component to a circuit that will determine the component type and measure its corresponding capacitance, inductance or resistance. 

The user shall be responsible for fully extending the component leads and placing it on a conveyor belt. The conveyor belt shall have a sensor that determines when a component has reached the end and will stop at this point. The conveyor belt shall detect when a component has been picked up by the claw and move a new component into position. The pick-up position shall be the zero-point of the gantry, so the gantry may recalibrate itself when picking up each new component. 

The component type and value shall be determined with a circuit that places the mystery component in series with a resistor Rtest and detects whether there is a change in voltage across Rtest. If the voltage across Rtest is transient, the mystery component is not a resistor. In this case, a microcontroller shall measure the rate of change of the voltage across Rtest and determine the time constant of the circuit. Knowing the value of Rtest, the microcontroller shall perform the calculations required to find the value of the mystery component. If the voltage across Rtest converges to 0, the mystery component is a capacitor. If the voltage across Rtest converges to the reference voltage, the component is an inductor. There shall be a feedback circuit that keeps the reference voltage at a set value.

The tool box used shall be an off-the-shelf plastic box with dimensions chosen to fit a component with leads fully extended. In a future version there shall be an option to cofigure the CSR for different toolboxes based on their bin dimensions and divider widths.

The desired timing for the whole sorting operation shall be 2 seconds, or the approximate amount of time it would take for a user to straighten a component and place it on the converyor belt. This way the user shall be able to seemlessly place components on the conveyor belt without waiting for the robot to finish sorting each time. 

There shall be an algorithm that determines the optimal path for the claw to take from the pick-up location to the sorted bin the component shall be dropped at. This path shall be optimized for speed and to minimize mechanical oscillations that must be damped. 

There shall be a series of motor driver ICs to offload the computation of driving each stepper motor from the microcontroller to a separate chip. 

There shall be a PCB or breadboard that integrates the motor drivers, microcontroller, and sensor inputs to ensure proper operation.
