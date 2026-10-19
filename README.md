# Kubernetes, Ansible & Elastic Stack — Banking Operations Home Lab

## Overview

A personal hands-on infrastructure and application operations project demonstrating Kubernetes administration, Ansible automation, centralized logging, monitoring, and incident troubleshooting.

The lab simulates an enterprise banking application environment and focuses on operational reliability, troubleshooting, and infrastructure automation.

**Environment:** Windows 11, Ubuntu WSL2, Docker Desktop, Kubernetes, Ansible, Elasticsearch, Kibana, and Elastic Agent.

## Architecture

The environment includes:

- **Kubernetes:** Hosts simulated banking application workloads.
- **Ansible:** Provides automated application health checks and controlled recovery.
- **Elasticsearch:** Stores and indexes application logs.
- **Elastic Agent:** Collects Kubernetes container logs.
- **Kibana:** Provides log investigation, dashboards, and alerting.

## Kubernetes Workloads

| Application | Purpose |
|---|---|
| banking-web | NGINX application running two replicas |
| banking-payment-worker | Simulated payment processing worker |
| banking-readiness-demo | Application readiness probe exercises |
| banking-log-generator | Generates simulated successful and failed payment events |
| payment-incident-simulator | Generates a temporary payment failure spike |

## Ansible Automation

Implemented operational automation including:

- Kubernetes Deployment health validation.
- Expected versus available replica verification.
- Controlled replica recovery with explicit authorization.
- Inventory configuration and reusable Ansible roles.
- Read-only infrastructure validation and idempotency checks.

## Elastic Stack and Observability

Deployed Elasticsearch and Kibana using Elastic Cloud on Kubernetes (ECK).

Configured Elastic Agent to collect container logs from Kubernetes banking applications.

Implemented:

- Centralized application log collection.
- Log filtering and analysis using Kibana Discover.
- ES|QL queries for transaction outcomes and failure trends.
- Kibana dashboards for payment-processing success and failure rates.
- A Security detection rule for elevated payment-processing failures.

## Incident Simulations

### INC-001 — Kubernetes Deployment Recovery

Simulated an application outage caused by an incorrect replica configuration.

Used Ansible to detect the configuration mismatch and restore the expected replica count.

### INC-002 — Payment Processing Failure Spike

Simulated an increased payment-failure rate using a Kubernetes Job.

Investigated the resulting logs using Kibana Discover and dashboards.

Configured an automated detection rule and validated alert generation and manual closure.

### Additional Kubernetes Troubleshooting

Practiced identifying and resolving:

- ImagePullBackOff
- CrashLoopBackOff
- Readiness probe failures

### Kibana Application Operations Dashboard

This dashboard demonstrates centralized Kubernetes logging,
payment-processing monitoring, and incident investigation
using Elasticsearch, Elastic Agent, and Kibana.
<img width="1908" height="927" alt="Dashboard" src="https://github.com/user-attachments/assets/b18e18c5-ed56-4016-a8cf-cb78e4bed5f7" />

## Repository Structure

```text
devops-elastic-lab/
├── ansible/       # Playbooks, inventories, variables, roles
├── kubernetes/    # Application and incident manifests
├── elastic/       # Elastic Stack and Agent manifests
├── incidents/     # Incident reports and investigations
├── .gitignore
└── README.md
```

## Security Considerations

- No production banking systems or real customer data are used.
- All payment transactions and incidents are simulated.
- Credentials, private keys, Kubernetes kubeconfig files, and local backups are excluded from version control.
- Recovery automation requires explicit authorization before modifying Deployment replica counts.
- The environment is intended for local learning and demonstration, not production deployment.

## Future Improvements

- Structured log parsing and Kubernetes metadata enrichment.
- Enhanced Kibana dashboards and alerting.
- Automated operational evidence collection.
- Additional Ansible roles and deployment automation.
- Expanded Kubernetes incident simulations.
- Infrastructure provisioning using Terraform and cloud integration.

## Project Scope

This project is an independently developed learning environment designed to strengthen practical skills in Application Operations, DevOps, Cloud Engineering, and Site Reliability Engineering.

It is not affiliated with a financial institution and does not represent a production banking infrastructure.
