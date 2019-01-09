# Docker Commands Cheat Sheet

### Login to a registry
`docker login -u username -p password registy.example.com`

### List images
`docker images`
`docker image ls`

### Build an image from current directory 
`docker build .` <br />
`docker build -t image-name .` - Name it <br />
`docker build -t image-name:latest .` - Name it and tag it<br />

### Pull down image
`docker pull registry.lab.example.com/node-hello`

### Push to a registry
`docker push docker-registry-default.apps.lab.example.com/schedule-is/phpmyadmin:4.7`

### Load image from a tar ball
`docker load -i phpmyadmin-latest.tar`

### Tagging images
`docker tag hash tag-name`

## Container commands

#### List containers
`docker ps`
`docker ps -a` Include those not running

#### Delete containers
`docker rm <container-id>`
`docker rm $(docker ps -a -q)` Remove all containers in one go