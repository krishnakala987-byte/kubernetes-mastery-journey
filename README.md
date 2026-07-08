# Kubernetes Mastery Journey

A hands-on reference of Kubernetes manifests I wrote while working through the core of Kubernetes, one concept at a time. Each folder is a focused, runnable example rather than a set of notes.

The theory behind these manifests lives in my [devops-mastery-journey](https://github.com/krishnakala987-byte/devops-mastery-journey) repo (folders 24 to 35). This repo is the part you can actually apply to a cluster.

## How to use this repo

Every folder works the same way:

```bash
cd <folder>
kubectl apply -f .
kubectl get all
```

I ran everything on Minikube locally (and some of it on EKS). Nothing here needs a paid cluster.

```bash
minikube start
```

## Learning path

The folders are not numbered, but this is the order I worked through them and the order that makes sense, each step building on the previous one:

| Step | Folder | What it covers |
|------|--------|----------------|
| 1 | pod | the smallest deployable unit, a single pod manifest |
| 2 | replicaset | keeping N copies of a pod alive |
| 3 | deployment | the resource you actually use: deployment + service |
| 4 | workload-management | scaling, rolling updates, rollbacks, HPA and VPA |
| 5 | probes | liveness, readiness and startup probes |
| 6 | resources | requests and limits, plus OOM and CPU starvation demos |
| 7 | configmap | config as volumes and env vars |
| 8 | configmap-nginx | a real example: nginx configured entirely from a configmap |
| 9 | secret | same patterns as configmap, for sensitive values |
| 10 | storage | static PV/PVC, StorageClass, dynamic provisioning |
| 11 | pvc | a deployment actually consuming a claim |
| 12 | statefulset | stable identity and storage per replica, with namespace and headless service |
| 13 | daemonset | one pod per node, the monitoring/logging agent pattern |
| 14 | job | run to completion workloads |
| 15 | cronjob | the same, on a schedule |
| 16 | scheduling | nodeSelector, node affinity, taints and tolerations, pod affinity and anti-affinity |
| 17 | ingress | routing external traffic by host and path |
| 18 | security | namespaces, resource quotas, limit ranges, RBAC, network policies |
| 19 | cluster-administration | helm, CRDs, operators, monitoring, logging |

## The folders with sub-steps

Some topics were too big for one manifest, so they are broken into numbered stages inside the folder:

- **workload-management/**: 01-scaling, 02-rolling-updates, 03-rollbacks, 04-hpa, 05-vpa
- **scheduling/**: 01-node-selector, 02-node-affinity, 03-taints-tolerations, 04-pod-affinity, 05-pod-anti-affinity
- **storage/**: 01-static-pv-pvc, 02-storageclass, 03-dynamic-provisioning, 04-statefulset-storage
- **security/**: 01-namespaces, 02-resource-quotas, 03-limit-ranges, 04-rbac, 05-network-policies
- **cluster-administration/**: 01-helm, 02-crds, 03-operators, 04-monitoring, 05-logging

## Commands I ended up using constantly

```bash
kubectl apply -f <file>.yml
kubectl get pods -o wide
kubectl describe pod <name>     # the first stop for every problem
kubectl logs <pod>
kubectl exec -it <pod> -- sh
kubectl rollout status deployment/<name>
kubectl rollout undo deployment/<name>
kubectl delete -f .             # clean up a whole folder
```

If describe and logs cannot explain a broken pod, the answer is almost always in the events at the bottom of describe.

## Lessons this repo taught me

- Deployments manage replicasets which manage pods. Once that chain clicked, rollouts and rollbacks stopped being magic
- Requests and limits are not optional. The oom-demo and cpu-starvation manifests in resources/ show exactly what happens without them
- Readiness and liveness probes do different jobs, and mixing them up causes restart loops
- StatefulSets are for when pods need a stable name and their own storage, not just for "databases"
- RBAC and network policies are where cluster security actually starts

## Related repos

- [devops-mastery-journey](https://github.com/krishnakala987-byte/devops-mastery-journey) : the full DevOps path, including the Kubernetes theory these manifests came from
- [aws-cloud-journey](https://github.com/krishnakala987-byte/aws-cloud-journey) : AWS hands-on, including the EKS project
- [terraform-zero-to-pro](https://github.com/krishnakala987-byte/terraform-zero-to-pro) : infrastructure as code
- [Python-for-DevOps](https://github.com/krishnakala987-byte/Python-for-DevOps) : the scripting side

## Status

Actively growing as I go deeper into operators, monitoring and production patterns.
