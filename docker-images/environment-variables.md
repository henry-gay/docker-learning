# Using Environment Variables in Docker

## Introduction

In this guide, we will learn how to use environment variables in a Docker container to make applications more configurable and flexible.

## Why Use Environment Variables?

Consider a simple web application written in Python that displays a web page with a background color. Initially, the color is hardcoded in the application:

```python
background_color = "red"
```

If we need to change the color in the future, modifying the application code is not ideal. Instead, we should move such configurations to an environment variable.

## Setting Environment Variables in Docker

To pass environment variables when running a Docker container, use the `-e` option with the `docker run` command:

```sh
docker run -e APP_COLOR=blue my-web-app
```

Now, the application will use the color specified in the `APP_COLOR` variable.

## Deploying Multiple Containers with Different Configurations

To run multiple instances of the application with different background colors:

```sh
docker run -e APP_COLOR=blue my-web-app
```

```sh
docker run -e APP_COLOR=green my-web-app
```

Each instance will have a different background color as per the assigned environment variable.

## Inspecting Environment Variables in a Running Container

To check the environment variables of a running container, use:

```sh
docker inspect <container_id>
```

Look under the **Config** section for the list of environment variables.

## Conclusion

Environment variables help keep configuration separate from the application code, making deployments more flexible and manageable in Docker.

