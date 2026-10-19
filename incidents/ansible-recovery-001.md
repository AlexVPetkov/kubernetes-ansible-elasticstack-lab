
# Incident Report: INC-001

## Application
banking-readiness-demo

## Environment
Local Docker Desktop Kubernetes cluster
Namespace: banking-lab

## Incident
The application's desired replica count was
incorrectly changed from 1 to 0.

## Impact
The application had no running Pods and
was unavailable through its Kubernetes Service.

## Detection
The Ansible health-check playbook detected a
mismatch between expected and actual replicas.

## Investigation
Reviewed the Deployment configuration and
confirmed that the desired replicas were set to 0.

## Recovery
Executed the controlled Ansible recovery playbook
with explicit authorization to restore 1 replica.

## Verification
- Deployment returned to 1/1 available
- Application Pod became ready
- Ansible health-check playbook passed

## Root Cause
Incorrect Deployment replica configuration.

## Prevention
Introduce configuration reviews, GitOps controls,
and automated health checks.
