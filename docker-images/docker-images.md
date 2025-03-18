# Creating and Pushing Docker Images

## Introduction

In this guide, we will create a Docker image for a simple Python Flask web application, run it as a container, and push it to Docker Hub.

## Deploying the Application Manually

Before containerizing the application, we deploy it manually to understand its dependencies:

1. Start a container with an Ubuntu base image:
   ```sh
   docker run -it ubuntu bash
   ```
2. Update the package list:
   ```sh
   apt-get update
   ```
3. Install Python and pip:
   ```sh
   apt-get install -y python python-pip
   ```
4. Install Flask:
   ```sh
   pip install flask
   ```
5. Copy the application code to `/opt/app.py`.
    ```python
    import os
    from flask import Flask
    app = Flask(__name__)
    
    @app.route("/")
    def main():
        return "Welcome!"
    
    @app.route('/how are you')
    def hello():
        return 'I am good, how about you?'
    
    if __name__ == "__main__":
        app.run(host="0.0.0.0", port=8080)
   ```
6. Run the Flask application:
   ```sh
   FLASK_APP=app.py flask run --host=0.0.0.0
   ```

## Writing a Dockerfile

To automate deployment, we create a `Dockerfile`:

```dockerfile
# Use Ubuntu as the base image
FROM ubuntu

# Update and install dependencies
RUN apt-get update && \
    apt-get install -y python python-pip && \
    pip install flask

# Copy application source code
COPY app.py /opt/app.py

# Set the entry point
ENTRYPOINT FLASK_APP=app.py flask run --host=0.0.0.0
```

## Building the Docker Image

Navigate to the project directory and run:

```sh
docker build -t my-simple-webapp .
```

## Running the Container

To run the container:

```sh
docker run -p 5000:5000 my-simple-webapp
```

The application will be accessible at:

```
http://<docker-host-ip>:5000
```

## Pushing the Image to Docker Hub

To share the image publicly:

1. Log in to Docker Hub:
   ```sh
   docker login
   ```
2. Tag the image with your Docker Hub username:
   ```sh
   docker tag my-simple-webapp <your-dockerhub-username>/my-simple-webapp
   ```
3. Push the image:
   ```sh
   docker push <your-dockerhub-username>/my-simple-webapp
   ```

## Conclusion

We successfully created a Docker image, ran a container, and published it to Docker Hub. Try containerizing your own applications and sharing them with the world!