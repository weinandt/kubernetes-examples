FROM node

WORKDIR /work/

COPY ./src/package.json .

RUN npm install

COPY ./src/server.js .

ENTRYPOINT [ "node", "server.js" ]