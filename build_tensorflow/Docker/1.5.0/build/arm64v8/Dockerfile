# Docker/deps/arm64v8/Dockerfile
FROM build-tensorflow:deps-arm64v8

WORKDIR /build
COPY ./ ./

# Build Tensorflow on arm
RUN chmod +x build_tensorflow.sh
RUN ./build_tensorflow.sh configs/1.5.0/arm64v8/cpu.conf
