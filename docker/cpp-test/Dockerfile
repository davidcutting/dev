FROM base-dev as nng-dev

WORKDIR /tmp

# Add packages
RUN git clone https://github.com/nanomsg/nng.git && \
    cd nng && \
    mkdir build && \
    cd build && \
    cmake -G Ninja .. && \
    ninja && \
    sudo ninja install

RUN git clone https://github.com/google/flatbuffers.git && \
    cd flatbuffers && \
    cmake -G "Unix Makefiles" -G Ninja -D FLATBUFFERS_CXX_FLAGS="-Wno-error" -DCMAKE_BUILD_TYPE=Release && \
    ninja && \
    sudo ninja install