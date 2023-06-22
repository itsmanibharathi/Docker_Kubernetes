# React + Docker 

>create a reacte application 

```
npx create-react-app
```

> Dockerfile

```
FROM node:latest as build
WORKDIR /usr/local/app
COPY ./ /usr/local/app/
RUN npm install
RUN npm run build
FROM nginx:1.13.12-alpine
COPY --from=build /usr/local/app/build /usr/share/nginx/html
EXPOSE 80
```
Use Nginx for Static web server

> Build image

```
Docker build [Docker file path] -t [Image name]
```
> Run container

```
docker run -p [external port]:[internal port] [Docker image]
```

