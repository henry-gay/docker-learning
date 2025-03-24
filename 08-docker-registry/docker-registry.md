# Docker Registry

## What is a Docker Registry?
If containers were the rain, then they would rain from the Docker Registry, which acts as the clouds. A Docker Registry is a central repository where Docker images are stored. It enables users to push, pull, and manage container images efficiently.

## Understanding Image Naming Convention

Let's take a simple example of running an Nginx container:
```sh
docker run nginx
```

When we run this command, Docker pulls the `nginx` image from a registry. But where exactly is this image coming from?

- The image name follows Docker's naming convention.
- `nginx` is the repository name.
- The full name is `library/nginx` when no specific account is provided.
- The `library` prefix indicates an official Docker Hub image.
- The username is typically your Docker Hub account name or an organization name.

### Where Are Images Stored?
By default, images are pulled from Docker's official registry, **Docker Hub** (`docker.io`). Other popular registries include:
- **Google Container Registry (GCR.io)** – Used for Kubernetes-related images.
- **Amazon Elastic Container Registry (ECR)** – AWS's private registry solution.
- **Azure Container Registry (ACR)** – Microsoft's cloud container registry.

## Public vs. Private Registries
- **Public Registry**: Open to everyone (e.g., Docker Hub, GCR.io).
- **Private Registry**: Restricted access, requiring authentication.

### Using Private Registries
To use a private registry, log in first:
```sh
docker login myprivateregistry.com
```
Then pull an image:
```sh
docker pull myprivateregistry.com/myimage
```
If authentication is missing, Docker will return an error stating that the image cannot be found.

## Running Your Own Private Registry
If you need an internal registry for an on-premises deployment, you can run your own **Docker Registry**. The Docker registry itself is a containerized application.

To deploy a local registry:
```sh
docker run -d -p 5000:5000 --name registry registry:2
```
This starts a registry on **port 5000**.

### Pushing Images to a Private Registry
1. **Tag the Image**
```sh
docker tag myimage localhost:5000/myimage
```
2. **Push the Image**
```sh
docker push localhost:5000/myimage
```

### Pulling Images from a Private Registry
From the same host:
```sh
docker pull localhost:5000/myimage
```
From another host:
```sh
docker pull <docker-host-ip>:5000/myimage
```

## Summary
- Docker Registry is a central repository for Docker images.
- Docker Hub is the default public registry.
- Private registries require authentication.
- You can run your own registry using the `registry` Docker image.
- Images can be tagged, pushed, and pulled to and from private registries.

Now, practice setting up and using private Docker registries!
