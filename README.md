## Docker CLI Commands
### Reference [Guide](https://spin.atomicobject.com/2018/10/04/docker-command-line/#:~:text=The%20--rm%20causes%20Docker,or%20any%20connected%20Docker%20registry)

Run all container 

```bash
docker run 
docker pull repository // To pull a repository from docker hub
``` 

To stop the all or specific image 

```bash
docker stop  // Stop all process
docker stop container-id // stop a specific container
``` 

To list all Process Status

```bash
docker ps [OPTIONS]

OPTIONS: 

	Name, shorthand		Default	Description
	--all , -a			Show all containers (default shows just running)
	--filter , -f		Filter output based on conditions provided
	--format			Pretty-print containers using a Go template
	--last , -n	-1		Show n last created containers (includes all states)
	--latest , -l		Show the latest created container (includes all states)
	--no-trunc			Don’t truncate output
	--quiet , -q		Only display numeric IDs
	--size , -s			Display total file sizes
```
Restart containers 

```bash
docker start container-id OR container name
```
To list out all the images 

```bash
docker images	
``` 

Removing a container 

```bash
docker stop container-id // first stop the container
docker rm container-id // To remove one or more conatainer
```

Remove images akin to deleting an installer 

```bash
docker rmi image-id //To remove one or more images
```
8. To search repo into docker hub
						
```bash
docker search reponame
```	

To run a container on a specific port 

```bash
docker run -p port-no:port-no reponame // To get the latest repo 
docker run -p port-no:port-no reponame:version-number // To get the specfic vesion of repo
```

TO run container into intractive terminal 

```bash
docker run -p port:port -it --name reponame repo
```

To inspect container
	
```bash
docker inspect cotainer-name
```

Run or mapping static website to host images 
	
```bash
#Referring the files from host 

docker run --rm -it --name -p port:port some-nginx -v /some/content:/usr/share/nginx/html:ro -d nginx
Ex:  docker run --rm -it -p 8080:80 --name nginx -v C:\Users\kkant\docker-practice:/usr/share/nginx/html:ro -d some-nginx

#Copy the file into docker containers

docker cp source-file-path container-name:destination-path
Ex: docker cp .\app\. nginx:/usr/share/nginx/html

docker exec -it container-name bash // Open bash console into a container 
Ex: docker exec -it nginx bash // Open bash console into a container 

#Baking a files into image from a container

docker commit container-name  image-name:image-tag
Ex: docker commit nginx furnish:nginx

#Push an image into docker hub 

docker push conrtainer-name/image_name:tag
Ex: docker push kkdker/furnish:nginx
```


Stop multiple running container at a time 
	
```bash
docker stop $(docker ps -q)
```

Remove All container at a time 
	
```bash
docker rm $(docker ps -aq)
```

Remove All volumes at a time 
	
```bash
docker volume rm $(docker volume ls -q)
```
To get the dangling volumes which is not associated any containers

```bash
docker volume ls -f dangling=true

#To remove volume  
docker volume rm $(docker volume ls -qf dangling=true)
```

Remove all images 
	
```bash
docker rmi $(docker images ls -q)

#TO remove dangling images 

docker rmi $(docker images -qf dangling=true)
```

Connect to mysql console

```bash
docker exec -it mysql-container-name mysql -u username -p
```

Connect to another container into embedded DNS server 

```bash
docker run --name service-name --rm --net DNS network name -it image-name sh

docker run --name furnishDecoration --rm --net myngroknet -it kkdker/myrandomimage:latest	
```

