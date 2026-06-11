Grafana is the visualization layer.

Prometheus stores metrics.
Grafana displays metrics.

Prometheus Stack automatically:
- Installs Grafana
- Connects Grafana to Prometheus
- Creates dashboards

Flow:

Application
     ↓
Prometheus
     ↓
Grafana



## Real Troubleshooting

Issue:
Grafana dashboards showed "No Data".

Checks:
- Prometheus pod Running
- Grafana pod Running
- Prometheus UI accessible

Error:
dial tcp <prometheus-ip>:9090: i/o timeout

Root Cause:
default-deny NetworkPolicy blocked Prometheus ingress.

Fix:
kubectl delete networkpolicy default-deny

Result:
Grafana dashboards started showing metrics.