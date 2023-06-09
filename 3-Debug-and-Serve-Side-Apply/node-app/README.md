# Node.js HTTP Server

This is a simple Node.js HTTP server that runs inside a Docker container using a Distroless Node.js base image. This server simply responds to any HTTP request with "Hello, world!".

## Prerequisites

1. Docker
2. Kubernetes
3. A Docker registry to push your Docker images (e.g., Docker Hub, Google Container Registry, etc.)

## How to run

### Build the Docker image

To build the Docker image, navigate to the directory containing the Dockerfile and the `app.js` file, and run the following command:

```bash
docker build -t my-node-app .
```

This will build the Docker image and tag it as my-node-app.

## Push the Docker image to a registry

Before you can run the image in a Kubernetes cluster, you need to push it to a Docker registry that your Kubernetes cluster can access. To tag and push the image, run:

``` bash
docker tag my-node-app:latest my-docker-registry/my-node-app:latest
docker push my-docker-registry/my-node-app:latest
Replace my-docker-registry with the address of your Docker registry.
```

## Deploy to Kubernetes
To deploy the application to a Kubernetes cluster, you need to apply the Kubernetes deployment configuration. Update the image field in the deployment.yaml file to point to the Docker image in your Docker registry, and then run:

```bash
kubectl apply -f deployment.yaml
``

This will create a deployment named my-deployment and a ConfigMap named my-configmap in your Kubernetes cluster.