#ARG BUILD_FROM="alpine:latest"
ARG BUILD_FROM
#FROM $BUILD_FROM
FROM ghcr.io/home-assistant/armv7-base-python:3.9-alpine3.13

ENV LANG C.UTF-8

# Copy data for add-on
COPY run.sh /
COPY js /js

WORKDIR /share

# Install requirements for add-on
RUN apk add --no-cache jq npm make gcc g++ python3 linux-headers udev && \
    npm init -f && \
    npm install mqtt && \
    npm install serialport --build-from-source=serialport

RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
