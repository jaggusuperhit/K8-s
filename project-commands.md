# Kubernetes Flask Project Commands

## Development Commands

| Command        | Description                                     |
| -------------- | ----------------------------------------------- |
| `runapp`       | Run the Flask application using Python directly |
| `rundev`       | Run Flask in development mode with auto-reload  |
| `pip-save`     | Update requirements.txt with current packages   |
| `exit-project` | Exit the project environment                    |

## Docker Commands

| Command                | Description                               |
| ---------------------- | ----------------------------------------- |
| `build` or `dbuild`    | Build Docker image for the application    |
| `drun`                 | Run the application in a Docker container |
| `dps`                  | List all running Docker containers        |
| `dstop [container_id]` | Stop a specific Docker container          |
| `clean`                | Stop and remove all Docker containers     |

## Kubernetes Commands

| Command               | Description                             |
| --------------------- | --------------------------------------- |
| `deploy`              | Deploy the application to Kubernetes    |
| `kpods`               | List all Kubernetes pods                |
| `kservices`           | List all Kubernetes services            |
| `kdeploy`             | List all Kubernetes deployments         |
| `klogs [pod_name]`    | View logs for a specific pod            |
| `kdelete [file.yaml]` | Delete resources defined in a YAML file |

## Complete Workflow Example

```
# 1. Activate the optimized environment
start-project.bat

# 2. Build the Docker image
build

# 3. Deploy to Kubernetes
deploy

# 4. Check if pods are running
kpods

# 5. Check services
kservices

# 6. View application logs
klogs flask-app-[tab]  # Press tab for auto-completion

# 7. When done, clean up Docker containers
clean

# 8. Exit the project environment
exit-project
```

## Minikube Commands

| Command        | Description                                             |
| -------------- | ------------------------------------------------------- |
| `mk-restart`   | Restart Minikube                                        |
| `mk-fix1`      | Fix Minikube by disabling validation (Solution 1)       |
| `mk-fix2`      | Fix Minikube by increasing resources (Solution 2)       |
| `mk-fix3`      | Fix Minikube by using a stable K8s version (Solution 3) |
| `mk-status`    | Check Minikube status                                   |
| `mk-dashboard` | Open Minikube dashboard in browser                      |
| `mk-ip`        | Get Minikube IP address                                 |
| `mk-ssh`       | SSH into Minikube VM                                    |

## Troubleshooting

If you encounter issues:

1. Make sure Docker Desktop is running
2. Ensure Kubernetes is enabled in Docker Desktop
3. Check for errors in the application logs
4. Verify that all required ports are available
5. Make sure your virtual environment is activated

### Fixing Minikube Issues

If you encounter the error "failed to download openapi" or connection issues:

1. Try the `mk-fix1` command first (disables validation)
2. If that doesn't work, try `mk-fix2` (increases resources)
3. If still having issues, try `mk-fix3` (uses a stable Kubernetes version)
4. For network/proxy issues, you may need to set HTTP_PROXY environment variables
