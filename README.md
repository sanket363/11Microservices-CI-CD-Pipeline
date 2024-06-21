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

### Deploy Application with ArgoCD

1. **Install ArgoCD:**

   You can install ArgoCD on your Kubernetes cluster by following the instructions provided in the [EKS Workshop](https://archive.eksworkshop.com/intermediate/290_argocd/install/) documentation.

2. **Set Your GitHub Repository as a Source:**

   After installing ArgoCD, you need to set up your GitHub repository as a source for your application deployment. This typically involves configuring the connection to your repository and defining the source for your ArgoCD application. The specific steps will depend on your setup and requirements.

3. **Create an ArgoCD Application:**

   - `name`: Set the name for your application.
   - `destination`: Define the destination where your application should be deployed.
   - `project`: Specify the project the application belongs to.
   - `source`: Set the source of your application, including the GitHub repository URL, revision, and the path to the application within the repository.
   - `syncPolicy`: Configure the sync policy, including automatic syncing, pruning, and self-healing.

4. **Access your Application**
   - To Access the app make sure port 30007 is open in your security group and then open a new tab paste your NodeIP:30007, your app should be running.

**Phase 7: Cleanup**

1. **Cleanup AWS EC2 Instances:**
   - Terminate AWS EC2 instances that are no longer needed.
