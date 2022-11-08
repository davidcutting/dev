# Image
FROM ubuntu:jammy as base-dev
ARG DEBIAN_FRONTEND=noninteractive

# Install base packages
RUN set -ex && apt-get update && apt-get -y --no-install-recommends install \
    autoconf \
    build-essential \
    ca-certificates \
    cmake \
    ninja-build \
    pkg-config \
    git \
    gdb \
    wget \
    # QOL
    sudo \
    bash-completion \
    stow

# Set up user
ARG USERNAME=dcutting
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN set -ex && \
    groupadd --gid $USER_GID $USERNAME && \
    useradd --uid $USER_UID --gid $USER_GID -m $USERNAME && \
    usermod -aG sudo $USERNAME

RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

USER $USERNAME

WORKDIR /home/$USERNAME
RUN git clone https://github.com/davidcutting/dotfiles.git && \
    rm ~/.bashrc && \
    cd dotfiles && \
    make minimal