# Microservices Web-Application Deployment using CI-CD

## This project involves the deployment of a web application built with a microservices architecture. It includes 11 distinct microservices:

- adservice
- cartservice
- checkoutservice
- currencyservice
- emailservice
- frontend
- loadgenerator
- paymentservice
- productcatalogservice
- recommendationservice
- shippingservice

The application utilizes a comprehensive set of services to deliver a robust and scalable e-commerce solution. Each microservice focuses on a specific aspect of the application, ensuring modularity and ease of maintenance.

### For SonarQube you can simply use Docker to run by using below command

```bash
docker run -d --name sonar -p 9000:9000 sonarqube:lts-community
```

#### For installation of SonarQube can refer to this [URL](https://docs.sonarsource.com/sonarqube/latest/setup-and-upgrade/install-the-server/introduction/)

### To install helm can refer to this [URL](https://helm.sh/docs/intro/install/)

### For adding Prometheus to this EKS Cluster Can follow below steps (We will be using helm for this)

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```

```bash
helm repo update
```

#### Install Chart

Starting with version 16.0, the Prometheus chart requires Helm 3.7+ in order to install successfully. Please check your helm release before installation.

```bash
helm install [RELEASE_NAME] prometheus-community/prometheus
```

Can Refer this URL for the [documentation](https://artifacthub.io/packages/helm/prometheus-community/prometheus)

### For adding Grafana to this EKS Cluster Can follow below steps (We will be using helm for this)

```bash
helm repo add grafana https://grafana.github.io/helm-charts
```

```bash
helm repo update
```

```bash
kubectl create namespace monitoring
```

```bash
helm install my-grafana grafana/grafana --namespace monitoring
```
