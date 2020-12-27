# node-mongo-docker
A node and express docker template with Mongo


# How to setup Dockerfile
Dockerfile is the blue print for container, it creates image from our container

To make the image based on the instruction in Dockerfile, run this command: 
```bash
docker build -t simple-backend .
```

To see your docker images run this command: 
```bash
docker images
```

To delete the docker image run this:
```bash
docker rmi image_id
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
docker start image_id
```

```bash
docker stop image_id
```

# How to setup docker compose

Compose will help to manage multiple containers and set the entire backend with a single file. We need to add a file named "docker-compose.yml"

This file will allow docker to know what services we want to compose and what are the application that we want to start

Look at docker-compose/yml file:

  - Add links to the container(like here we added - mongo as link). It means that server can not work unless we have mongo started.

  - Introduce the mongo service(we need to have a volume to have a dynamic data). We used an image with the port 27017 for that.

Note: So first the mongo container will run and then our app will run on port 4000

  - Make sure that we shared our Volume in docker:
    Open the docker preferences on Mac and go to the "Resources/File Sharing" you should see the /Volumes attached to docker, if it's not there you should attach one

Now in our code we should connect to mongo on port 27017 and not the localhost

```bash
mongoose.connect('mongodb://mongo:27017/crm', {
    useMongoClient: true
});
```
Now we are ready to make our image by docker compose, it bulids all the images:
```bash 
docker-compose build
```
Once we have the images we can run the containers by:
```bash
docker-compose up
```

To make sure that docker will run the mongo contianer first we can use -d, it will pull the images, then start the container and then mongo will start
```bash
docker-compose up -d mongo 
```

Then:
```bash
docker-compose up -d app
```

To check if everything is working correctly we can use:
```bash
docker ps
docker logs image_id
```
Now if you check [localhost:4000](http://localhost:4000/) you will see that the server is running.

To stop the containers you can use:
```bash
docker stop
```