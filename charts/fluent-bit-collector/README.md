# fluent-bit-collector

![Version: 0.3.0](https://img.shields.io/badge/Version-0.3.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 2.1.6](https://img.shields.io/badge/AppVersion-2.1.6-informational?style=flat-square)

Helm chart for Fluent Bit running as a collector DaemonSet.

**Homepage:** <https://fluentbit.io/>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| stevehipwell | <steve.hipwell@gmail.com> | <https://github.com/stevehipwell> |

## Source Code

* <https://github.com/fluent/fluent-bit/>
* <https://github.com/stevehipwell/helm-charts/>

## Installing the Chart

To install the chart using the recommended OCI method you can use the following command.

```shell
helm upgrade --install fluent-bit-collector oci://ghcr.io/stevehipwell/helm-charts/fluent-bit-collector --version 0.3.0
```

Alternativly you can use the legacy non-OCI method via the following commands.

```shell
helm repo add stevehipwell https://stevehipwell.github.io/helm-charts/
helm upgrade --install fluent-bit-collector stevehipwell/fluent-bit-collector --version 0.3.0
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | Affinity settings for pod scheduling. |
| args | list | `[]` | Args for the default container. |
| commonLabels | object | `{}` | Labels to add to all chart resources. |
| config.customParsers | string | See _values.yaml_ | Custom parsers to configure. |
| config.extraFiles | object | `{}` | Extra files to mount to /fluent-bit/etc |
| config.hostVolumes | list | See _values.yaml_ | Host volumes to read-only mount to the default container. |
| config.luaScripts | object | `{}` | Lua scripts to configure, these will be created at /fluent-bit/scripts and need to be referenced by an absolute path. |
| config.pipeline | string | See _values.yaml_ | Fluent Bit pipeline configuration. |
| config.service | object | See _values.yaml_ | Fluent Bit service configuration. |
| config.storage | bool | `false` | If `true`, writeable host filesystem storage will be enabled. |
| dashboards.enabled | bool | `false` | If `true`, install the _Grafana_ dashboards provided by the chart. |
| env | list | `[]` | Environment variables for the default container. |
| extraVolumeMounts | list | `[]` | Extra volume mounts for the default container. |
| extraVolumes | list | `[]` | Extra volumes for the pod. |
| fullnameOverride | string | `nil` | Override the full name of the chart. |
| hotReload.enabled | bool | `false` | If `true`, enable [hot-reload](https://docs.fluentbit.io/manual/administration/hot-reload) via a sidecar container. |
| hotReload.image.digest | string | `nil` | Optional image digest for the hot-reload sidecar container. |
| hotReload.image.pullPolicy | string | `"IfNotPresent"` | Image pull policy for the hot-reload sidecar container. |
| hotReload.image.repository | string | `"ghcr.io/jimmidyson/configmap-reload"` | Image repository for the hot-reload sidecar container. |
| hotReload.image.tag | string | `"v0.11.1"` | Image tag for the hot-reload sidecar container. |
| hotReload.resources | object | `{}` | Resources for the hot-reload sidecar container. |
| image.digest | string | `nil` | Optional image digest for the default container. |
| image.pullPolicy | string | `"IfNotPresent"` | Image pull policy for the default container. |
| image.repository | string | `"cr.fluentbit.io/fluent/fluent-bit"` | Image repository for the default container. |
| image.tag | string | `nil` | Image tag for the default container, this will default to `.Chart.AppVersion` if not set and will be omitted if set to `-`. |
| imagePullSecrets | list | `[]` | Image pull secrets. |
| livenessProbe | object | See _values.yaml_ | Liveness probe configuration for the default container. |
| minReadySeconds | string | `nil` | Min ready seconds for the `DaemonSet`. |
| nameOverride | string | `nil` | Override the name of the chart. |
| nodeSelector | object | `{}` | Node labels to match for pod scheduling. |
| podAnnotations | object | `{}` | Annotations to add to the pod. |
| podLabels | object | `{}` | Labels to add to the pod. |
| podSecurityContext | object | See _values.yaml_ | Security context for the pod. |
| priorityClassName | string | `nil` | Priority class name for the pod. |
| readinessProbe | object | See _values.yaml_ | Readiness probe configuration for the default container. |
| resources | object | `{}` | Resources for the default container. |
| securityContext | object | See _values.yaml_ | Security context for the default container. |
| service.additionalPorts | list | See _values.yaml_ | Additional ports to expose. |
| service.annotations | object | `{}` | Service annotations. |
| service.enabled | bool | `false` | If `true`, create an internal local traffic service. |
| service.httpPort | int | `2020` | Fluent Bit HTTP port used for status and metrics. |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account. |
| serviceAccount.automountToken | bool | `true` | If `true`, mount the `ServiceAccount` token. |
| serviceAccount.create | bool | `true` | If `true`, create a new `ServiceAccount`. |
| serviceAccount.labels | object | `{}` | Labels to add to the service account. |
| serviceAccount.name | string | `nil` | If this is set and `serviceAccount.create` is `true` this will be used for the created `ServiceAccount` name, if set and `serviceAccount.create` is `false` then this will define an existing `ServiceAccount` to use. |
| serviceMonitor.additionalEndpoints | list | `[]` | Additional `ServiceMonitor`endpoints, these are needed for metrics output plugins. |
| serviceMonitor.additionalLabels | object | `{}` | Additional labels for the `ServiceMonitor`. |
| serviceMonitor.enabled | bool | `false` | If `true`, create a `ServiceMonitor` (or `PodMonitor` if the Service isn't enabled) resource to support the _Prometheus Operator_. |
| serviceMonitor.endpointConfig | object | `{}` | Additional endpoint configuration for the default `ServiceMonitor` endpoint. |
| terminationGracePeriodSeconds | string | `nil` | Termination grace period for the pod in seconds. |
| tolerations | list | `[]` | Node taints which will be tolerated for pod scheduling. |
| updateStrategy | object | `{}` | Update strategy for the `DaemonSet`. |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs/releases/v1.11.0)
