# Kubernetes Deployment for Flask Application

This directory contains Kubernetes manifests to deploy the Flask application to a Kubernetes cluster.

## Files

- `deployment.yaml`: Defines the deployment of the Flask application
- `service.yaml`: Exposes the Flask application within the cluster
- `configmap.yaml`: Contains configuration data for the application
- `ingress.yaml`: Routes external traffic to the application
- `kustomization.yaml`: Ties all resources together for easier deployment

## Prerequisites

- A Kubernetes cluster
- kubectl installed and configured
- Docker image of the application pushed to a registry

## Deployment Steps

1. Build and tag your Docker image:

   ```
   docker build -t flask-app:latest .
   ```

2. Update the image name in `deployment.yaml` with your actual image name:

   ```yaml
   image: flask-app:latest # Replace with your actual image name
   ```

3. If you're using a private Docker registry, you'll need to:

   - Push your image to the registry
   - Create a Kubernetes secret for registry authentication
   - Reference the secret in your deployment

4. If you have a domain name, uncomment and update the host in `ingress.yaml`:

   ```yaml
   - host: flask-app.example.com # Replace with your actual domain
   ```

5. Deploy the application using kubectl:

   ```
   kubectl apply -f ./kubernetes/configmap.yaml
   kubectl apply -f ./kubernetes/deployment.yaml
   kubectl apply -f ./kubernetes/service.yaml
   kubectl apply -f ./kubernetes/ingress.yaml
   ```

   Or use kustomize:

   ```
   kubectl apply -k ./kubernetes/
   ```

6. Check the status of your deployment:
   ```
   kubectl get pods
   kubectl get services
   kubectl get ingress
   ```

## Configuration

You can modify the `configmap.yaml` file to add or change environment variables for your application.

## Scaling

To scale the application, you can modify the `replicas` value in `deployment.yaml` or use the kubectl scale command:

```
kubectl scale deployment flask-app --replicas=3
```
