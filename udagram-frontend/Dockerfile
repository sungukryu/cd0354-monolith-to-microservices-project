## Build
# FROM --platform=linux/arm64 arm64v8/node:14 AS node
# FROM node:16-buster AS node

# Install Ionic and Cordova
# RUN npm install -g @ionic/cli cordova

# FROM --platform=linux/amd64 beevelop/ionic:latest AS node
FROM beevelop/ionic:latest AS ionic

# Create app directory
WORKDIR /usr/src/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./
RUN npm ci
# RUN npm ci --legacy-peer-deps
# Bundle app source
COPY . .
RUN ionic build
## Run 
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=ionic /usr/src/app/www /usr/share/nginx/html