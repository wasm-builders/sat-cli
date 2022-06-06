FROM gitpod/workspace-full

USER gitpod

# subo 0.5.2
RUN brew tap suborbital/subo && \
    brew install subo

# ------------------------------------
# Install Sat (Suborbital)
# ------------------------------------
# "sat_version":"v0.1.4"
RUN git clone --depth=1 https://github.com/suborbital/sat.git && \
    cd sat && \
    go build -o .bin/sat -tags netgo,wasmtime . && \
    sudo cp .bin/sat /usr/local/bin/sat && \
    cd .. && \
    rm -rf sat

