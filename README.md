# podman-commands

Search for rhel on the RH Quay Registries
```
podman search rhel
```

Download the rhel image from the registry
```
podman pull rhel
```

List the images that are present phyiscally
```
podman images
```

Run a container and print a value
```
sudo podman run ubi7/ubi:7.7 echo "Hello!"
```
The above commands pulls the ubi7 (Universal Base Image) from the repo, runs it, and executes the echo command on the container.

Pull and run (-d runs it in background) a http container image from RHEL repos
```
sudo podman run -d rhscl/httpd-24-rhel7:2.4-36.8
```

Check the internal IP address for the running container. The -l flag means the latest container handled by podman is assumed
```
sudo podman inspect -l -f "{{.NetworkSettings.IPAddress}}"
```
