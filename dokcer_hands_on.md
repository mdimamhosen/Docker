docker rmi <image_name_or_id>

to see container images on your system.
docker ps 
docker ps -a -> to see all containers including stopped ones.

docker pull <image_name> -- to download an image from Docker Hub.
docker images -> to see all downloaded images on your system.
docker run <image_name> -> to create and start a container from an image.
docker run -it <image_name> /bin/bash -> to start a container in interactive mode with a bash shell.
docker stop <container_id_or_name> -> to stop a running container.
docker start <container_id_or_name> -> to start a stopped container.
docker rm <container_id_or_name> -> to remove a stopped container.
docker rmi <image_name_or_id> -> to remove an image from your system.
# Docker Hands-On Guide


docker exec -it <container_id_or_name> bash -> to access a running container's shell.


# -it -> stdin + pseudo tty for interactive terminal
# tty -> terminal emulator for text input/output  

docker run myubuntu1 ubuntu:24.04 bash -> if we do without -it it will run and exit immediately.


docker run -i <image_name> <program_name> ->   to run a program in interactive mode without a tty. this is useful for running commands that do not require user interaction. like cat, grep, etc.

docker run -t <image_name> <program_name> -> to run a program with a tty but without stdin. this is useful for running commands that require a terminal but do not need user input. like top, htop, etc.


docker build . -> to build a Docker image from a Dockerfile in the current directory.
docker build -t <image_name>:<tag> . -> to build a Docker image with a specific name and tag.
docker images -> to see all built images on your system.
docker run <image_name>:<tag> -> to create and start a container from a specific image and tag.