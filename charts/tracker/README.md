# Tracker

Tracker is the primary API service in the [deps.cloud](https://deps.cloud) ecosystem.
It manages the dependency graph stored in various relational databases.

## Introduction

This chart bootstraps a tracker deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.16+
- Helm 3.0+

## Installing the Chart

To install the chart with the release name `tracker`:

```bash
$ helm repo add depscloud https://depscloud.github.io/deploy/charts
$ helm install tracker depscloud/tracker
```

The command deploys the tracker on the Kubernetes cluster in the default configuration.
The [Parameters](#parameters) section lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm search repo --versions`

## Uninstalling the Chart

To uninstall/delete the `tracker` deployment:

```bash
$ helm delete tracker
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Parameters

The following table lists the configurable parameters of the tracker chart.

| Parameter                                | Description                                                             | Default                       |
|------------------------------------------|-------------------------------------------------------------------------|-------------------------------|
| `global.labels`                          | Labels applied to all deps.cloud resources                              | `{}`                          |
| `global.service.topology`                | Provides control over the network topology for all deps.cloud resources | `[]`                          |
| `global.metrics.serviceMonitor.enabled`  | Enables Prometheus service monitors for all deps.cloud resources        | `false`                       |
| `global.metrics.serviceMonitor.interval` | The default interval metrics should be pulled on                        | `10s`                         |
| `replicaCount`                           | The number of instances to run                                          | `1`                           |
| `image.repository`                       | The address of the registry hosting the image                           | `depscloud/tracker`           |
| `image.pullPolicy`                       | The pull policy for the image                                           | `IfNotPresent`                |
| `image.tag`                              | The version of the image                                                | `.Chart.AppVersion`           |
| `imagePullSecrets`                       | Registry secret names                                                   | `[]`                          |
| `nameOverride`                           | String to partially override the full name template                     | `""`                          |
| `fullnameOverride`                       | String to completely override the full name                             | `""`                          |
| `serviceAccount.create`                  | Whether or not a service account should be created                      | `true`                        |
| `serviceAccount.automountToken`          | Should we mount the service account token                               | `false`                       |
| `serviceAccount.name`                    | The name of the service account                                         | `""`                          |
| `podSecurityContext`                     | Provide any pod security context attributes                             | `{}`                          |
| `securityContext`                        | Provide any security context attributes                                 | `{}`                          |
| `service.type`                           | The type of service used to address the tracker                         | `Headless`                    |
| `service.topology`                       | Provides control over the network topology                              | `{}`                          |
| `resources`                              | Any resource constraints to place on the container                      | `{}`                          |
| `nodeSelector`                           | Target the deployment to a certain class of nodes                       | `{}`                          |
| `tolerations`                            | Identify any taints the process can tolerate                            | `[]`                          |
| `affinity`                               | Set up an an affinity based on attributes                               | `{}`                          |
| `tls.secretName`                         | The name of the secret container certificate data for mutual TLS        | `""`                          |
| `storage.address`                        | The address of the storage service (mysql, sqlite3)                     | `file::memory:?cache=shared`  |
| `storage.driver`                         | The driver to use for the storage service                               | `sqlite3`                     |
| `storage.readOnlyAddress`                | The read only address to the storage service                            | `""`                          |
| `storage.statements`                     | Optionally override any statements being used                           | `""`                          |
| `labels`                                 | Labels applied to the tracker resources                                 | `{}`                          |
| `metrics.serviceMonitor.enabled`         | Enables Prometheus service monitors for tracker                         | `false`                       |
| `metrics.serviceMonitor.interval`        | The default interval metrics should be pulled on                        | `10s`                         |
