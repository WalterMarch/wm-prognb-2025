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
RUN apt-get install -y unzip
RUN apt-get install -y wget
RUN apt-get install -y zip

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

# C# (csharp/dotnet)
RUN apt-get install -y dotnet-sdk-8.0

# Java 21
RUN apt-get install -y openjdk-21-jdk

# JavaScript and TypeScript (Node.js via nvm)
SHELL ["/bin/bash", "-c"]
USER $USERNAME
RUN wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
COPY confignvm.sh .
RUN source ./confignvm.sh
USER root

# SDKMAN! for Kotlin and Scala
RUN wget -O sdk.install.sh "https://get.sdkman.io"
RUN chmod +x sdk.install.sh

# Pascal
RUN apt-get install -y fpc

# Perl
RUN apt-get install -y perl

# Python
RUN ln -fs /usr/bin/python3 /usr/bin/python
RUN apt-get install -y python3-pip
RUN pip install black

# Ruby
RUN  apt-get install -y ruby-full

# switch to user $USERNAME
SHELL ["/bin/bash", "-c"]
USER $USERNAME

# Kotlin and Scala as user
RUN /sdk.install.sh
RUN source ~/.sdkman/bin/sdkman-init.sh && sdk install kotlin && sdk install scala

# configure git
COPY configit.sh .
RUN source ./configit.sh
