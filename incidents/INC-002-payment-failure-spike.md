
# INC-002 — Payment Processing Failure Spike

## Incident classification
Simulated banking application incident

## Environment
- Windows 11 / Ubuntu WSL2
- Docker Desktop Kubernetes
- Namespace: banking-lab
- Elasticsearch and Kibana: 9.2.3
- Elastic Agent: 9.2.3

## Summary
A simulated increase in payment-processing failures
was generated to validate centralized logging,
dashboard visualization, and automated alert detection.

## Detection
Kibana Security detection rule:
Banking — High Payment Failure Count

Rule threshold:
More than 20 matching failure events within 1 minute.

## Observed evidence
- Payment failures appeared in Kibana Discover.
- Failure percentage reached 76.06% in the
  selected dashboard time window.
- Failure count peaked at approximately
  60 events per minute.
- Kibana generated a Medium-severity alert.
- The alert was manually moved to Closed.

## Root cause
An intentionally deployed Kubernetes Job,
payment-incident-simulator, generated
100 simulated failure events.

No real payment transactions were affected.

## Recovery
The incident generator completed its workload
and stopped producing failure events.

## Verification
- Kubernetes application health: OK
- Error rate below alert threshold: OK
- Security alert workflow status: Closed

## Lessons learned
- Centralized logs simplify investigation.
- Dashboards expose abnormal failure patterns.
- Alert rules can automate incident detection.
- Alert closure is separate from service recovery.

## Potential improvements
- Add Kubernetes metadata enrichment.
- Configure external notifications.
- Automate health-check evidence collection.
- Improve log parsing into structured fields.
