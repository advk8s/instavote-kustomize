# Kubernetes Deployment for Dev Environment

This project contains Kubernetes manifests for deploying a set of applications in a development environment. The applications included are:

- **Vote**: A voting application that allows users to cast votes.
- **Redis**: A lightweight in-memory data structure store used as a database, cache, and message broker.
- **Worker**: A background worker that processes votes.
- **Database (Postgres)**: A relational database for storing application data.
- **Result**: An application that displays the results of the voting.

## Directory Structure

The project is organized as follows:

```
k8s-deployment
├── kustomization.yaml          # Main Kustomization file for the project
├── dev
│   ├── kustomization.yaml      # Kustomization file for the dev environment
│   ├── vote-deployment.yaml    # Deployment manifest for the vote application
│   ├── vote-service.yaml       # Service manifest for the vote application
│   ├── redis-deployment.yaml   # Deployment manifest for the Redis application
│   ├── redis-service.yaml      # Service manifest for the Redis application
│   ├── worker-deployment.yaml   # Deployment manifest for the worker application
│   ├── db-deployment.yaml      # Deployment manifest for the database application
│   ├── db-service.yaml         # Service manifest for the database application
│   ├── result-deployment.yaml   # Deployment manifest for the result application
│   ├── result-service.yaml     # Service manifest for the result application
```

## Deployment Instructions

1. **Set up your Kubernetes cluster**: Ensure you have access to a Kubernetes cluster and that `kubectl` is configured to communicate with it.

2. **Navigate to the project directory**:
   ```
   cd k8s-deployment
   ```

3. **Deploy the applications**:
   Use `kubectl` to apply the Kustomization file for the dev environment:
   ```
   kubectl apply -k dev/
   ```

4. **Access the applications**:
   - The Vote application can be accessed via NodePort on port 30000.
   - The Result application can be accessed via NodePort on port 30100.

## Notes

- Ensure that the images specified in the deployment manifests are available in your container registry.
- Modify the replicas and other configurations as needed based on your requirements.
- This project is intended for development purposes and may require additional configurations for production use.