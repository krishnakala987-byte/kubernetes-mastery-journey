Chart:
- Collection of Kubernetes YAML templates

Release:
- Installed instance of a Chart

Example:

Chart:
bitnami/nginx

Release:
my-nginx

Helm Flow:

Chart
  ↓
Templates
  ↓
Values
  ↓
Generated YAML
  ↓
Kubernetes Resources

Important:

helm install my-nginx bitnami/nginx

my-nginx = Release Name

bitnami/nginx = Chart Name
