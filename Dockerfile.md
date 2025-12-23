### HEALTHCHECK in Dockerfile
Dockerfile HEALTHCHECK is not required when you use Kubernetes.
 Kubernetes has a better, more powerful health-check system.

### Real-world production rule
Docker HEALTHCHECK = optional   ❌ Don’t rely on Docker HEALTHCHECK in Kubernetes

Kubernetes probes = mandatory.        [ liveness + readiness + startup ]

### VOLUME
when you use Kubernetes, you usually do not need VOLUME in your Dockerfile.







 
