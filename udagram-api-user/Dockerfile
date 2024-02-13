# FROM --platform=linux/amd64 node:13
FROM --platform=linux/arm64 arm64v8/node:14 AS node

# Create app directory
WORKDIR /usr/src/app
# Install app dependencies

COPY package*.json ./
# RUN npm rebuild bcrypt --build-from-source
# RUN npm install bcrypt
RUN rm package-lock.json
RUN npm install 
RUN npm ci 
# Bundle app source
COPY . .
EXPOSE 8080
CMD [ "npm", "run", "prod" ]