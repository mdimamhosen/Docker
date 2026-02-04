FROM ubuntu:24.04
-> layer 0
    -> Check the cache for ubuntu:24.04
    -> Cache miss then pull ubuntu:24.04
    -> Image loaded

RUN apt-get update && apt-get install -y 
-> layer 1
    -> Create a temporary container from the image(layer 0)
    -> run command in the temporary container and update the filesystem
    -> apt-get update && apt-get install -y 
    -> Commit the changes to a new image (layer 1)
    -> Image created
    -> Remove the temporary container

RUN apt-get install -y golang
-> layer 2
    -> Create a temporary container from the image(layer 1)
    -> apt-get install -y golang
    -> Commit the changes to a new image (layer 2)
    -> Image created
    -> Remove the temporary container

WORKDIR /app
-> layer 3
    -> Create a temporary container from the image(layer 2)
    -> WORKDIR /app
    -> Commit the changes to a new image (layer 3)
    -> Image created
    -> Remove the temporary container

COPY ./server.go ./server.go
-> layer 4
    -> Create a temporary container from the image(layer 3)
    -> COPY ./server.go ./server.go
    -> Commit the changes to a new image (layer 4)
    -> Image created
    -> Remove the temporary container

CMD ["go", "run", "server.go"]
-> layer 5
    -> Create a temporary container from the image(layer 4)
    -> CMD ["go", "run", "server.go"]
    -> Commit the changes to a new image (layer 5)
    -> Image created
    -> Remove the temporary container


docker build -t firstContainer .
Final image built: firstContainer:latest
And the layer 5 name is = firstContainer:latest



Intermediate Images Created During Build Process are also stored in Docker Daemon's local storage.
you can see them by running the command: docker images -a
# docker build --no-cache -t firstContainer .
This command forces Docker to not use any cached layers and rebuild all layers from scratch.

# docker build -t firstContainer .
This command will use cached layers if available, speeding up the build process.

Docker saves the intermediate images cause they can be reused in future builds, reducing build time and resource consumption.