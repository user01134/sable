# Build container versions pinned on 04-18-26
FROM messense/cargo-zigbuild@sha256:4c18634a3d9c7775683b0f1e313584770d32216623a1273a104b634fa294bf4c

ARG RUST_VERSION
RUN rustup default ${RUST_VERSION}
RUN rustup target add aarch64-linux-android

RUN apt-get update && apt-get install -y wget unzip \
 && wget https://dl.google.com/android/repository/android-ndk-r26d-linux.zip \
 && unzip android-ndk-r26d-linux.zip \
 && mv android-ndk-r26d /opt/android-ndk \
 && rm android-ndk-r26d-linux.zip
ENV ANDROID_NDK_HOME=/opt/android-ndk
ENV PATH=$ANDROID_NDK_HOME/toolchains/llvm/prebuilt/linux-x86_64/bin:$PATH


WORKDIR /
