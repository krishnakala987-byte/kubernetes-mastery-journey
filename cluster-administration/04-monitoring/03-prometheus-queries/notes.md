# Prometheus Queries

Prometheus stores metrics as time-series.

Examples:

up
Checks if target is healthy.

node_cpu_seconds_total
CPU metric from Node Exporter.

container_memory_usage_bytes
Container memory usage.

rate(container_cpu_usage_seconds_total[5m])
CPU usage over last 5 minutes.

kube_pod_info
Information about pods.

kube_node_info
Information about nodes.