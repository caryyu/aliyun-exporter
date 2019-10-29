# Aliyun Exporter
It's a Prometheus exporter that collects metrics from the [CloudMonitor API](https://partners-intl.aliyun.com/help/doc-detail/51939.htm) of Alibaba Cloud. It can help you:

* integrate CloudMonitor to your Monitoring System.
* leverage the power of PromQL, Alertmanager and Grafana(see [Screenshots](#)).
* analyze metrics however you want.
* save money. Api invocation is far cheaper than other services provided by CloudMonitor.

This project also provides an out-of-box solution for full-stack monitoring of Alibaba Cloud, including dashboards, alerting and diagnosing.

# CRD Installation
Please make sure that following CRDs have been installed,
```
kubectl apply -f https://raw.githubusercontent.com/coreos/prometheus-operator/master/example/prometheus-operator-crd/servicemonitor.crd.yaml
```
More about CRDs to Prometheus Operator Chart: https://github.com/helm/charts/blob/master/stable/prometheus-operator/README.md

# Configuration
The following table lists the configurable parameters of this chart and their default values.
| Parameter                                    | Description                                                                                  | Default                                              |
| -------------------------------------------- | -------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| `image.repository`                           | Docker image respository                                                                     | `aylei/aliyun-exporter`                              |
| `image.tag`                                  | Docker image tag                                                                             | `0.3.1`                                              |
| `image.pullPolicy`                           | Image pull policy described from Kubernetes                                                  | `IfNotPresent`                                       |
| `image.pullSecrets`                          | Image pull secrets from private image registry                                               | `IfNotPresent`                                       |
| `replicaCount`                               | Number of replica of the Pods for HA                                                         | `1`                                                  |
| `podAnnotations`                             | Additional Pod annotations                                                                   | `{}`                                                 |
| `aliyunAccessId`                             | AliCloud Access Key                                                                          | `None`                                               |
| `aliyunAccessSecret`                         | AliCloud Access Secret                                                                       | `None`                                               |
| `aliyunRegion`                               | AliCloud Region                                                                              | `cn-hangzhou`                                        |
| `service.type`                               | Kubernetes service type                                                                      | `ClusterIP`                                          |
| `service.labels`                             | Kubernetes service labels                                                                    | `[]`                                                 |
| `service.annotations`                        | Kubernetes service additional annotations                                                    | `[]`                                                 |
| `service.selector`                           | Kubernetes service additional selectors                                                      | `[]`                                                 |
| `servicemonitor.labels`                      | Prometheus ServiceMonitor labels for discovering                                             | `prometheus-monitoring: "true"`                      |

Specify each parameter using the --set key=value[,key=value] argument to helm install. For example,
```
helm install --name my-release --set aliyunAccessId=xxxxxx --set aliyunAccessSecret=xxxxxx --set aliyunRegion=cn-shanghai stable/aliyun-exporter
```

# Source Code Repo
https://github.com/aylei/aliyun-exporter