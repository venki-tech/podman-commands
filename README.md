# podman-commands

The below podman commands are run with sudo. If your user id has permissions to run podamn as is, go ahead and ignore the sudo.

Search for rhel on the RH Quay Registries
```
sudo podman search rhel
```

Download the rhel image from the registry
```
sudo podman pull rhel
```

List the images that are present phyiscally
```
sudo podman images
```

Run a container and print a value
```
sudo podman run ubi7/ubi:7.7 echo "Hello!"
```
The above commands pulls the ubi7 (Universal Base Image) from the repo, runs it, and executes the echo command on the container.
When an image is not available locally, podman downloads the image from the attached repositories.

Pull and run (-d meaning detached runs it in background) a http container image from RHEL repos
```
sudo podman run -d rhscl/httpd-24-rhel7:2.4-36.8
```

Check the internal IP address for the running container. The -l flag means the latest container handled by podman is assumed
```
sudo podman inspect -l -f "{{.NetworkSettings.IPAddress}}"
```

Check the internal IP of a specific continer , where in this example the container name is mysql
```
sudo podman inspect -f '{{ .NetworkSettings.IPAddress }}' mysql
```

The following example starts a Bash terminal inside the container, and interactively runs some commands in it:
```
sudo podman run -it ubi7/ubi:7.7 /bin/bash
```

Below podman command injects environment variables into the container rhel7 using the switch -e. The below command would print Hello World in two separate lines.
```
sudo podman run -e VAR1=Hello -e VAR2=World rhel7:7.5 printenv VAR1 VAR2
```

To download a mysql image from the repo, and start it by providing a "--name" and some environment variables
```
sudo podman run --name mysql-basic -e MYSQL_USER=user1 -e MYSQL_PASSWORD=mypa55 -e MYSQL_DATABASE=items -e MYSQL_ROOT_PASSWORD=r00tpa55 -d rhscl/mysql-57-rhel7:5.7-3.14
```

This command starts the Apache HTTP server in the background and returns to the Bash prompt.
```
sudo podman run --name httpd-basic -p 8080:80 -d redhattraining/httpd-parent:2.4
```

To check if the containers are running, the below commands lists the state of each container even if its been recently stopped. 
```
sudo podman ps -a -q
```

To check if the container is running but display on required fields
```
sudo podman ps -a --format="table {{.ID}} {{.Names}} {{.Status}}"
```

To stop a container issue the following command
```
sudo podman stop $(sudo podman ps -a -q)
```

To remove the containers from the list
```
docker rm $(docker ps -a -q)
```

To remove the images from the local repository
```
docker rmi image-name
```
