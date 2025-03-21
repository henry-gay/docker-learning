# Docker Engine

## Introduction

Docker Engine is the core component that enables containerization. It consists of three main parts:

- **Docker Daemon**: Manages Docker objects like images, containers, volumes, and networks.
- **REST API Server**: Provides an interface for external applications to interact with the daemon.
- **Docker CLI**: The command-line tool used to run and manage containers.

The Docker CLI can interact with a local or remote Docker Engine using the `-H` flag:

```sh
docker -H=10.123.2.1:2375 run nginx
```

## How Docker Provides Isolation

Docker uses **namespaces** to isolate containers. These include:

- **Process ID (PID) namespaces**: Each container sees its processes starting from PID 1.
- **Network namespaces**: Each container has its own virtual network stack.
- **Mount namespaces**: Controls file system access per container.

### Process ID Namespace Example

If we run an Nginx container:

```sh
docker run -d --name mynginx nginx
```

Inside the container:

```sh
docker exec -it mynginx ps aux
```

The process will have PID 1 inside the container, but it will have a different PID on the host.

## Resource Management

By default, containers share system resources without restrictions. Docker uses **cgroups** (control groups) to limit resource usage.

### Limiting CPU Usage

```sh
docker run --cpus=0.5 nginx
```

This ensures the container does not use more than 50% of the CPU.

### Limiting Memory Usage

```sh
docker run --memory=100m nginx
```

This restricts memory usage to 100 MB.

## Conclusion

Docker Engine provides process isolation using namespaces and manages resource allocation using cgroups. Understanding these concepts helps optimize container performance and resource usage efficiently.