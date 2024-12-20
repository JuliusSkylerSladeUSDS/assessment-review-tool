# Match the Node version used by the prod/staging GitHub Workflow.
# See: /.github/workflows
FROM node:12.16.2

ENV APP_DIR=/opt/react_app

WORKDIR ${APP_DIR}

RUN npm -g install react-scripts@3.4.1
RUN npm -g install serve

# Copy Node package files first to utilize layer caching.
COPY package*.json .

RUN npm clean-install

ENV PATH ${APP_DIR}/node_modules/.bin:$PATH

COPY . .

# TODO: do whatever GitHub actions does to build and run this.
CMD ["npm", "start"]
