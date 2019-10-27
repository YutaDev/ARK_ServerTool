FROM node:9.7.0-alpine

WORKDIR /app

COPY package.json /app

RUN apk update && \
    npm install && \
    npm install -g npm && \
    npm install -g vue-cli