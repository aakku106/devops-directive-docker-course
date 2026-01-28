FROM node:19.4-bullseye AS build
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm i
COPY . .
CMD ["npm","run","dev"]
