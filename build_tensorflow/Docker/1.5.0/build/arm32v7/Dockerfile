# Docker/deps/arm32v7/Dockerfile
FROM build-tensorflow:deps-arm32v7

WORKDIR /build
COPY ./ ./

# Build Tensorflow on arm
RUN chmod +x build_tensorflow.sh
RUN ./build_tensorflow.sh configs/cpu-arm32v7.conf v1.5.0
