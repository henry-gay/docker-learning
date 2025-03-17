# Advanced Docker Run Commands

## Introduction

In this guide, we explore advanced options available when running Docker containers using the `docker run` command. We will cover topics such as running specific versions of images, attach and detach modes, port mapping, volume mapping, and working with real-life applications like Jenkins.

## Running Specific Versions of an Image

To run a container with a specific version of an image, you can use **tags**. For example, running Ubuntu without a tag defaults to the latest version:

```sh
docker run ubuntu cat /etc/*release*
```

To run a different version, specify the tag:

```sh
docker run ubuntu:17.10 cat /etc/*release*
```

Docker will download the specified version if it is not available locally.

## Attach and Detach Modes

By default, Docker runs containers in the foreground. If you run:

```sh
docker run ubuntu sleep 15
```

You remain attached to the container until it exits. If you need to detach, you can press `CTRL+C`, but this may terminate the container.

To run in the background (detached mode), use the `-d` option:

```sh
docker run -d ubuntu sleep 1500
```

To list running containers:

```sh
docker ps
```

To stop a container:

```sh
docker stop <container_id>
```

To reattach to a running container:

```sh
docker attach <container_id>
```

## Running Persistent Applications

Some applications run continuously, like a timer application that prints the time every second:

```sh
docker run timer
```

By default, this runs in attached mode. To run it in detached mode:

```sh
docker run -d timer
```

You can then use `docker attach` to view its output.

## Running Web Applications with Port Mapping

Running a web server in a container requires exposing ports. For example, to run Jenkins:

```sh
docker run jenkins/jenkins
```

Jenkins runs internally on ports `8080` and `50000`. To access it externally, map its ports to the Docker host:

```sh
docker run -p 8080:8080 -p 50000:50000 jenkins/jenkins
```

Now, Jenkins is accessible via `http://<docker-host-ip>:8080`.

## Inspecting Container IP Addresses

To find the internal IP of a container:

```sh
docker inspect <container_id>
```

Look under the `NetworkSettings` section for the `IPAddress` field.

## Mapping Volumes for Data Persistence

Containers have isolated file systems, so data is lost when they are removed. To persist data, map a directory on the host to the container:

```sh
docker run -v /root/my-jenkins-data:/var/jenkins_home -u root jenkins/jenkins
```

Now, Jenkins configurations will persist even if the container is removed.

## Conclusion

This guide covered advanced Docker run commands, including version tagging, running in detached mode, port mapping, and volume mapping. These concepts are crucial for managing real-world containerized applications efficiently.
