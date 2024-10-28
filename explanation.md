# Overview
This project involved the containerization and deployment of a full-stack yolo application using Docker.


# Requirements
Install the docker engine here:
- [Docker](https://docs.docker.com/engine/install/) 

## How to launch the application 
run docker-compose up -d

![Alt text](image.png)

## Image reduction strategy
- Choice of base image default to node:alpine
- Multi stage docker build for the client microservice

## Dockerfile directives used backend
1. FROM node:alpine
Specifies the base image (a minimal Node.js environment) to build the application.

2. WORKDIR /app
Sets the working directory inside the container to /app, where all subsequent commands will be run.

3. COPY package.json ./
Copies the package.json file to the container to install dependencies.

4. RUN npm install
Executes the installation of Node.js dependencies listed in package.json.

5. COPY . .
Copies all remaining application code from the local directory to the container's working directory.

6. EXPOSE 5000
Informs Docker that the container will listen on port 5000 for incoming connections.

7. CMD ["npm", "start"]
Specifies the command to start the application when the container runs.

## Dockerfile directives used frontend
## Stage 1 (Build Stage):
1. FROM node:alpine AS build
Specifies the base image as node:alpine and names the build stage as build for future reference.

2. WORKDIR /app
Sets the working directory inside the container to /app where all subsequent commands will be executed.

3. COPY package.json ./
Copies the package.json file to the container for installing dependencies.

4. RUN npm install
Installs the Node.js dependencies listed in the package.json file.

5. COPY . .
Copies all application files from the local machine into the container's working directory.

6. ENV NODE_OPTIONS=--openssl-legacy-provider
Sets an environment variable to fix OpenSSL-related issues with Node.js and Webpack.

7. RUN npm run build
Builds the React app in production mode, generating static files in the /app/build directory.

## Stage 2 (Runtime Stage):
1. FROM node:alpine
Specifies the base image as node:alpine for running the built React app.

2. WORKDIR /app
Sets the working directory in the container for serving the app.

3. RUN npm install -g serve
Installs the serve package globally, which is used to serve static files.

4. COPY --from=build /app/build /app/build
Copies the production build output from the first stage (build) to the runtime container.

5. EXPOSE 3000
Informs Docker that the container will listen on port 3000 for incoming connections.

6. CMD [ "serve", "-s", "build", "-l", "3000" ]
Specifies the command to serve the React app using serve on port 3000.


## Docker networking implementation

In the docker-compose.yml, we define a custom network yolo-network using the bridge driver. All services (frontend, backend, MongoDB) are connected to this network, allowing them to communicate with each other by name (e.g., mongo) internally.
The front-end exposes port 3000 and the backend exposes port 5000 to allow external communication


## Docker-compose volume definition and usage
In the docker-compose.yml, the volume mongo-data is used to persist MongoDB data. It ensures that the data stored in the MongoDB container is saved outside the container's lifecycle, so even if the container is stopped or removed, the data remains intact. The volume maps the container's /data/db directory to the mongo-data volume on the host system.


## Docker hub image links
https://hub.docker.com/repository/docker/bugtwent/yolobackend/general
https://hub.docker.com/repository/docker/bugtwent/yolofrontent/general
