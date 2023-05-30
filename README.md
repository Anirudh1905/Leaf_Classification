# Leaf Classification

GCP Deployment using Docker, Kubernetes and enabling CI/CD using Cloud Build

* Create the model and save it in the models folder
* Move to GCP console and create a kubernetes cluster by specifying the name of cluster, region, instance type, nodes etc.
* ```
  gcloud container clusters create project-kube --zone "us-west1-b" --machine-type "n1-standard-1" --num-nodes "1" --service-account <service-account-name>
  ```
* Create deployments.yaml file for deploying the pods and service.yaml file to make this as a service and exposing our application to website by linking the web port with the container port
* To enable CI/CD we can use cloudbuild in which we can write all the steps and set the trigger so once we push a change new docker image gets build and gets pushed to ECR and starts running the pods using the deployment.yaml and service.yaml.

## Kubernetes Cheatcodes

Building the container image -

```
gcloud builds submit --tag gcr.io//complaintsapi .
```

List the image -

```
gcloud builds list --filter complaints
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
gcloud container clusters resize complaints-gke --num-nodes 3 --zone us-west1-b
```

Get details on cluster -

```
gcloud container clusters list
```

Scale pod replicas -

```
kubectl scale deployment complaints --replicas 2
```

Auto Scale setting in deployment -

```
kubectl autoscale deployment complaints --max 6 --min 2 --cpu-percent 50
```

Get details on horizontal pod autoscaler -

```
kubectl get hpa
```
