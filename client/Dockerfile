#including multistage builds
FROM node:alpine AS build 

#set working directory
WORKDIR /app

#copying package json
COPY package.json ./

#installing dependencies
RUN npm install

#copying rest of the code
COPY . .

#fix for error:0308010C:digital envelope routines::unsupported
# Add the OpenSSL legacy provider flag to resolve crypto issues
ENV NODE_OPTIONS=--openssl-legacy-provider
#build for react production
RUN npm run build 

#STAGE 2

#use node:alpine image to server app
FROM node:alpine 

#setting working directory for the server
WORKDIR /app

#installing a simple http server to serve build
RUN npm install -g serve

#copy build output from build stage
COPY --from=build /app/build /app/build

#exposing port for the app
EXPOSE 3000

#serving the app
CMD [ "serve", "-s", "build", "-l", "3000" ]
