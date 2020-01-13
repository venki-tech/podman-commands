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

The following example starts a Bash terminal inside the container, and interactively runs some commands in it:
```
sudo podman run -it ubi7/ubi:7.7 /bin/bash
```

Below podman command injects environment variables into the container rhel7 using the switch -e. The below command would print Hello World in two separate lines.
```
sudo podman run -e VAR1=Hello -e VAR2=World rhel7:7.5 printenv VAR1 VAR2
```
