FROM node:10 AS my-test
WORKDIR /app
COPY . .
RUN yarn install && yarn build

FROM nginx:alpine
WORKDIR /usr/share/nginx/html
RUN rm -rf ./*
COPY --from=my-test /app/build .
ENTRYPOINT ["nginx", "-g", "daemon off;"]
