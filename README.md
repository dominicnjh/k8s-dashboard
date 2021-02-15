# Description

This repo consists of k8s yaml files required to set up k8s dashboard in your cluster and exposed with ingress.

<br>

# Getting Started

1. Change the `host` field in the `dashboard-ingress.yaml`

2. Apply the files in your cluster

3. Access the kubernetes dashboard ui via the host you have previously configured

4. Select `Token` as the login option

5. You can get the token by running the following command in your cluster:

```shell
kubectl -n kubernetes-dashboard get secret $(kubectl -n kubernetes-dashboard get sa/admin-user -o jsonpath="{.secrets[0].name}") -o go-template="{{.data.token | base64decode}}"
```

<br>

# For On-Prem Users

You are required to change the image field in the `recommended.yaml`.

Below are the docker images required for this setup:

1. `kubernetesui/dashboard:v2.1.0`
2. `kubernetesui/metrics-scraper:v1.0.6`
