FROM node:10

WORKDIR /usr/src/app/src
WORKDIR /usr/src/app

COPY ./src/package*.json ./

RUN npm install

COPY ./src ./src

VOLUME /usr/src/app/src

EXPOSE 8080
CMD [ "node", "./src/server.js" ]
