FROM ubuntu:16.04

ENV DEBIAN_FRONTEND noninteractive

ENV PATH=/root/.cargo/bin:$PATH

RUN apt-get update && apt-get upgrade -qy && \
    apt-get install -y --no-install-recommends \
    curl git openssl libssl-dev ca-certificates \
    build-essential python && \
    apt-get clean && rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/* && \

    curl https://sh.rustup.rs -sSf | sh -s -- --default-toolchain nightly -y && \
    rustup update && \
    rustup default nightly

RUN rustup update && \
    rustup install nightly && \
    rustup target add wasm32-unknown-unknown --toolchain nightly

CMD ["/bin/bash", "--login"]