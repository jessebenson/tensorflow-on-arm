# Minimal docker image with just the Tensorflow build outputs from Docker/1.6.0/build/arm64v8/Dockerfile
FROM build-tensorflow:1.6.0-build-arm64v8 AS build
FROM alpine
COPY --from=build /tmp/tensorflow_lib/* /tensorflow/