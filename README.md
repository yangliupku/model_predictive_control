# CarND-Controls-MPC
Self-Driving Car Engineer Nanodegree Program

---
## Model Description
###Kinetic Model:
In this project, the state of vehicle is described by a simple kenetic bicycle model. The state variables are 
 - x: x coordinate 
 - y: y coordinate
 - $\psi$: direction angle of the vehicle 
 - v: linear velocity of the vehicle

The control variables are 
- a: linear accelaration, usually related to throttle
- $ \delta$: steering angle.

Here's the state transfer equation of the vehicle in our model:
![alt text][image1]

### Trajectory planning
We will receive the reference waypoints from the simulator. Our goal is to find the optimal sequence of control signals [$a_1$,$\psi_1$,$a_2$,$\psi_2$ ...$a_n$,$\psi_n$] so that the trajectory of our vehicle is close to the reference waypoints. In short, at each time step, our controller will:
- receive reference trajectory
- find the optimal steer and accelaration to miminize cost 
- actuate steer and accelaration for the **first step**

![alt text][image3]

## Results
Here's the result of running the controller on the simulator. We can see the centrifugal cost forces the car to slow down when making turns. This enables car to drive at peak velocity of 85mph while stay in the center of the lane.
<img src="./report/test.gif" width="720"/>

## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1(mac, linux), 3.81(Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `install-mac.sh` or `install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets
    cd uWebSockets
    git checkout e94b6e1
    ```
    Some function signatures have changed in v0.14.x. See [this PR](https://github.com/udacity/CarND-MPC-Project/pull/3) for more details.

* **Ipopt and CppAD:** Please refer to [this document](https://github.com/udacity/CarND-MPC-Project/blob/master/install_Ipopt_CppAD.md) for installation instructions.
* [Eigen](http://eigen.tuxfamily.org/index.php?title=Main_Page). This is already part of the repo so you shouldn't have to worry about it.
* Simulator. You can download these from the [releases tab](https://github.com/udacity/self-driving-car-sim/releases).
* Not a dependency but read the [DATA.md](./DATA.md) for a description of the data sent back from the simulator.


## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./mpc`.

[//]: # "Image References"
[image1]: ./report/fig1_state_equation.png 
[image2]: ./report/fig2_traj_planning.png
[image3]: ./report/fig3_pipeline.png 