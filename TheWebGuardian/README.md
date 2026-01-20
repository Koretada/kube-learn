# The Web Guardian

This project is a simple Kubernetes-based web application serving a static HTML page using Nginx.

## Project Structure

- `namespace.yaml`: Defines the `thewebguardian` namespace.
- `configmap.yaml`: Stores the HTML content (`index.html`).
- `nginx-pod.yaml`: The Pod definition running Nginx, mounting the ConfigMap.
- `service.yaml`: Exposes the Pod via a NodePort service.

## Prerequisites

- A running Kubernetes cluster (e.g., Minikube, Kind, or a cloud provider).
- `kubectl` command-line tool configured to communicate with your cluster.

## Deployment

Follow these steps to deploy the application:

1. **Create the Namespace**
   ```bash
   kubectl apply -f namespace.yaml
   ```

2. **Create the ConfigMap**
   ```bash
   kubectl apply -f configmap.yaml
   ```

3. **Deploy the Pod**
   ```bash
   kubectl apply -f nginx-pod.yaml
   ```

4. **Expose the Service**
   ```bash
   kubectl apply -f service.yaml
   ```

## Verification

Check if the resources are running:

```bash
kubectl get all -n thewebguardian
```

Access the application:
- If using **Minikube**:
  ```bash
  minikube service web-access -n thewebguardian
  ```
- Or access via NodePort `30005` on your cluster node's IP.

## Cleanup

To remove the deployed resources:

```bash
kubectl delete namespace thewebguardian
```
