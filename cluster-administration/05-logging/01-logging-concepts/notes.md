# Kubernetes Logging Concepts

Applications write logs to stdout and stderr.

Kubernetes exposes logs using:

kubectl logs <pod-name>

Types of Logs:

1. Application Logs
2. Container Logs
3. Kubernetes Events

kubectl logs
→ Application logs

kubectl describe pod
→ Kubernetes events

Log Flow:

Application
    ↓
stdout/stderr
    ↓
Container Runtime
    ↓
kubectl logs