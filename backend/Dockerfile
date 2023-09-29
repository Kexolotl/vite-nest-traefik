FROM node:lts-alpine3.17

WORKDIR /app

ADD package-lock.json .
ADD package.json .
RUN npm ci
ADD . .
RUN npm run build
RUN npm prune --production --no-fund --no-audit

EXPOSE 3000
CMD [ "npm", "run", "start:prod" ]