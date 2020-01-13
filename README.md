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
The above commands pulls the ubi7 image from the repo, runs it, and executes the echo command on the container.

