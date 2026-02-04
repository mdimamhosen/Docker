Docker Enginer --->

        What it does: 
            1. Create 
            2. Delete
            3. Stop
            4. Clean Container
            5. Build Image

    Parts:
        1. Dockerd -> Docker Daemon
        2. Container Runtime
            a. Containerd
            b. Runc

Daemon-> Guardian or Someone who did good for us silently invisibly 
So,
Daemon --> 
            1. Background Process
            2. Listens For Request
            2. Serve services to other process

        & Container Runtime works with the Container C D Stop --->

        Containerd -> High Level Container Runtime
        Runc -> Low Level Container Runtime

    Containerd -> Manage Container Life Cycle, Container Storage and Image Manage

    Runc -> C D Stop Container (use namespace and if delete the container also delete the namespace with that associate container)




break -> dokcer run hello-world

