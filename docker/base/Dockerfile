# Image
FROM ubuntu:jammy as base

ENV DEBIAN_FRONTEND=noninteractive

# Timezone and Locale
RUN apt-get update && apt-get install -y locales tzdata && \
    locale-gen en_US.UTF-8 && \
    update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8 && \
    ln -fs /usr/share/zoneinfo/UTC /etc/localtime && \
    dpkg-reconfigure --frontend noninteractive tzdata && \
    rm -rf /var/lib/apt/lists/*

ENV LANG en_US.UTF-8

######################
from base as base-dev

# Install base packages
RUN apt-get update && apt-get install -y \
    bash-completion \
    build-essential \
    ca-certificates \
    cmake \
    ninja-build \
    pkg-config \
    gdb \
    git \
    vim \
    wget \
    sudo \
    stow

# Set up user
ARG USERNAME=dcutting
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Create a non-root user
RUN groupadd --gid $USER_GID $USERNAME && \
    useradd -s /bin/bash --uid $USER_UID --gid $USER_GID -m $USERNAME && \
    echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME && \
    chmod 0440 /etc/sudoers.d/$USERNAME && \
    rm -rf /var/lib/apt/lists/* && \
    echo "source /usr/share/bash-completion/completions/git" >> /home/$USERNAME/.bashrc

ENV DEBIAN_FRONTEND=