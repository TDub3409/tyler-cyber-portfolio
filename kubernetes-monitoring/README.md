# Kubernetes Cluster Monitoring — Grafana + Prometheus

> Real-time observability dashboards for a live multi-node Kubernetes cluster, built with Grafana and Prometheus to surface pod health, node capacity, and abnormal behavior at a glance.

![Stack](https://img.shields.io/badge/stack-Grafana%20%2B%20Prometheus-orange)
![Platform](https://img.shields.io/badge/platform-Kubernetes-blue)
![Query](https://img.shields.io/badge/query-PromQL-red)

## Overview

This project delivers a real-time monitoring solution for a live, multi-node
Kubernetes cluster. Using Prometheus as the metrics data source and Grafana for
visualization, the dashboards track pod readiness, service availability, and
per-node resource consumption so that operational problems — a pod failing to
become ready, a node running low on disk, a workload crash-looping — are visible
immediately rather than discovered after something breaks.

I led the project, deciding what the team would monitor and why, and dividing
the build work between myself and a partner. It began as a
Database Design & Implementation course project and grew into a full
infrastructure-observability build on real cluster infrastructure.

## Environment

| Component | Details |
|-----------|---------|
| Orchestration | Kubernetes (6-node cluster: 1 control-plane + 5 workers) |
| Metrics source | Prometheus |
| Visualization | Grafana |
| Query language | PromQL |
| Context | Database Design & Implementation course project; live cluster |

## What the dashboards show

The full dashboard is built from six panels: **Pods Per Namespace**, **Running
Pods**, **Node Storage Capacity**, **Node Allocatable Memory**, **Pod Ready
Status**, and **Pod Restart Count** — together covering workload distribution,
service health, node capacity, and early signs of instability. The panels below
are highlighted in detail.

### Pod Ready Status

At-a-glance readiness for the core cluster services — `clops-operator-deployment`,
`cyberlab-api-server`, `cyberlab-backend`, and `cyberlab-mongodb` — each showing
a clear Ready / Not Ready state. Built on the `kube_pod_status_ready` metric so a
pod that fails to reach a ready state is immediately obvious.

![Pod Ready Status panel](images/pod-ready-status.png)

### Node Storage & Memory

Per-node resource tracking across the control-plane node and all five workers
(`master-0`, `node-0` … `node-4`), covering storage capacity and allocatable
memory. This is what catches a node trending toward exhaustion before it takes
workloads down with it.

![Node resource usage](images/node-usage.png)

### Pod Restart Count

Tracks container restarts per pod over a rolling 24-hour window using
`increase(kube_pod_container_status_restarts_total[24h])`, surfacing
crash-looping workloads that would otherwise stay quiet until they failed
outright.

## A design decision worth calling out

The raw Kubernetes node names returned by Prometheus are long and hard to read on
a dashboard (e.g. `kubernetes-cluster-[id]-node-0`). Rather than accept the noisy
default labels, I used PromQL's `label_replace` to extract a short, readable name
for each node:

```promql
label_replace(
  kube_node_status_allocatable{resource="memory"},
  "short_name", "$1", "node", "kubernetes-cluster-[a-z0-9]+-(.+)"
)
```

I applied the same technique a second time to clean up pod names in the Pod Ready
Status panel. It's a small thing, but it's the difference between dropping in a
pre-built dashboard and actually building one: the panels read cleanly because
the queries were written to reshape the data for the human looking at it.

## What I set out to monitor, and why

The team's goal was to give a clear, immediate read on overall pod and node
health for our school's cluster — both during deployment and in ongoing
operation. We prioritized pod readiness and restart counts because those surface
the two quietest failure modes: a pod that never becomes ready, and one that is
crash-looping. Node storage and memory panels were added so capacity problems
are visible as a trend rather than as an outage.

## What I'd add next

- Alerting rules so the dashboard pages someone instead of waiting to be watched
- Longer-term historical retention for trend analysis rather than only recent state
- Per-namespace resource-quota tracking to flag noisy-neighbor workloads

## Links

- GitHub: https://github.com/TDub3409/tyler-cyber-portfolio
- LinkedIn: https://www.linkedin.com/in/tyler-wood-301294328/

---

*Built by Tyler Wood*
