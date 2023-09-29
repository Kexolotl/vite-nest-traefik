FROM node:lts-alpine3.17 as build-stage

WORKDIR /code/
ADD package-lock.json .
ADD package.json .
RUN npm ci
ADD . .
RUN npm run build

FROM nginx:stable-alpine as production-stage
COPY --from=build-stage /code/dist/ /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 5173
ENTRYPOINT ["nginx", "-g", "daemon off;"]