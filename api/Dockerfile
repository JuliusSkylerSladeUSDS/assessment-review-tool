FROM node:14.21.3-alpine

ENV APP_DIR=/opt/node_app/app \
    PORT=9000

RUN npm install -g typescript

WORKDIR $APP_DIR

COPY package*.json .

RUN npm clean-install

COPY . .

RUN npm run build
WORKDIR $APP_DIR/build

EXPOSE $PORT

CMD ["node", "server.js"]
