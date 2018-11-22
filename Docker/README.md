# Docker Commands Cheat Sheet

### List images
`docker images`
`docker image ls`

### Build an image from current directory 
`docker build .` <br />
`docker build -t image-name .` - Name it <br />
`docker build -t image-name:latest .` - Name it and tag it<br />

### Pull down image
`docker pull registry.lab.example.com/node-hello`