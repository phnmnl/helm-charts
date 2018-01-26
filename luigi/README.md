![Logo](luigi_logo.png)

# Introduction
This chart bootstraps a [Luigi 2.6.0](https://github.com/spotify/luigi) deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

Luigi is a Python (2.7, 3.3, 3.4, 3.5) package that helps you build complex pipelines of batch jobs. It handles dependency resolution, workflow management, visualization, handling failures, command line integration, and much more. It is built on top of `python:alpine` and its only aim is to run the [Luigi central scheduler](http://luigi.readthedocs.io/en/stable/central_scheduler.html).

## Prerequisites Details
- Kubernetes 1.4+
- PV provisioner support in the underlying infrastructure

## Installing the Chart
You can install the Chart via Helm CLI:

```console
$ helm install --name luigi --set ingress.host=your.domain.name luigi
```

## Clean-up
-----------

In order to remove the Luigi release, you can execute the following commands:

```console
$ helm list
$ helm delete --purge <release-name>
```

## Helm chart settings
----------------------

The following tables lists the configurable parameters of the chart and their default values.

| Parameter                | Description                               | Default                                                |
|--------------------------|-------------------------------------------|--------------------------------------------------------|
| `image.repository`       | Luigi image                               | `container-registry.phenomenal-h2020.eu/phnmnl/luigi`  |
| `image.tag`              | Image's tag                               | `v2.6.0_cv0.1.5`                                       |
| `image.pullPolicy`       | Image pull policy                         | `IfNotPresent`                                         |
| `ingress.enabled`        | Assuming use of ingress controllers       | `true`                                                 |                                                 
| `ingress.host`           | Luigi host to create application URLs     | `nil`                                                  |
| `ingress.servicePort`    | Kubernetes Ingress backend (service:port) | `8082`                                                 |
| `replicaCount`           | Deplyoment replication factor             | `1`                                                    |
| `resources`              | CPU/Memory resource requests/limits       | Memory: `1Gi`, CPU: `200m`                             |
| `service.externalPort`   | Kubernetes Service `targetPort`           | `8082`                                                 |
| `service.internalPort`   | Kubernetes Service `port`                 | `8082`                                                 |
| `service.name`           | Kubernetes Service `name`                 | `name`                                                 |
| `service.loadBalancerIP` | `LoadBalancer` IP if used                 | `nil`                                                  |
| `service.nodePortExposed`| `NodePort` value if used (only for test)  | `nil`                                                  |
| `service.type`           | Kubernetes Service type                   | `ClusterIP`                                            |

To the best of our knowledge, the use of the `NodePort` option as service type should be limited only for testing (e.g. with minikube) due to security concerns.  

Other parameters are also changeable. Please consult all available parameters in the `values.yaml` file.


## Tool Authors

- Spotify
