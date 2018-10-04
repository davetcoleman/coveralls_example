# example_ros_pkg - 2018 - 1st Oct, 2018

Dummy Commit - 07

Description: Example for Subhas

Features:

 - TODO(dave@picknik.ai):

Developed by Dave Coleman at [PickNik Consulting](http://picknik.ai/)

[![Build Status](https://travis-ci.org/bailaC/coveralls_example.svg?branch=master)](https://travis-ci.org/bailaC/coveralls_example)

[![Coverage Status](https://coveralls.io/repos/github/bailaC/coveralls_example/badge.svg?branch=master)](https://coveralls.io/github/bailaC/coveralls_example?branch=master)

[![codecov](https://codecov.io/gh/bailaC/coveralls_example/branch/master/graph/badge.svg)](https://codecov.io/gh/bailaC/coveralls_example)


## Install

### Ubuntu Debian

> Note: this package has not been released yet

    sudo apt-get install ros-kinetic-example_ros_pkg

### Build from Source

1. [Install ROS Kinetic](http://wiki.ros.org/kinetic/Installation/Ubuntu) and the following build tools.
```
sudo apt-get install python-wstool python-catkin-tools clang-format-3.8
```

2. Re-use or create a catkin workspace:
```
mkdir -p ~/ws_catkin/src
cd ~/ws_catkin/src
```

3. Download the required repositories and install any dependencies:
```
git clone git@github.com:PickNikRobotics/example_ros_pkg.git
wstool init .
wstool merge example_ros_pkg/example_ros_pkg.rosinstall
wstool update
rosdep install --from-paths . --ignore-src --rosdistro kinetic
```

4. Configure and build the workspace:
```
cd ..
catkin config --extend /opt/ros/kinetic --cmake-args -DCMAKE_BUILD_TYPE=Release
catkin build
```

5. Source the workspace.
```
source . ./devel/setup.bash
```

### Run launch file

Run simple_class_main
```
roslaunch example_ros_pkg simple_class_main.launch
```
Run simple_class_main with GDB
```
roslaunch example_ros_pkg simple_class_main.launch debug:=true
```
Run simple_class_main with Callgrind
```
roslaunch example_ros_pkg simple_class_main.launch callgrind:=true
```
Run simple_class_main with Valgrind
```
roslaunch example_ros_pkg simple_class_main.launch callgrind:=true
```

## Run Docker Locally

### Prerequisite

You must have a private rsa key `~/.ssh/id_rsa` that is not password protected and is attached to your github and bitbucket accounts. You must also have a working instillation of `docker`.

### Build and Run

1. Navigate to `~/ws_catkin/src/example_ros_pkg`. You should see the `Dockerfile` recipe in the directory.

2. Build the docker image
```
cp ~/.ssh/id_rsa id_rsa && docker build -t example_ros_pkg:kinetic-source .; rm id_rsa
```

3. Run the docker image

Without the gui
```
docker run -it --rm example_ros_pkg:kinetic-source /bin/bash
```

With the gui (tested with Ubuntu native and a Ubuntu VM)
```
. ./gui-docker -it --rm example_ros_pkg:kinetic-source /bin/bash
```

## Usage

TODO(dave@picknik.ai):

## Code API

> Note: this package has not been released yet

See [the Doxygen documentation](http://docs.ros.org/kinetic/api/example_ros_pkg/html/anotated.html)

## Testing and Linting

To run [roslint](http://wiki.ros.org/roslint), use the following command with [catkin-tools](https://catkin-tools.readthedocs.org/).

    catkin build --no-status --no-deps --this --make-args roslint

To run [catkin lint](https://pypi.python.org/pypi/catkin_lint), use the following command with [catkin-tools](https://catkin-tools.readthedocs.org/).

    catkin lint -W2 --rosdistro kinetic

Use the following command with [catkin-tools](https://catkin-tools.readthedocs.org/) to run tests.

    catkin run_tests --no-deps --this -i
