# Tensorflow-on-arm

Inspired by the [tensorflow-on-raspberry-pi](https://github.com/samjabrahams/tensorflow-on-raspberry-pi).
Tool for compile tensorflow for arm.

## Building in Docker
Run the Dockerfiles to build Tensorflow for arm in an isolated environment:
```shell
cd build_tensorflow

# tensorflow 1.5.0 arm32v7 - works
docker build --rm -t build-tensorflow:1.5.0-arm32v7 -f Docker/1.5.0/arm32v7/Dockerfile .

# tensorflow 1.5.0 arm64v8 - works
docker build --rm -t build-tensorflow:1.5.0-arm64v8 -f Docker/1.5.0/arm64v8/Dockerfile .

# tensorflow 1.6.0 arm32v7 - not yet working (https://github.com/jessebenson/tensorflow-on-arm/issues/1)
docker build --rm -t build-tensorflow:1.6.0-arm32v7 -f Docker/1.6.0/arm32v7/Dockerfile .

# tensorflow 1.6.0 arm64v8 - works
docker build --rm -t build-tensorflow:1.6.0-arm64v8 -f Docker/1.6.0/arm64v8/Dockerfile .

# tensorflow 1.7.0 arm32v7 - not yet working (https://github.com/jessebenson/tensorflow-on-arm/issues/1)
docker build --rm -t build-tensorflow:1.7.0-arm32v7 -f Docker/1.7.0/arm32v7/Dockerfile .

# tensorflow 1.7.0 arm64v8 - works
docker build --rm -t build-tensorflow:1.7.0-arm64v8 -f Docker/1.7.0/arm64v8/Dockerfile .
```

## Pre-built Docker Images
Pre-built docker images are published to https://hub.docker.com/r/jessebenson/build-tensorflow for easy consumption.  Usable to retrieve the Tensorflow binaries:

```shell
docker run -dit --name build jessebenson/build-tensorflow:arm32v7
docker cp build:/tensorflow/libtensorflow.so .
docker cp build:/tensorflow/libtensorflow_framework.so .
docker stop build
```

## Dependences
```shell
apt-get install openjdk-8-jdk automake autoconf
apt-get install curl zip unzip libtool swig libpng12-dev zlib1g-dev pkg-config git zip g++ unzip wget xz-utils

# For python2.7
apt-get install python-numpy python-dev python-pip

# For python3
apt-get install python3-numpy python3-dev python3-pip
```

## Cross-compilation
Make you sure added arm architecture, see how to adds in debian flavors:
```shell
dpkg --add-architecture armhf
echo "deb [arch=armhf] http://httpredir.debian.org/debian/ stretch main contrib non-free" >> /etc/apt/source.list
```
if you want compile python support:
```shell
# For python2.7
apt-get install libpython-all-dev:armhf

# For python3
apt-get install libpython3-all-dev:armhf
```

## Edit tweaks like bazel resources, board model, and others
see configuration file examples in: build_tensorflow/configs/

## Finally, compile tensorflow.
```shell
cd build_tensorflow/
chmod +x build_tensorflow.sh
./build_tensorflow.sh <path-of-config>
# If no output errors, the pip package will be in the directory: /tmp/tensorflow_pkg/
```
