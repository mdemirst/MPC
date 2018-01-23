# Model Proedictive Control
In this project, I developed Model Predictive Control to control vehicle within given trajectory.

# The model

The model I used is actually same as given in the quizes. I have 2d position, orientation, speed, cross track error, orientation error as my state variables. As an actuators we use steering and throttle. For update equations, I used same equations as given in the quizes.

# Timestep
I used horizon of 1 second divided by 10 equal timesteps. Therefore my dt is 0.1. I believe horizon of 1 second is optimal. If I increase it, I would end up doing too much calculation without any gain because at each update we need to do all the calculations again and only use the first prediction. On the other hand, if I decrease it, I may not cover required model constraints well enough.

# Polynomial Fitting and MPC Preprocessing
Before fitting a polynom, I had to convert all the waypoints into local vehicle plane. For this, I used Eigen Transformation library. I chose vehicle position and orientation as a local coordinate origin and feed relative trajectory to MPC solver. Other than that, I didn't do any preprocessing. 

# Model Predictive Control with Latency
In order to take latency into account, I used future predicted vehicle state as current state and fed it into MPC.

# Demo
[Here is the video of my MPC running on demo track](https://youtu.be/L0XZNJsVSGY)
