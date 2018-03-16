# Docker/deps/arm64v8/Dockerfile
FROM build-tensorflow:deps-arm64v8

WORKDIR /build
COPY ./ ./

# Build Tensorflow on arm
RUN chmod +x build_tensorflow.sh
RUN ./build_tensorflow.sh configs/cpu-arm64v8.conf v1.7.0-rc0
