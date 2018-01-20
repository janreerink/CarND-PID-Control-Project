# CarND-Controls-PID
This project implements a PID controller for the Udacity self-driving car nano-degree. See the readme for details on setup.



## Discussion of PID value tuning
The controller receives the cross-track error as input and attempts to correct by modifying the steering angle.
Three parameters determine the behavior of the controller. The first term is proportional to the error and multiplied with a 
parameter to correct steering angle. The D term compares present and previous values of the error and uses the difference, 
multiplied with a parameter, to modify the steering angle correction accordingly, which prevents oversteering/osciallations.
The I term is, in this case, the sum of previous errors, again multiplied wiht a parameter. It is useful for correcting systematic
bias.

For this implementation the values were manually tuned, initially only for control of steering angles.
The I-term was set to 0 (no reason to assume a bias), P and D were set to very small values and then modified.
Some testing showed that a trade-off between sensitvity to errors and prevention of oscillations was required: 
higher values for the P-parameter improved the controller's ability to react to curves but also increased oscillations. The D-term was useful for reducing oscillations.

To increase speed a second controller for throttle was added. Here the proportional correction of speed in situation with high error (curves) was important. The higher speed also required some tweaking of the steering-controller parameters.

The final input parameters were (-0.12, 0, -3.9) and (-0.3, 0, -0.1) for the two controllers. 

[Example video](pid_lap.mp4)
