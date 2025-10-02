# guava-monster
An investigation on how (if) neural nets can enhance the computational efficiency of model predictive control, applied to the thrust vector-controlled rocket landing problem.

## Background
Model predictive control often relies on a simplified dynamics model instead of high fidelity models. This is because high fidelity models (like those which use CFD) are too slow to simulate with online control. Model predictive control also attempts to minimize a cost function over a control sequence. This can take multiple iterations depending on how optimal the initial guess for the control sequence is. The less optimal the control sequence, the more iterations and the slower the computation. 

## Goals
### 1. Dynamics Model Network
Replace the simplified dynamics model of the model predictive controller with a neural network that has been trained on a high fidelity dynamics model. This network will probably be trained on data generated from ANSYS. Network architecture will most likely be a standard feedforward network.

### 2. Warm Starter Network
Have a neural network that is able to provide a good initial guess for what the control sequence should be. Network architecture is yet to be decided. By running this initial guess through the QP solver for the MPC, we also ensure that our control actions can be constrained e.g. our thrust is below a certain value, our gimbal angles do not exceed a certain angle, etc. 
