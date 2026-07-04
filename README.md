# kubernetes-mastery-journey

A hands-on reference of Kubernetes manifests I wrote while working through the core of Kubernetes, one concept at a time. Each folder is a focused, runnable example rather than a set of notes.

## What is covered

- Workloads: pods, deployments, replicasets, statefulsets, daemonsets, jobs, and cronjobs.
- Configuration and secrets: configmaps and secrets, including a configmap-backed nginx example.
- Storage: persistent volume claims and storage.
- Networking: ingress.
- Scheduling and resources: node scheduling, resource requests and limits, and liveness/readiness probes.
- Security: RBAC and pod security.
- Cluster administration and general workload management.

Each directory holds the YAML for that topic, so it can be applied and inspected on any cluster with kubectl.
