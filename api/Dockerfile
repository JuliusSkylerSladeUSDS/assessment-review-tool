# Match the Node version used by the prod/staging GitHub Workflow.
# See: /.github/workflows
FROM node:14.21.3-alpine

ENV APP_DIR=/opt/node_app/app \
    PORT=9099

# Install typescript to get access to tsc.
RUN npm install -g typescript

WORKDIR $APP_DIR

# Copy Node package files first to utilize layer caching.
COPY package*.json .

RUN npm clean-install

# Copy the rest of the application code.
COPY . .

# The prod/staging GitHub workflow runs npm run build.
RUN npm run build
WORKDIR $APP_DIR/build

EXPOSE $PORT
# The prod/staging buildpack manifest runs node server.js
CMD ["node", "server.js"]
