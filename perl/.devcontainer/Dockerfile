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

ARG ZONE_INFO=America/New_York
ENV LANG=en_US.UTF-8

# timezone info
RUN ln -fs /usr/share/zoneinfo/$ZONE_INFO /etc/localtime
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y tzdata
RUN dpkg-reconfigure --frontend noninteractive tzdata

# locale info
RUN apt-get install -y locales && \
    sed -i -e "s/# $LANG.*/$LANG UTF-8/" /etc/locale.gen && \
    dpkg-reconfigure --frontend=noninteractive locales && \
    update-locale LANG=$LANG

# Perl
RUN apt-get install -y perl

# switch to user $USERNAME
SHELL ["/bin/bash", "-c"]
USER $USERNAME
