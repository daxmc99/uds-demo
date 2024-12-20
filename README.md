# UDS Overview

# High-level overview

UDS is a packaging framework that allows end users to meet stringent requirements for obtaining an Authority to Operate (ATO). 

It leverages several open standards like OSCAL to enable this support while blending in other OSS software from Defense Unicorns like Zarf, Pepr and Lula. 

UDS has several core packages it bundles together to enable this goal

**Core Applications**

- [Authservice](https://github.com/istio-ecosystem/authservice) - Authorization
- [Grafana](https://grafana.com/oss/grafana/) - Monitoring
- [Istio](https://istio.io/) - Service Mesh
- [KeyCloak](https://www.keycloak.org/) - Identity & Access Management
- [Loki](https://grafana.com/oss/loki/) - Log Aggregation
- [Metrics Server](https://github.com/kubernetes-sigs/metrics-server) - Metrics
- [Neuvector](https://open-docs.neuvector.com/) - Container Security
- [Pepr](https://pepr.dev/) - UDS policy engine & operator
- [Prometheus Stack](https://github.com/prometheus-operator/kube-prometheus) - Monitoring
- [Vector](https://vector.dev/) - Log Aggregation
- [Velero](https://velero.io/) - Backup & Restore

## UDS bundles

A core concept in UDS are **bundles**. Bundles allow replicable configuration of UDS deployments. A UDS bundle is very similar to Helm but more opinionated and specific. 

![image.png](./image.png)

Firstly, UDS bundles require Zarf. Zarf handles the pulling and packaging of images into a large OCI artifact. 

> OCI artifacts are set of standards used by the Open Container Initative to store arbitrary files
>

## Key differences

- UDS is more opinionated than Helm and the UDS-core specifies a set of applications
- UDS leverages an operator with CRDs to simiply the deployment of applications with UDS
  - For example, Istio Virtual services can be configured by
  [Package CR](https://uds.defenseunicorns.com/reference/configuration/custom-resources/packages-v1alpha1-cr/)
  - This explicitly HAS LESS FLEXIBILITY than the native Istio virtual service options
  - ie, no support for [HTTPFaultInjection](https://istio.io/latest/docs/reference/config/networking/virtual-service/#HTTPFaultInjection)
- 

## Takeaways

- UDS follows the standard Kubernetes maturity model where abstractions are added to simplify
 desired patterns. 
- 