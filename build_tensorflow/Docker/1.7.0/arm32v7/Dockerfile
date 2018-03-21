FROM ubuntu:16.04 AS build

RUN apt-get update

# Install dependencies
RUN apt-get install -y openjdk-8-jdk automake autoconf
RUN apt-get install -y curl zip unzip libtool swig libpng12-dev zlib1g-dev pkg-config git g++ wget xz-utils
RUN apt-get install -y python-numpy python-dev python-pip
RUN apt-get install -y python3-numpy python3-dev python3-pip

# Add armhf (arm32v7) architecture
RUN dpkg --add-architecture armhf
RUN echo "deb [arch=armhf] http://httpredir.debian.org/debian/ stretch main contrib non-free" >> /etc/apt/source.list

WORKDIR /build
COPY ./ ./

# Build Tensorflow on arm
RUN chmod +x build_tensorflow.sh
RUN ./build_tensorflow.sh configs/1.7.0/arm32v7/cpu.conf

# Publish a minimal docker image with just the Tensorflow build outputs (libtensorflow.so and libtensorflow_framework.so)
FROM alpine
COPY --from=build /tmp/tensorflow_lib/* /tensorflow/
