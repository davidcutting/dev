from base-dev as cpp-dev

# Install base cpp development packages
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install \
    build-essential \
    cmake \
    meson \
    ninja-build \
    pkg-config \
    cppcheck \
    valgrind \
    clang \
    lldb \
    llvm \
    gdb \
    && apt-get autoremove -y && apt-get clean -y && rm -rf /var/lib/apt/lists/*
