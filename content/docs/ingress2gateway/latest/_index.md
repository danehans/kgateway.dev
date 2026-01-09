---
title: Ingress2Gateway Latest
weight: 460
description: Translate Ingress to Gateway API and kgateway resources
---

Welcome to the Ingress2Gateway docs for **latest**.

THe [ingress2gateway](https://github.com/kgateway-dev/ingress2gateway) tool is a fork of the [Kubernetes ingress2gateway](https://github.com/kubernetes-sigs/ingress2gateway)
project with the following additional features:

- **Ingress NGINX Annotations:** Supports Converts NGINX-specific Ingress annotations, e.g. session affinity, authentication, rate limiting, CORS, etc..
- **Kgateway CRD Output:** Generates Gateway API resources and kgateway specific resources, e.g. TrafficPolicy, BackendConfigPolicy, etc..

We [plan](https://github.com/kgateway-dev/ingress2gateway/issues/54) to merge these features upstream.

Use these guides to begin migrating to kgateway from [Ingress NGINX](https://github.com/kubernetes/ingress-nginx).

{{< cards >}}
  {{< card link="get-started" title="Get started" >}}
  {{< card link="emitters" title="Emitters" >}}
  {{< card link="providers" title="Providers" >}}
  {{< card link="reference" title="Reference" >}}
  {{< card link="contributing" title="Contributing" >}}
{{< /cards >}}
