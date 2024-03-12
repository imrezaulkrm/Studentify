# Stage 1: Build Angular app
FROM node:alpine as build-stage

WORKDIR /usr/src/app

COPY package*.json ./
RUN npm install
COPY . .
RUN npm build --prod

# Stage 2: Serve Angular app with NGINX
FROM nginx:alpine

COPY --from=build-stage /usr/src/app/dist/student-fontend /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]


