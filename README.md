# Leaf Classification

GCP Deployment using Docker, Kubernetes and enabling CI/CD using Cloud Build

* Create the model and save it in the models folder
* Move to GCP console and create a kubernetes cluster by specifying the name of cluster, region, instance type, nodes etc.
* ```
  gcloud container clusters create project-kube --zone "us-west1-b" --machine-type "n1-standard-1" --num-nodes "1" --service-account <service-account-name>
  ```
