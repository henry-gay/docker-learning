# Basic Docker Commands

We now look at some of the Docker commands. At the end of this lecture, you will go through a hands-on quiz, where you will practice working with these commands.

## Running a Container

The `docker run` command is used to run a container from an image. Running the following command pulls the image down (if not already present) and starts a container:

```sh
docker run nginx
```

For subsequent executions, the same image is reused.

## Listing Containers

To list all running containers:

```sh
docker ps
```

To list all containers, including stopped ones:

```sh
docker ps -a
```

## Stopping a Container

To stop a running container, use:

```sh
docker stop <container_id_or_name>
```

## Removing a Container

To remove a stopped container:

```sh
docker rm <container_id_or_name>
```

## Listing Docker Images

To see a list of available images and their sizes:

```sh
docker images
```

## Removing an Image

To remove an image:

```sh
docker rmi <image_id_or_name>
```

**Note:** Ensure no containers are using the image before removing it.

## Pulling an Image Without Running It

To download an image without running it:

```sh
docker pull ubuntu
```

## Append a Command

To run a process in the container :

```sh
docker run ubuntu sleep 5
```

## Running a Command Inside a Container

To execute a command inside a running container:

```sh
docker exec <container_id_or_name> cat /etc/hosts
```

## Running a Container in the Background

To run a container in detached mode:

```sh
docker run -d nginx
```

## Attaching to a Running Container

To reattach to a running container:

```sh
docker attach <container_id_or_name>
```

**Note:** You can use the first few characters of the container ID if it's unique.

## Running a Web Application

Example of running a simple web server:

```sh
docker run kodekloud/simple-webapp
```

By default, this runs in the foreground. To stop it, press `CTRL + C`.

To run it in the background:

```sh
docker run -d kodekloud/simple-webapp
```

Then, use `docker ps` to check the running container.

## Summary

These are the fundamental Docker commands to get started. More advanced topics will be covered in upcoming lectures.

