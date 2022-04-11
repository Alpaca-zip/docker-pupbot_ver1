FROM tiryoh/ros-desktop-vnc:melodic
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y ros-melodic-rosserial-arduino \
    ros-melodic-rosserial-python \
    ros-melodic-rosserial-client \
    ros-melodic-rosserial-msgs \
    ros-melodic-rqt* \
    ros-melodic-rviz \
    ros-melodic-ros-control \
    ros-melodic-ros-controllers
RUN mkdir -p /home/ubuntu/catkin_ws/src && \
    /bin/bash -c "source /opt/ros/melodic/setup.bash ; cd /home/ubuntu/catkin_ws/src ; catkin_init_workspace" && \
    /bin/bash -c "source /opt/ros/melodic/setup.bash ; cd /home/ubuntu/catkin_ws && catkin build" && \
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