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

# C# (csharp/dotnet)
RUN apt-get install -y dotnet-sdk-8.0

# Java 21
RUN apt-get install -y openjdk-21-jdk

# JavaScript (Node.js via nvm; React)
EXPOSE 3000
SHELL ["/bin/bash", "-c"]
USER $USERNAME
RUN wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
COPY confignvm.sh .
RUN source ./confignvm.sh
USER root

# SDKMAN! for Kotlin
RUN wget -O sdk.install.sh "https://get.sdkman.io"
RUN chmod +x sdk.install.sh

# switch to user $USERNAME
SHELL ["/bin/bash", "-c"]
USER $USERNAME

# Kotlin as user
RUN /sdk.install.sh
RUN source ~/.sdkman/bin/sdkman-init.sh && sdk install kotlin

# configure git
COPY configit.sh .
RUN source ./configit.sh
