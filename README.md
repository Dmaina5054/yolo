# Overview
This project involved the containerization and deployment of a full-stack yolo application using Docker.


# Requirements
Install the docker engine here:
- [Docker](https://docs.docker.com/engine/install/) 

## How to launch the application 
run docker-compose up -d

![Alt text](image.png)

## Image reduction strategy
- Multi stage docker build for the client microservice
- Choice of base image default to node:alpine

## Docker hub image links
https://hub.docker.com/repository/docker/bugtwent/yolobackend/general
https://hub.docker.com/repository/docker/bugtwent/yolofrontent/general