# Fluent Bit

## Purpose

Fluent Bit is a lightweight log collector.

## Responsibilities

- Read Kubernetes container logs
- Parse logs
- Add Kubernetes metadata
- Send logs to Elasticsearch

## Logging Flow

log-generator
    ↓
stdout
    ↓
Fluent Bit
    ↓
Elasticsearch
    ↓
Kibana

## Analogy

Prometheus → Metrics Collector

Fluent Bit → Log Collector