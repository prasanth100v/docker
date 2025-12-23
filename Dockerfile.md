### HEALTHCHECK in Dockerfile
Dockerfile HEALTHCHECK is not required when you use Kubernetes.
 Kubernetes has a better, more powerful health-check system.

### Real-world production rule
Docker HEALTHCHECK = optional
Kubernetes probes = mandatory        [ liveness + readiness (+ startup if needed) in Kubernetes ]









 
