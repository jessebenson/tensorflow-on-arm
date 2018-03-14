# Minimal docker image with just the Tensorflow build outputs from arm32v7/Dockerfile-build
FROM build-tensorflow:1.5.0-build-arm32v7 AS build
FROM alpine
COPY --from=build /tmp/tensorflow_lib/* /tensorflow/