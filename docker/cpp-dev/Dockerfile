FROM ghcr.io/davidcutting/base-dev:master as cpp-dev

# Install base cpp development packages
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install \
    build-essential \
    clang-14 \
    clangd-14 \
    clang-format-14 \
    clang-tidy-14 \
    clang-tools-14 \
    lld \
    lldb \
    llvm \
    gdb \
    gcovr \
    libgtest-dev \
    cppcheck \
    valgrind \
    ninja-build \
    cmake \
    meson \
    pkg-config \
    && apt-get autoremove -y && apt-get clean -y && rm -rf /var/lib/apt/lists/*

RUN update-alternatives --install /usr/bin/clangd clangd /usr/bin/clangd-14 100
