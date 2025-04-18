# Flask Application with Kubernetes Deployment

A simple Flask web application deployed to Kubernetes using Docker.

## Project Overview

This project demonstrates how to:

- Create a simple Flask web application
- Containerize it using Docker
- Deploy it to Kubernetes (using Minikube)
- Push the Docker image to Docker Hub

## Prerequisites

- Docker Desktop
- Kubernetes (Minikube)
- Python 3.9+
- Git

## Application Structure

```
├── app.py                 # Flask application
├── dockerfile             # Docker configuration
├── requirements.txt       # Python dependencies
├── static/                # Static files (CSS, JS)
├── templates/             # HTML templates
└── kubernetes/            # Kubernetes manifests
    ├── deployment.yaml    # Deployment configuration
    ├── service.yaml       # Service configuration
    ├── configmap.yaml     # ConfigMap for environment variables
    ├── ingress.yaml       # Ingress for external access
    └── kustomization.yaml # Kustomize configuration
```

## Getting Started

### Local Development

1. Clone the repository:

   ```bash
   git clone https://github.com/jaggusuperhit/K8-s.git
   cd K8-s
   ```

2. Create a virtual environment:

   ```bash
   python -m venv k8
   k8\Scripts\activate  # Windows
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Run the application:

   ```bash
   python app.py
   ```

5. Access the application at http://localhost:5000

### Docker Deployment

1. Build the Docker image:

   ```bash
   docker build -t flask-app:latest .
   ```

2. Run the Docker container:

   ```bash
   docker run -p 5000:5000 flask-app:latest
   ```

3. Access the application at http://localhost:5000

### Kubernetes Deployment (Minikube)

1. Start Minikube:

   ```bash
   minikube start
   ```

2. Build and load the Docker image into Minikube:

   ```bash
   docker build -t flask-app:final .
   minikube image load flask-app:final
   ```

3. Deploy to Kubernetes:

   ```bash
   kubectl apply -k ./kubernetes/
   ```

4. Access the application:
   ```bash
   minikube service flask-app
   ```

### Using Docker Hub Image

1. Pull the image from Docker Hub:

   ```bash
   docker pull jaggusuperhit/flask-app:latest
   ```

2. Run the Docker container:

   ```bash
   docker run -p 5000:5000 jaggusuperhit/flask-app:latest
   ```

3. Deploy to Kubernetes using the Docker Hub image:
   ```bash
   kubectl apply -k ./kubernetes/
   ```

## Pushing to Docker Hub

1. Log in to Docker Hub:

   ```bash
   docker login
   ```

2. Tag your image:

   ```bash
   docker tag flask-app:latest jaggusuperhit/flask-app:latest
   ```

3. Push to Docker Hub:
   ```bash
   docker push jaggusuperhit/flask-app:latest
   ```

## Kubernetes Commands

### Deployment

```bash
# Apply all resources
kubectl apply -k ./kubernetes/

# Check pod status
kubectl get pods

# Check service status
kubectl get services

# Access the application
minikube service flask-app
```

### Cleanup

```bash
# Delete all resources
kubectl delete -k ./kubernetes/

# Stop Minikube
minikube stop
```

## Troubleshooting

### Common Issues

1. **Image Pull Error**: If you see `ErrImagePull` or `ImagePullBackOff`, make sure the image exists and is accessible.

   ```bash
   # Fix by loading the image into Minikube
   minikube image load flask-app:latest
   ```

2. **CrashLoopBackOff**: Check the logs to see why the pod is crashing.

   ```bash
   kubectl logs <pod-name>
   ```

3. **Service Not Accessible**: Make sure the service is running and the ports are correctly configured.
   ```bash
   kubectl describe service flask-app
   ```

## License

This project is licensed under the MIT License - see the LICENSE file for details.
