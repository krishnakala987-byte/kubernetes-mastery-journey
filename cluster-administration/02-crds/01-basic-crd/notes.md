CRD = Custom Resource Definition

Purpose:
- Extend Kubernetes API
- Create new resource types

Built-in Resources:
- Pod
- Service
- Deployment

Custom Resources:
- Database
- Certificate
- Application

Example:

kubectl get pods

kubectl get databases

CRD teaches Kubernetes about new resource types.

-------------------------------------------------------------

Custom Resource:

apiVersion: demo.com/v1
kind: Database

metadata:
  name: mydb

CRD:
- Defines a new resource type

Custom Resource:
- Instance of that resource

Example:

CRD = Database type

Custom Resource = mydb

Important:

CRD alone does not create Pods.

An Operator is required to automate actions.


