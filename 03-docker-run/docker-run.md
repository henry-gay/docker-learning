# Docker Run Commands

## Running a Specific Version of an Image

We learned that we could use the `docker run redis` command to run a container with the latest version of Redis. But what if we want to run an older version, such as Redis 4.0? We specify the version separated by a colon, which is called a **tag**:

```sh
docker run redis:4.0
```

If you don't specify a tag, Docker defaults to using the `latest` tag, which is managed by the software authors. You can find available versions on [Docker Hub](https://hub.docker.com/).

## Running Interactive Containers

Some applications require user input. By default, Docker does not allow input when running a container. For example, if we run a prompt-based application in a container:

```sh
docker run myapp
```

It will not wait for input. To enable input, we need to use the `-i` option for **interactive mode**:

```sh
docker run -i myapp
```

However, if the application expects a prompt, it still might not display correctly. This is because the container does not have a terminal attached. To solve this, we use the `-t` option for **pseudo-terminal**:

```sh
docker run -it myapp
```

## Port Mapping

When running a web application in a container, we need to map ports so users can access it. For example, consider a web app listening on port `5000` inside the container.

Each container has an internal IP, but it is only accessible from within the Docker host. To make it accessible externally, we map the container's port to a port on the host using `-p`:

```sh
docker run -p 80:5000 mywebapp
```

Now, users can access the application via:

```
http://<docker-host-ip>:80
```

This way, multiple applications can run on different ports. For example, running multiple MySQL instances:

```sh
docker run -p 3306:3306 mysql
```

```sh
docker run -p 8306:3306 mysql
```

However, the same port on the host cannot be mapped multiple times.

## Data Persistence

Containers have their own isolated file system. If a container storing data is removed, all data inside it is lost. To persist data, we use **volumes**.

For example, a MySQL container stores its data in `/var/lib/mysql` inside the container. To persist data, we map a directory on the host to this location:

```sh
docker run -v /opt/datadir:/var/lib/mysql mysql
```

Now, all data is stored at `/opt/datadir` on the host and remains even if the container is deleted.

## Inspecting Containers

To get detailed information about a running container, use:

```sh
docker inspect <container-id>
```

This returns a JSON output containing details such as mounts, network settings, and configuration data.

## Viewing Container Logs

If a container runs in detached mode (`-d`), use the `docker logs` command to view its logs:

```sh
docker logs <container-id>
```

This shows the output that the container writes to standard output.

---