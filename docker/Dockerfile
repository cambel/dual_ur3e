ARG from=ros:melodic-ros-base-bionic

FROM nvidia/opengl:1.0-glvnd-runtime-ubuntu18.04 as nvidia
FROM ${from}

# FROM ros:melodic-ros-base-bionic

LABEL maintainer Cristian Beltran "beltran@hlab.sys.es.osaka-u.ac.jp"

COPY --from=nvidia /usr/local /usr/local
# COPY --from=nvidia /etc/ld.so.conf.d/glvnd.conf /etc/ld.so.conf.d/glvnd.conf
ENV NVIDIA_VISIBLE_DEVICES=all NVIDIA_DRIVER_CAPABILITIES=all

## ROS packages
RUN apt-get update && apt-get install --no-install-recommends -y \
    ros-melodic-gazebo-ros-pkgs \
    ros-melodic-spacenav-node \
    ros-melodic-rqt-common-plugins \
    ros-melodic-catkin \
    ros-melodic-rqt-joint-trajectory-controller \
    ros-melodic-rqt-tf-tree \
    ros-melodic-rqt-multiplot \
    ros-melodic-moveit \
    ros-melodic-moveit-runtime \
    ros-melodic-moveit-python \
    ros-melodic-moveit-resources \
    && rm -rf /var/lib/apt/lists/*

RUN apt-get update && apt-get install --no-install-recommends -y \
    git python-pip \
    python-catkin-tools \
    python-setuptools \
    software-properties-common \
    python-dev
    && rm -rf /var/lib/apt/lists/*

### Ros Workspace ###
RUN pip install catkin-pkg rospkg PySide2 enum34

# Set up the workspace
RUN /bin/bash -c "source /opt/ros/melodic/setup.bash \
               && mkdir -p ~/ros_ws/src \
               && cd ~/ros_ws/ \
               && catkin init"

RUN /bin/bash -c "source /opt/ros/melodic/setup.bash \
               && cd ~/ros_ws/src/ \
               && git clone https://github.com/cambel/dual_ur3e \
               && git clone https://github.com/UniversalRobots/Universal_Robots_ROS_Driver.git ur_driver \
               && git clone -b calibration_devel https://github.com/fmauch/universal_robot.git universal_robot \
               && cd .. && apt-get update && rosdep install -iyr --from-paths src \
               && rm -rf build \
               && catkin build \
               && rm -rf /var/lib/apt/lists/*"

RUN apt update && apt install -y \
    wget mesa-utils\
    && rm -rf /var/lib/apt/lists/*

RUN apt-get install -y build-essential libgl1-mesa-dev qt512-meta-minimal qt512webengine qt512svg

RUN echo 'source /opt/ros/melodic/setup.bash' >> ~/.bashrc
RUN echo 'source /root/ros_ws/devel/setup.bash' >> ~/.bashrc
