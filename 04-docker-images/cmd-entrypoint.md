# CMD vs ENTRYPOINT in Docker

## Introduction

In this guide, we will explore the differences between `CMD` and `ENTRYPOINT` instructions in Docker, how they define the process a container runs, and how to override these commands during runtime.

## Understanding CMD

When you run a Docker container from an Ubuntu image:

```sh
docker run ubuntu
```

The container starts and exits immediately. This happens because containers are meant to run a specific process. If the process stops, the container stops as well.

Docker images typically define a default command using the `CMD` instruction in the `Dockerfile`. For example, in an Nginx image:

```dockerfile
CMD ["nginx", "-g", "daemon off;"]
```

For Ubuntu, the default `CMD` is `bash`. Since `bash` requires a terminal, and none is provided by default, it exits immediately.

## Overriding CMD

To specify a different command at runtime, append it to `docker run`:

```sh
docker run ubuntu sleep 5
```

This overrides the default command, making the container execute `sleep 5` before exiting.

To make this change permanent, create a custom image:

```dockerfile
FROM ubuntu
CMD ["sleep", "5"]
```

Build the image:

```sh
docker build -t ubuntu-sleeper .
```

Now, running the container will always execute `sleep 5`:

```sh
docker run ubuntu-sleeper
```

If you specify a new command, it completely replaces `CMD`:

```sh
docker run ubuntu-sleeper sleep 10
```

## Understanding ENTRYPOINT

The `ENTRYPOINT` instruction is similar to `CMD`, but it does not get replaced when passing arguments in `docker run`. Instead, arguments are appended:

```dockerfile
FROM ubuntu
ENTRYPOINT ["sleep"]
```

Now, if you run:

```sh
docker run ubuntu-sleeper 10
```

Docker executes:

```sh
sleep 10
```

## Combining ENTRYPOINT and CMD

To provide default arguments while allowing runtime overrides, use both:

```dockerfile
FROM ubuntu
ENTRYPOINT ["sleep"]
CMD ["5"]
```

- If no arguments are given, it defaults to `sleep 5`
- If an argument is provided, it overrides `CMD`, but `ENTRYPOINT` remains unchanged

Example:

```sh
docker run ubuntu-sleeper 10  # Runs sleep 10
```

## Overriding ENTRYPOINT at Runtime

To completely override `ENTRYPOINT`, use the `--entrypoint` flag:

```sh
docker run --entrypoint sleep2.0 ubuntu-sleeper 10
```

Now, `sleep2.0 10` is executed instead of `sleep 10`.

## Conclusion

- `CMD` provides default arguments but can be overridden entirely.
- `ENTRYPOINT` defines the executable, and `CMD` provides optional parameters.
- Using both together allows flexibility while keeping defaults.
- `--entrypoint` can override `ENTRYPOINT` during runtime.

Understanding these instructions helps in designing more modular and configurable Docker images.