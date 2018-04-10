# FCND-Term1-P2-3D-Motion-Planning

## Overview
This is the project 2 of term 1 in [Flying Car Nanodegree](https://www.udacity.com/course/flying-car-nanodegree--nd787) on Udacity.  
The code communicates with [Udacity FCND Simulator](https://github.com/udacity/FCND-Simulator-Releases/releases) using [Udacidrone](https://udacity.github.io/udacidrone/) API.

## Prerequisites
To run this project, you need to have the following software installed:  
- [Miniconda](https://conda.io/miniconda.html) with Python 3.6.x  
- [Udacity FCND Simulator](https://github.com/udacity/FCND-Simulator-Releases/releases)

## Setup Instructions (abbreviated)
1. Download [miniconda](https://conda.io/miniconda.html) and then install by opening the file/app that you download.  
2. `git clone https://github.com/udacity/FCND-Term1-Starter-Kit.git` to clone the starter kit and then cd FCND-Term1-Starter-Kit into that directory. If you have a windows machine, you must rename meta_windows_patch.yml to meta.yml as well.  
3. `conda env create -f environment.yml` to create the miniconda environment: this took me 20 minutes to run due to the large number of installs required.  
4. `source activate fcnd` to activate the environment (you'll need to do this whenever you want to work in this environment).

## Project Description
TODO: Create description for each files in the repository
- [3D-Motion-Planning.ipynb](./3D-Motion-Planning.ipynb)
- [motion_planning.py](./motion_planning.py)
- [planning_utils.py](./planning_utils.py)
- [README.md](./README.md)

## Run the project
1. Setup the environment by following [Setup Instructions](./README.md#12)  
2. Launch your [Udacity FCND Simulator](https://github.com/udacity/FCND-Simulator-Releases/releases)  
3. In your terminal which has `fcnd` environment activated, pick your goal position and run the corresponding command  

First goal position [800, 785, 0.147]  
```
python motion_planning.py --global_goal_lon -122.39355284 --global_goal_lat 37.79682234 --global_goal_alt -0.147
```
Second goal position [787, 46, 0.147]  
```
python motion_planning.py --global_goal_lon -122.40195876 --global_goal_lat 37.79673913 --global_goal_alt -0.147
```
Third goal position [80, 80, 0.147]  
```
python motion_planning.py --global_goal_lon -122.40161255 --global_goal_lat 37.79037412 --global_goal_alt -0.147
```
Fourth goal position [80, 800, 0.147]  
```
python motion_planning.py --global_goal_lon -122.39343552 --global_goal_lat 37.79033231 --global_goal_alt -0.147
```
4. Your drone should be flying after 20-30 seconds waiting.  
5. Done  

## Project Rubric
### 1. Writeup  
#### 1.1 Provide a Writeup / README that includes all the rubric points and how you addressed each one. You can submit your writeup as markdown or pdf.  
You are reading it!  
### 2. Explain the Starter Code  
#### 2.1 Test that `motion_planning.py` is a modified version of `backyard_flyer_solution.py` for simple path planning. Verify that both scripts work. Then, compare them side by side and describe in words how each of the modifications implemented in `motion_planning.py` is functioning.  
1. States are defined different, using auto()  
2. Add PLANNING state in states  
3. Replace all_waypoints with waypoints in class initial definition  
4. In state_callback(), in Arming state, instead of calling takeoff_transition(), it is calling plan_path()  
5. In state_callback(), in Planning state, calliing takeoff_transition()  
6. Add new function send_waypoints()  
7. Add new function plan_path()  
### 3. Implementing Your Path Planning Algorithm  
#### 3.1 In the starter code, we assume that the home position is where the drone first initializes, but in reality you need to be able to start planning from anywhere. Modify your code to read the global home location from the first line of the `colliders.csv` file and set that position as global home (`self.set_home_position()`)  
Global home location is read at [`motion_planning.py` Line124](./motion_planning.py#L124)  
Function [`read_home()`](./planning_utils.py#L164-L180) added to [`planning_utils.py`](./planning_utils.py)  
#### 3.2 In the starter code, we assume the drone takes off from map center, but you'll need to be able to takeoff from anywhere. Retrieve your current position in geodetic coordinates from `self._latitude`, `self._longitude` and `self._altitude`. Then use the utility function `global_to_local()` to convert to local position (using `self.global_home` as well, which you just set)  
This implementation is handled by [`motion_planning.py` Line130-134](./planning_utils.py#L130-L134)
#### 3.3 In the starter code, the `start` point for planning is hardcoded as map center. Change this to be your current local position.  
This implementation is handled by [`motion_planning.py` Line143-148](./planning_utils.py#L143-L148)  
#### 3.4 In the starter code, the goal position is hardcoded as some location 10 m north and 10 m east of map center. Modify this to be set as some arbitrary position on the grid given any geodetic coordinates (latitude, longitude)  
Three arguments were added to [`motion_planning.py` Line192-194](./planning_utils.py#L192-L194)  
They were being parsed and passing to created `drone` at [`motion_planning.py` Line199-200](./planning_utils.py#L199-L200)  
Class `MotionPlanning` were modified to accept new arguments at [`motion_planning.py` Line26](./planning_utils.py#L26)  
Global goal position was initialized at [`motion_planning.py` Line36](./planning_utils.py#L36)  
It will be used at [`motion_planning.py` Line153](./planning_utils.py#L153)  
#### 3.5 Write your search algorithm. Minimum requirement here is to add diagonal motions to the A* implementation provided, and assign them a cost of sqrt(2). However, you're encouraged to get creative and try other methods from the lessons and beyond!  
#### 3.6 Cull waypoints from the path you determine using search.  
### 4. Executing the flight  
#### 4.1 This is simply a check on whether it all worked. Send the waypoints and the autopilot should fly you from start to goal!  
