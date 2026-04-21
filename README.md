# platform-ops-mcp-server

> An MCP (Model Context Protocol) server that exposes platform operations tools — Kubernetes, Terraform, and Prometheus — as callable functions for LLM-powered agents.

---

## Overview

`platform-ops-mcp-server` is a portfolio project that bridges the gap between AI agents and real platform infrastructure. It implements the **Model Context Protocol (MCP)** to expose platform engineering operations as structured, agent-callable tools.

This allows any MCP-compatible AI agent (e.g., Claude, LangGraph agents) to:

- Inspect and manage **Kubernetes** workloads
- Trigger and query **Terraform** operations
- Query **Prometheus** metrics and alerts

Rather than hardcoding API calls inside an agent, this server acts as a clean, reusable interface layer — making AI-driven platform automation composable and production-safe.

---

## Motivation

Platform engineers are increasingly integrating LLMs into their operational workflows — for incident response, infrastructure review, cost analysis, and more. However, there is no standard way to give agents safe, structured access to platform tools.

MCP solves this by defining a protocol for tool exposure. This project demonstrates how to build an MCP server tailored to platform operations, enabling AI agents to act as intelligent platform assistants.

---

## Exposed Tools

### Kubernetes
- List namespaces, pods, deployments, services
- Get pod logs and events
- Check resource health and restart counts
- Scale deployments

### Terraform
- Show current plan output
- List workspace state resources
- Detect drift between state and actual infrastructure

### Prometheus
- Query metrics by PromQL expression
- List active alerts and their severity
- Fetch resource utilization trends (CPU, memory, network)

---

## Tech Stack

| Layer | Technology |
|---|---|
| Protocol | Model Context Protocol (MCP) |
| Language | Python 3.11+ |
| K8s Client | `kubernetes` (official Python client) |
| Terraform | `python-terraform` / subprocess |
| Metrics | Prometheus HTTP API |
| Agent Compatibility | Claude, LangGraph, any MCP client |
| Transport | stdio / HTTP SSE |

---

## Architecture

```
MCP Client (LLM Agent)
        │
        ▼
platform-ops-mcp-server
        ├── k8s_tools.py       → Kubernetes operations
        ├── terraform_tools.py → Terraform state & plan
        └── prometheus_tools.py→ Metrics & alerting queries
```

---

## Project Status

> 🚧 In active development — portfolio project showcasing platform engineering + MCP server design.

---

## Roadmap

- [ ] MCP server scaffold (stdio transport)
- [ ] Kubernetes tool implementations
- [ ] Terraform tool implementations
- [ ] Prometheus tool implementations
- [ ] HTTP SSE transport support
- [ ] Tool input validation and safe-mode guardrails
- [ ] Integration with `iac-audit-agent`
- [ ] Docker packaging
- [ ] Example agent walkthrough (incident triage demo)

---

## Related Projects

- [`iac-audit-agent`](https://github.com/skbasetti/iac-audit-agent) — LangGraph agent that uses this MCP server to audit IaC governance

---

## Author

**skbasetti** — Platform Engineering | AI Agents | Cloud Infrastructure
