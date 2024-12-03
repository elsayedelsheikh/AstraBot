FROM althack/ros2:humble-dev 

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update \
   && apt-get -y install --no-install-recommends \
      tmux       \
      neovim      \
      libi2c-dev   \
      libserial-dev \
      python3-pip    \
      ros-${ROS_DISTRO}-xacro \
      ros-${ROS_DISTRO}-rmw-cyclonedds-cpp \
      ros-${ROS_DISTRO}-foxglove-bridge \
      ros-${ROS_DISTRO}-teleop-twist-keyboard  \
      ros-${ROS_DISTRO}-controller-manager \
      ros-${ROS_DISTRO}-hardware-interface \
      ros-${ROS_DISTRO}-diff-drive-controller \
      ros-${ROS_DISTRO}-joint-state-broadcaster \
      ros-${ROS_DISTRO}-ros2controlcli \
      ros-${ROS_DISTRO}-robot-localization \
      ros-${ROS_DISTRO}-navigation2 \
      ros-${ROS_DISTRO}-nav2-bringup \
      ros-${ROS_DISTRO}-example-interfaces \
   # Clean up
   && apt-get autoremove -y \
   && apt-get clean -y \
   && rm -rf /var/lib/apt/lists/*
RUN python3 -m pip install smbus pyserial
ENV DEBIAN_FRONTEND=dialog

# Add User to Dialout Group for accessing Serial
ARG USERNAME=ros
RUN usermod -aG dialout ${USERNAME}
RUN groupadd -r i2c && usermod -aG i2c ${USERNAME}

# Set up auto-source of workspace for ros user
ARG WORKSPACE
RUN echo "if [ -f ${WORKSPACE}/install/setup.bash ]; then source ${WORKSPACE}/install/setup.bash; fi" >> /home/ros/.bashrc