# PhenoMeNal Helm Charts

This repo contains the source and packaged Helm charts used by PhenoMeNal for the deployment of Jupyter, PhenoMeNal Portal and for the continous delivery of data-related tests for PhenoMeNal containers. The Galaxy Helm Chart and source produced by PhenoMeNal is available at a Galaxy Project owned [repository](https://github.com/galaxyproject/galaxy-kubernetes).

To use this repo with your local Helm installation, to deploy to your Kubernetes clusters or local minikube, you need to first add the Helm repo:

```bash
$ helm repo add phenomenal https://phnmnl.github.io/helm-charts/
```

## PhenoMeNal Portal Chart

### On Minikube

For deploying on Minikube, with automatic persistence:

```
$ helm install phenomenal/portal
```

Currently the PhenoMeNal Portal relies on the EBI TSI Portal, and as such for deployments to work, the incoming URL from where PhenoMeNal Portal is run needs to be whitelisted at EBI TSI Portal.

