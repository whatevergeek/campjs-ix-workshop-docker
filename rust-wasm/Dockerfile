FROM ubuntu:16.04

ENV DEBIAN_FRONTEND noninteractive

ENV PATH=/root/.cargo/bin:$PATH

#Install rust
RUN apt-get update && apt-get upgrade -qy && \
    apt-get install -y --no-install-recommends \
    curl git openssl libssl-dev ca-certificates \
    build-essential python && \
    apt-get clean && rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/* && \

    curl https://sh.rustup.rs -sSf | sh -s -- --default-toolchain nightly -y && \
    rustup update && \
    rustup default nightly

# Install wasm32
RUN rustup update && \
    rustup install nightly && \
    rustup target add wasm32-unknown-unknown --toolchain nightly

# Install nvm with node and npm
ENV NVM_DIR $HOME/.nvm
ENV NODE_VERSION 8.11.1
RUN curl https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | /bin/bash \
     && /bin/bash -c "source $NVM_DIR/nvm.sh && nvm install $NODE_VERSION && nvm use --delete-prefix $NODE_VERSION"

CMD ["/bin/bash", "--login"]