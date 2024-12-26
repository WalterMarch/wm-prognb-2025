FROM ubuntu:22.04

ARG USERNAME=myuser
ARG USER_UID=1000
ARG USER_GID=$USER_UID
ARG USER_SHELL=/bin/bash

RUN apt-get update

# some important utilities
RUN apt-get install -y curl
RUN apt-get install -y git
RUN apt-get install -y tree
RUN apt-get install -y wget

# Create the user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME \
    && usermod -s $USER_SHELL $USERNAME

# Pascal 
RUN apt-get install -y fpc

# switch to user $USERNAME
SHELL ["/bin/bash", "-c"]
USER $USERNAME
