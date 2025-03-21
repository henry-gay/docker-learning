# Docker Networking

## Introduction

Docker provides built-in networking to allow containers to communicate with each other and with external systems. When you install Docker, it automatically creates three networks:

- **Bridge** – The default network for containers.
- **Host** – Shares the network stack with the host system.
- **None** – Completely isolates the container from all networks.

## Bridge Network

The **bridge** network is a private internal network created by Docker on the host. Containers attached to this network receive an internal IP address (e.g., `172.17.x.x`). Containers in the same bridge network can communicate with each other using these IPs.

To expose a container to the outside world, use **port mapping**:

```sh
docker run -p 5000:5000 my-web-app
```

## Host Network

In the **host** network mode, the container uses the host system’s network stack, meaning:

- The container shares the host’s network interfaces.
- No port mapping is needed.
- You cannot run multiple containers on the same port.

To run a container using the host network:

```sh
docker run --network host my-web-app
```

## None Network

The **none** network mode completely isolates the container from any network, meaning:

- No access to external networks.
- No communication with other containers.

Run a container in an isolated network:

```sh
docker run --network none my-container
```

## Creating Custom Networks

By default, Docker creates one bridge network. To create a custom network:

```sh
docker network create --driver bridge --subnet 192.168.1.0/24 my-custom-network
```

To list all networks:

```sh
docker network ls
```

To attach a container to a custom network:

```sh
docker run --network my-custom-network my-app
```

## Inspecting Network Settings

To check a container’s network details, use:

```sh
docker inspect <container_id>
```

Look under the **NetworkSettings** section to find:

- Network type
- Internal IP
- MAC address

## Container Name Resolution

Containers in the same network can communicate using their **container names** instead of IPs. Docker has a built-in DNS server (`127.0.0.11`) that resolves container names.

Example: A web server accessing a MySQL database using its container name instead of IP.

## How Docker Implements Networking

Docker isolates container networks using **network namespaces**. It then connects them using **virtual Ethernet (veth) pairs** to allow communication between containers.

## Conclusion

Docker networking provides flexibility for container communication. Whether using bridge, host, or none networks, or creating custom networks, understanding these concepts helps in designing scalable containerized applications.