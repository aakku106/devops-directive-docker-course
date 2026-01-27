# FROM node, means node:latest, which could be a problem most of the time, so use 
#  so lest do 19.6-alpine
FROM node:19.6-alpine

#  just look specifing alpine drastically reduced disk usage size
##IMAGE                  ID             DISK USAGE   CONTENT SIZE   EXTRA
##api-node:0             d7d346b175e0       1.04GB             0B
##api-node:1             3ca9952a6daa       1.17GB             0B
##api-node:2             7c69f0f0f6e7        216MB             0B
##postgres:15.1-alpine   91c930beec93        241MB             0B    U

WORKDIR /usr/src/app
ENV NODE_ENV production

COPY package*.json ./
#RUN npm i
## Just using ci --only=production
##our Size decreases from
##api-node:4             826821b29e56        216MB             0B
##api-node:5             cc8138677320        181MB             0B

RUN --mount=type=cache,target=/usr/src/app/.npm \
  npm set cache /usr/src/app/.npm && \
  npm ci --only=production
USER node
COPY --chown=node:node ./src/ .

EXPOSE 3000

CMD ["node","index.js"]

