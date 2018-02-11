# CarND-Controls-MPC
Self-Driving Car Engineer Nanodegree Program

For the MPC project a kinematic model is used, where the vehicle state includes: [x,y,psi,v,cte,epsi], which corresponds to [vehicle position x, vehicle position y, vehicle orientation, cross track error, vehicle orientation error].

For the actuators I consider the steering wheel `delta` and acceleration `a`.

Kinamatic Equations:

x[t+1] = x[t] + v[t] * cos(psi[t]) * dt
y[t+1] = y[t] + v[t] * sin(psi[t]) * dt
psi[t+1] = psi[t] + v[t] / Lf * delta[t] * dt
v[t+1] = v[t] + a[t] * dt
cte[t+1] = f(x[t]) - y[t] + v[t] * sin(epsi[t]) * dt
epsi[t+1] = psi[t] - psides[t] + v[t] * delta[t] / Lf * dt 

### Timestep Length and Elapsed Duration (N & dt)

`N` is the number of timesteps in the horizon. `dt` is how much time elapses between actuations. This values were found in a trial and error method. In theory, T should be as large as possible, while dt should be as small as possible.

### Polynomial Fitting and MPC Preprocessing

A third polynomial is used to fit reference waypoints. To calculate the CTE the waypoints were transformed in the car reference system.


### Model Predictive Control with Latency
The 100ms latency represents the delay between the time the command to activate the actuator is sent and the time the actuator is actually executed. To deal with the delay I first predict its state after 100 ms, and then feed this new state into the solver.


# Model-Predictive-Control
