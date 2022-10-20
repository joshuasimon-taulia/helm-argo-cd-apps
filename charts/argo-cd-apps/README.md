# argo-cd-apps

[argo-cd-apps](https://github.com/argoproj) - using argo-cd

## TL;DR;

```bash
$ helm repo add joshuasimon https://jenkins-x-charts.github.io/repo
$ helm repo update
$ helm search repo joshuasimon/helm-argo-cd-apps --version=0.1.0
$ helm upgrade -i argo-cd-apps joshuasimon/helm-argo-cd-apps -n argocd --create-namespace --version=0.1.0
```

## Introduction

This chart deploys argo-cd-apps k8s custom resources on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes v1.21+
- install the [argo-cd](https://github.com/argoproj/argo-helm/tree/main/charts/argo-cd) chart

## Installing the Chart

To install/upgrade the chart with the release name `argo-cd-apps`:

```bash
$ helm upgrade -i argo-cd-apps joshuasimon/helm-argo-cd-apps -n argocd --create-namespace --version=0.1.0
```

The command deploys argo-cd-apps k8s custom resources on the Kubernetes cluster in the default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall the `argo-cd-apps`:

```bash
$ helm uninstall argo-cd-apps -n argocd
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters of the `helm-argo-cd-apps` chart and their default values.

|                 Parameter                 |                                            Description                                            |                                             Default                                              |
|-------------------------------------------|---------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| extraConfig                               | additional applicationset configuration                                                           | <code>{}</code>                                                                                  |
| syncPolicy                                | [argo-cd application sync policy](https://argo-cd.readthedocs.io/en/stable/user-guide/auto_sync/) | <code>{"automated":{"prune":true,"selfHeal":true},"syncOptions":["CreateNamespace=true"]}</code> |
| jxRequirements.ingress.annotations        | shared ingress annotations on all services                                                        | <code>{}</code>                                                                                  |
| jxRequirements.ingress.apiVersion         |                                                                                                   | <code>"networking.k8s.io/v1"</code>                                                              |
| jxRequirements.ingress.domain             | the domain for hosts                                                                              | <code>""</code>                                                                                  |
| jxRequirements.ingress.externalDNS        |                                                                                                   | <code>false</code>                                                                               |
| jxRequirements.ingress.namespaceSubDomain |                                                                                                   | <code>-jx.</code>                                                                                |
| jxRequirements.ingress.serviceType        |                                                                                                   | <code>""</code>                                                                                  |
| jxRequirements.ingress.tls.email          |                                                                                                   | <code>""</code>                                                                                  |
| jxRequirements.ingress.tls.enabled        |                                                                                                   | <code>false</code>                                                                               |
| jxRequirements.ingress.tls.production     |                                                                                                   | <code>false</code>                                                                               |
| jxRequirements.ingress.tls.secretName     |                                                                                                   | <code>""</code>                                                                                  |


Specify each parameter using the `--set key=value[,key=value]` argument to `helm upgrade -i`. For example:

```bash
$ helm upgrade -i argo-cd-apps joshuasimon/helm-argo-cd-apps -n argocd --create-namespace --version=0.1.0 --set syncPolicy={"automated":{"prune":true,"selfHeal":true},"syncOptions":["CreateNamespace=true"]}
```

Alternatively, a YAML file that specifies the values for the parameters can be provided while
installing the chart. For example:

```bash
$ helm upgrade -i argo-cd-apps joshuasimon/helm-argo-cd-apps -n argocd --create-namespace --version=0.1.0 --values values.yaml
```
