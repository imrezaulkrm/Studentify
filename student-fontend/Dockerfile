# Stage 1: Build Angular app
#FROM node:18 as build-stage

#WORKDIR /usr/src/app
# Copy package.json and yarn.lock
#COPY package*.json .
#COPY . .
#RUN npm install
#RUN npm build --prod

# Stage 2: Serve Angular app with NGINX
#FROM nginx:alpine

#COPY --from=build-stage /usr/src/app/dist/student-fontend /usr/share/nginx/html
#COPY nginx.conf /etc/nginx/nginx.conf

#EXPOSE 80

#CMD ["nginx", "-g", "daemon off;"]


# Use the official Node.js image as a base image
FROM node:14

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install project dependencies
RUN npm install

# Copy the rest of the application code to the working directory
COPY . .

# Build the Angular app
RUN npm run build

# Expose the port on which the app will run (adjust as needed)
EXPOSE 4200

# Command to run the Angular application
CMD ["npm", "start"]

