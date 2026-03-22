# Homelab Infrastructure

A production-grade Kubernetes homelab built on Proxmox, managed entirely via GitOps with Flux CD.

## Overview

This repository contains the complete infrastructure-as-code for my personal Kubernetes homelab. Every application and configuration is deployed automatically from this git repository using Flux CD — no manual kubectl commands in production.

## Architecture

- **Hypervisor:** Proxmox VE running on bare metal
- **Cluster:** K3S Kubernetes (1 control plane + 2 worker nodes)
- **Networking:** Cilium CNI (eBPF-based)
- **GitOps:** Flux CD (continuous deployment from this repo)
- **Ingress:** Nginx ingress controller

## Applications

| App | Namespace | Description |
|-----|-----------|-------------|
| Forgejo | forgejo | Self-hosted git server |
| Homepage | homepage | Lab dashboard with live cluster stats |
| Grafana + Prometheus | monitoring | Metrics, dashboards, and alerting |
| Uptime Kuma | uptime-kuma | Uptime monitoring for all services |
| CloudNativePG | cloudnativepg | PostgreSQL operator for Kubernetes |

## GitOps Workflow

All changes follow this workflow:
1. Edit YAML manifests in this repository
2. Push to GitHub
3. Flux CD detects the change and applies it to the cluster automatically

## Stack

Proxmox → K3S → Flux CD → Cilium → Nginx Ingress → Applications
