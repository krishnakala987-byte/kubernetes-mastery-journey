Operator = CRD + Controller Logic

CRD:
Creates a new Kubernetes API object.

Example:
kind: Database

Custom Resource:
An instance of a CRD.

Example:
apiVersion: demo.com/v1
kind: Database
metadata:
  name: mydb

Operator:
Watches custom resources and performs actions automatically.

Example:
Database CR created
↓
Operator notices it
↓
Creates Pod
Creates PVC
Creates Service

Reconciliation Loop:
Desired State vs Actual State

Desired = 3 replicas
Actual = 2 replicas

Operator creates 1 more pod.

Examples:
- Cert Manager
- Prometheus Operator
- ArgoCD Operator
- MongoDB Operator