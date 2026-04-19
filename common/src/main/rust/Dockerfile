FROM messense/cargo-zigbuild:latest

# Rust
ENV RUST_VERSION=nightly-2026-01-29

RUN rustup default $RUST_VERSION
RUN rustup target add x86_64-pc-windows-gnu
RUN rustup target add aarch64-apple-darwin
RUN rustup target add x86_64-unknown-linux-gnu
RUN rustup target add aarch64-unknown-linux-gnu
RUN rustup target add aarch64-linux-android

RUN apt-get update && apt-get install -y wget unzip \
 && wget https://dl.google.com/android/repository/android-ndk-r26d-linux.zip \
 && unzip android-ndk-r26d-linux.zip \
 && mv android-ndk-r26d /opt/android-ndk \
 && rm android-ndk-r26d-linux.zip
ENV ANDROID_NDK_HOME=/opt/android-ndk
ENV PATH=$ANDROID_NDK_HOME/toolchains/llvm/prebuilt/linux-x86_64/bin:$PATH
ENV CC_aarch64_linux_android=aarch64-linux-android21-clang
ENV CXX_aarch64_linux_android=aarch64-linux-android21-clang++

WORKDIR /
