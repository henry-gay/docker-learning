# Docker Storage and File Systems

## Introduction

Docker uses a layered architecture to store images, containers, and persistent data efficiently. This guide covers Docker storage drivers, file systems, and how Docker manages data.

## Docker Storage Structure

When Docker is installed, it creates the `/var/lib/docker` directory, which contains:

- **aufs/** – Stores image and container layers
- **containers/** – Holds container metadata
- **image/** – Stores Docker images
- **volumes/** – Manages persistent volumes

## Docker's Layered Architecture

Each Docker image consists of multiple layers:

1. **Base Layer** – Example: Ubuntu
2. **Dependency Layer** – Installed packages
3. **Application Layer** – App source code
4. **Entry Point Layer** – Defines the executable

Each layer stores only the changes from the previous layer, optimizing storage and build time.

## Copy-on-Write Mechanism

When a container modifies a file from an image, Docker copies it to the container's writable layer before making changes. This ensures the base image remains unchanged.

## Managing Persistent Data with Volumes

By default, container data is lost when the container is removed. To persist data, use **volumes**:

### Creating and Using a Volume

```sh
docker volume create data_volume
```

Mount the volume in a container:

```sh
docker run -v data_volume:/var/lib/mysql mysql
```

Even if the container is deleted, `data_volume` will persist.

### Bind Mounts

To use a specific directory on the host:

```sh
docker run -v /data/mysql:/var/lib/mysql mysql
```

This ensures data is stored in `/data/mysql` on the host.

### New Method: Using --mount

The recommended way to mount volumes is by using the `--mount` flag, which provides better readability:

```sh
docker run \
--mount type=bind,source=/data/mysql,target=/var/lib/mysql mysql
```

This method explicitly defines the mount type, source path on the host, and target path inside the container.

## Storage Drivers

Docker supports multiple storage drivers:

- **AUFS** – Default on Ubuntu
- **Overlay2** – Preferred for newer Linux kernels
- **Device Mapper** – Used in CentOS/Fedora
- **BTRFS/ZFS** – Advanced file system options

Docker automatically selects the best storage driver based on the OS.

## Conclusion

Understanding Docker storage, layered architecture, and volumes helps optimize containerized applications for performance and data persistence. Choose the appropriate storage driver based on your OS and workload.