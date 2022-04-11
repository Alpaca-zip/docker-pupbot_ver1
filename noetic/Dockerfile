FROM tiryoh/ros-desktop-vnc:noetic
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y ros-noetic-rosserial-arduino \
    ros-noetic-rosserial-python \
    ros-noetic-rosserial-client \
    ros-noetic-rosserial-msgs \
    ros-noetic-rqt* \
    ros-noetic-rviz \
    ros-noetic-ros-control \
    ros-noetic-ros-controllers
RUN mkdir -p /home/ubuntu/catkin_ws/src && \
    /bin/bash -c "source /opt/ros/noetic/setup.bash ; cd /home/ubuntu/catkin_ws/src ; catkin_init_workspace" && \
    /bin/bash -c "source /opt/ros/noetic/setup.bash ; cd /home/ubuntu/catkin_ws && catkin build" && \
    echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
RUN cd /home/ubuntu/catkin_ws/src && \
    git clone https://github.com/ROBOTIS-GIT/dynamixel-workbench.git && \
    git clone https://github.com/ROBOTIS-GIT/dynamixel-workbench-msgs.git && \
    git clone https://github.com/ROBOTIS-GIT/DynamixelSDK.git && \
    cd /home/ubuntu/catkin_ws && \
    catkin build && \
    cd /home/ubuntu/catkin_ws/src && \
    git clone https://github.com/Alpaca-zip/pupbot_ver1.git && \
    cd /home/ubuntu/catkin_ws && \
    catkin build