---
title: "Get started"
weight: 10
---

## ingress2gateway

The [ingress2gateway](https://github.com/kgateway-dev/ingress2gateway) converts Ingress resources into Gateway API and kgateway resources.

## Prerequisites

Before you start the migration, ensure you have the following:

1. **Kgateway Installed**: You need kgateway running in the Kubernetes cluster containing Ingress NGINX-annotated Ingresses.
2. **Kubernetes Cluster Access**: Ensure you have access to your Kubernetes cluster and necessary permissions to manage resources.

### Install ingress2gateway

ingress2gateway is installable on a variety of Linux platforms, macOS and Windows. Find your preferred operating system below.

- [Install ingress2gateway on macOS]({{< relref "install/macos/_index.md" >}})
- [Install ingress2gateway on Linux]({{< relref "install/linux/_index.md" >}})
- [Install ingress2gateway on Windows]({{< relref "install/windows/_index.md" >}})

Refer to the [releases page](https://github.com/kgateway-dev/ingress2gateway/releases) for a list of published versions.

## Example Conversion

Create a basic Ingress manifest that uses the `nginx` IngressClass:

```yaml
cat <<'EOF' > basic-ingress.yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: demo-localhost
spec:
  ingressClassName: nginx
  rules:
  - host: demo.localdev.me
    http:
      paths:
      - backend:
          service:
            name: echo-backend
            port:
              number: 8080
        path: /
        pathType: Prefix
EOF
```

Convert the Ingress manifest:

```bash
ingress2gateway print --providers=ingress-nginx --emitter=kgateway --input-file basic-ingress.yaml > basic-kgateway.yaml
```

Apply the manifest to your cluster.

```bash
kubectl apply -f
```

Check the status of the Gateway and HTTPRoute resources:

```bash
kubectl get gateways
kubectl get httproutes
```

Troubleshoot any issues by reviewing the Gateway and HTTPRoute statuses and kgateway controller logs.

## Common workflows

### Convert a file and write output to a directory

```bash
ingress2gateway print   --providers=ingress-nginx   --emitter=kgateway   --input-file ./ingress.yaml   --output-dir ./out
```

### Convert a folder of YAMLs

```bash
ingress2gateway print   --providers=ingress-nginx   --emitter=kgateway   --input-dir ./manifests   --output-dir ./out
```

### Check tool version

```bash
ingress2gateway version
```

## Next steps

- Review the [ingress-nginx provider](../providers/ingressnginx/) to understand the supported Ingress NGINX annotations.
- Review the [kgateway emitter](../emitters/kgateway/) to understand how providers such as ingress-nginx are mapped to kgateway-specific resources.
- Read the [emitter design](../emitters/) to understand the details of the design of emitters and providers.
