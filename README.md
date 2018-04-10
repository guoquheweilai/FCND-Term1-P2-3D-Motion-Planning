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
TODO: how to run the project step by step  
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
TODO: Answer the rubric questions by specifying the line number in the code  
Code can be found at [line 162](./motion_planning.py#L162)
