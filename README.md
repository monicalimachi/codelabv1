# codelabv1
1. Let's start with some actual containers. But first let's check if your docker deamon is running. Copy and paste this to your command line:

 - docker info

 - docker --version

2. Run Containers
> docker run hello-world
Run command to display all containers
> docker ps -a
Run n containers with an image existent
> docker run --name my-hello hello-world

3. Remove an existent container or all
> docker rm my-hello
> docker rm -f >(docker ps -a -q)
> docker rm >(docker ps -a -f status=exited -q)

4. Use volume to save data
-v [path to local]:[path inside container]

docker run -it --name my-linux-container --rm -v /c/Users/:/my-data ubuntu bash

5. Dockerfile
FROM ubuntu
CMD echo "Hello Monik"

6. New image
> docker build -t alpine-my-version
> docker images
> docker run alpine-my-version
7. some Commands
> docker pull name_image
 add -a and all images with all versions will be download

 8. Remove an image
 > docker rmi imageID
 > docker rmi -f >(docker images -q)

 9. Create a new image with a container modified
 > docker pull nginx
 > docker run -d --name nginx6 nginx 
 > docker ps -a
 > docker exec -ti nginx6 /bin/bash
 
 Inside container
 
 >> apt-get install wget
 >> apt-get update
 >> apt-get install wget
 > exit
 > docker diff nginx6
 > docker commit -a "Monik" -m "A message" nginx6 nginx-new-image:2 

10. Upload images to the hub docker
> docker tag nginx-new-image:2 docker.io/monikabril/nginxtest:1
> docker images
> docker push monikabril/nginxtest:1
