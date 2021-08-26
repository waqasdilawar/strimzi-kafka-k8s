# 01-  deploy [Prometheus Community Operator](https://artifacthub.io/packages/helm/prometheus-community/kube-prometheus-stack)

**Prerequisites**
* Kubernetes 1.16+
* Helm 3+

`helm repo add prometheus-community https://prometheus-community.github.io/helm-charts`

`helm repo add stable https://charts.helm.sh/stable`

`helm repo update`

**[Install Chart](https://artifacthub.io/packages/helm/prometheus-community/kube-prometheus-stack#install-chart)**
# Helm

`helm install [RELEASE_NAME] prometheus-community/kube-prometheus-stack`


**Grafana admin password change**

`kubectl exec -it my-prometheus-grafana-66894cd656-pnq7f -c grafana -- sh`

`grafana-cli admin reset-admin-password new_passwd`

# 02-  deploy Strimzi kafka with metrics

`kubectl create -f 'https://strimzi.io/install/latest?namespace=default'`

`kubectl apply -f kafka/01-strimzi-kafka-with-metrics.yaml`

Quick start example could also be found here at [Strimzi website](https://strimzi.io/quickstarts/).

# 03-  deploy PodMonitor to scrap kafka metrics into Prometheus
**release: my-prometheus** it should be [RELEASE_NAME] of the release name from **#01**

`kubectl apply -f kafka/02-prometheus-strimzi-podmonitor.yaml`

# 04-  Add Grafana different dashboards from configuration available at [Strimzi repository](https://github.com/strimzi/strimzi-kafka-operator/tree/main/examples/metrics/grafana-dashboards)
