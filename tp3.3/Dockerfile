FROM node:18

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

COPY package.json .
COPY package-lock.json .

RUN npm install

COPY index.js .

CMD [ "npm", "start"]