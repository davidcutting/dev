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

# Install base development environment packages
RUN apt-get update && apt-get install -y \
    ca-certificates \
    bash-completion \
    build-essential \
    git \
    vim \
    wget \
    sudo