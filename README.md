# What is Helm ?

- Helm is the package manager for Kubernetes.
- Helm helps you to streamline installation and management of kubernetes application.
- Helm uses a packaging format called charts.

# What is Helm Chart?

- A chart is a collection of files that describe a related set of Kubernetes resources.
- Helm Charts are simply Kubernetes YAML manifests combined into a single package that can be advertised to your Kubernetes clusters.
- A single chart might be used to deploy something simple, like a Nginx pod, or something complex, like a full web app stack with HTTP servers, databases.
- Helm Charts help you define, install, and upgrade even the most complex kubernetes application.

### Helm Chart Structure?

- chart.yml : Contains meta information about chart. Example like version number etc.
- values.yml : Contains the values for the template files.
- charts: Contains other dependent charts.
- templates: Where you put the actual manifest you are deploying with the chart. For example you might be deploying an nginx deployment that needs a service, configmap and secrets.

## Helm Commands

```bash
Command <--------------|-----------> Description
--------               |           -------------------------
- Helm install         |            For installing Helm Chrts
- Helm search          |            Search for a chart in repository
- Helm list            |            List all  the deployed releases
- Helm upgrade         |            Upgrade your releases with new version
- Helm delete          |            Delete the release and all deployed resources
```

## Helm Installation

```bash
wget https://get.helm.sh/helm-v3.11.0-rc.2-linux-amd64.tar.gz
tar -zxvf helm-v3.11.0-linux-amd64.tar.gz
cd linux-amd64/
ls
sudo mv ./helm /usr/local/bin/helm
cd /usr/local/bin
helm
helm version
helm search hub wordpress
```

## Helm Install WordPress

```bash
helm repo add my-repo https://charts.bitnami.com/bitnami
helm install my-release my-repo/wordpress
kubectl get pods
kubectl get deployments
kubectl get svc
helm history wordPress
```

## Helm Install Prometheus

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install prometheus prometheus-community/prometheus
kubectl get pods
kubectl get all
kubectl get svc
kubectl expose service prometheus-server --type=NodePort --target-port=9090 --name=prometheus-server-ext
kubectl get svc
minikube service prometheus-server-ext
minikube service list
```

## Helm Install Grafana

```bash
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
helm install grafana stable/grafana
helm list
kubectl get pods
kubectl get all
kubectl get svc
kubectl expose service grafana --type=NodePort --target-port=3000 --name=grafana-ext
kubectl get svc
minikube service grafana-ext
kubectl get secret --namespace default grafana -o yaml
echo "YWRtaW4=" | openss1 base64 -d ; echo
echo "passwd" | openss1 base64 -d ; echo
minikube service list

```

## Other resources

- [More Installing Helm](https://helm.sh/docs/intro/install/)
- [Find, install and publish Kubernetes packages](https://artifacthub.io/)
