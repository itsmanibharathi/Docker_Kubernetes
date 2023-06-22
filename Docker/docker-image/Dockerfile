FROM node:latest as build
WORKDIR /usr/local/app
COPY ./ /usr/local/app/
RUN npm install
RUN npm run build
FROM nginx:1.13.12-alpine
COPY --from=build /usr/local/app/build /usr/share/nginx/html
EXPOSE 80