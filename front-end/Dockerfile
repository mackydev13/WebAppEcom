FROM node:16.14-buster

WORKDIR /home/node
COPY . /home/node/

RUN npm i -g npm@8.5.0

USER node

CMD bash -c "npm install && npm run dev"

EXPOSE 3000
