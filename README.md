# node-mongo-docker
A node and express docker template with Mongo


# How to setup Docker
Dockerfile is the blue print for container, it creates image from our container

To make the image based on the instruction in Dockerfile, run this command: 
```bash
docker build -t simple-backend .
```

To see your docker images run this command: 
```bash
docker images
```

To run docker: 
```bash
docker run -p 4000:4000 simple-backend
```

To check what container is running: 
```bash
docker ps
```

You can start or stop a docker image by:
```bash
docker start imageid
```

```bash
docker stop imageid
```


