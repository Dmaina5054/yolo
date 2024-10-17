#use minimal node js image
FROM node:alpine

#setting working directory
WORKDIR /app

#copying package json
COPY package.json ./

#installing dependencies
RUN npm install 

#copying rest of application code
COPY . .

#exposing port
EXPOSE 5000

#starting app
CMD ["npm" "start"]
