pull the ubuntu
run the ubuntu
istall golang
create a go file 
create a directory
copy the go file to the directory from the host to the container -> docekr cp server.go <container id>:/app/server.go
run the go file using go run server.go


start that container in the another terminal using docker exec -it <container id> bash


curl localhost:8080 -> should return Hello, World! 

curl -> command line tool to transfer data from or to a server, using one of the supported protocols (HTTP, HTTPS, FTP, FTPS, SCP, SFTP, TFTP, DICT, TELNET, LDAP or FILE). The command is designed to work without user interaction. 


docker commit <container id> <new image name> -> to create a new image

docker run -d -p 8080:8080 <new image name> -> to run the new image at port 8080