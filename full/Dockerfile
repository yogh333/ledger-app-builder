FROM starknet-alpine-builder-lite:latest

# Define rustup/cargo home directories
ENV RUSTUP_HOME=/opt/rustup \
    CARGO_HOME=/opt/.cargo

RUN apk add rustup curl

RUN rustup-init --default-toolchain nightly -y

# Adding cargo binaries to PATH
ENV PATH=${CARGO_HOME}/bin:${PATH}

# Adding ARMV6M target to the default toolchain
#RUN rustup target add thumbv6m-none-eabi

# Adding Rust standard library source code component
RUN rustup component add rust-src

# Install cargo-ledger
RUN cargo install --git https://github.com/LedgerHQ/cargo-ledger

# Target files for Nano S, S+, X
RUN cargo ledger setup