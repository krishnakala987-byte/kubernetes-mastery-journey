# StorageClass

A StorageClass defines:

1. Which storage provisioner to use
2. Reclaim Policy
3. Volume Binding Mode
4. Dynamic Provisioning behavior

Example:

kubectl get storageclass

Output:

NAME                 PROVISIONER
standard (default)   k8s.io/minikube-hostpath

Important Fields
----------------

Provisioner:
- Creates storage automatically

ReclaimPolicy:
- Delete
- Retain

Delete:
PVC deleted
    ↓
PV deleted

Retain:
PVC deleted
    ↓
PV kept

VolumeBindingMode:
- Immediate
- WaitForFirstConsumer

Immediate:
PV created immediately

WaitForFirstConsumer:
PV created only when Pod is scheduled

Production Preference:
- Retain for databases
- Delete for temporary workloads


What is StorageClass?

Answer:
StorageClass is a Kubernetes resource that enables dynamic provisioning of Persistent Volumes and defines storage behavior such as provisioner, reclaim policy, and volume binding mode.
