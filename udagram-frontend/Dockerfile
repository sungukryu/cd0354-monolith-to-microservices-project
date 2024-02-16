## Build
# FROM beevelop/ionic:latest AS ionic
# Start with the official Node.js image
FROM node:14 AS ionic

# Install Cordova and Ionic
RUN npm install -g cordova ionic
# Create app directory
WORKDIR /usr/src/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./
RUN npm ci
# Bundle app source
COPY . .
RUN ionic build
## Run 
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html