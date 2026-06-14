# Centralized Logging Demo

Architecture:

log-generator
      ↓
Fluent Bit
      ↓
Elasticsearch
      ↓
Kibana

Goal:

Generate logs from a pod.

Collect them automatically.

Store them centrally.

Search them from Kibana.