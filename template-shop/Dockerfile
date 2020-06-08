# use 12.10.0-alpine
FROM node:12.10.0-alpine as build-stage

WORKDIR /src

COPY package.json ./
RUN npm install

COPY . .

RUN npm run build

# production stage
FROM nginx:alpine as production-stage
RUN rm -rf /usr/share/nginx/html/*
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=build-stage /src/build /usr/share/nginx/html
EXPOSE 80
CMD [ "nginx", "-g", "daemon off;" ]