# Leaf Classification

GCP Deployment using Docker, Kubernetes and enabling CI/CD using Cloud Build

* Create the model and save it in the models folder
* Move to GCP console and clone the repository
* Create a kubernetes cluster by specifying the name of cluster, region, instance type, nodes etc.
* Create deployments.yaml file with docker image and ports of container for deploying the pods
* Create service.yaml file for exposing our application to website by linking the web port with the container port
* To enable CI/CD we can use `Cloudbuild` in which we can write all the steps and set the trigger so once we push a code change new docker image gets build and gets pushed to `GCR` and starts running the pods in the kubernetes cluster using the deployment.yaml and service.yaml files.

## Kubernetes Cheatcodes

Building the container image -

```
gcloud builds submit --tag gcr.io//<image_name> .
```

List the image -

```
gcloud builds list --filter <image_name>
```

Checking logs of built image -

```
gcloud builds log
```

Create Kubernetes Cluster -

```
gcloud container clusters create <cluster_name> --zone "us-west1-b" --machine-type "n1-standard-1" --num-nodes "1" --service-account <service_account_name>
```

Create Kubernetes Deployment -

```
kubectl apply -f deployment.yaml
```

Get details on deployed application -

```
kubectl get deployments
```

Get info of created pods via deployment -

```
kubectl get pods
```

Decribe deployed pod -

```
kubectl describe pod
```

Get pod logs -

```
kubectl logs
```

Create service for deployment -

```
kubectl apply -f service.yaml
```

Get service details -

```
kubectl get services
```

Add nodes to cluster -

```
gcloud container clusters resize <cluster_name> --num-nodes 3 --zone us-west1-b
```

Get details on cluster -

```
gcloud container clusters list
```

Scale pod replicas -

```
kubectl scale deployment <deployment_name> --replicas 2
```

Auto Scale setting in deployment -

```
kubectl autoscale deployment <deployment_name> --max 6 --min 2 --cpu-percent 50
```

Get details on horizontal pod autoscaler -

```
kubectl get hpa
```
