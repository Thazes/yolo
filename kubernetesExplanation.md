# Deployment with K8s on GKE

## 1. Manifest folder

Created a folder for the manifest files and added the following files:
    1. mongodb.yml
    2. backend-configuration.yml
    3. client-configuration.yml

### mongodb.yml

These file contains mongodb stateful set, mongodb persistent volume claim and loadbalancer service for the mongodb

### backend-configuration.yml

These file contains yolobackend deployment where I fetched matagaro12/yolobackend_ip2:v1.0.1 image from docker hub and connected to yolo database then configured the file with yolo_backend loadbalance service

### client-configuration.yml

These file contains client deployment where I fetched matagaro12/yoloclient_ip2:v1.0.3 image from docker hub and then configured the file with client loadbalance service

After creating the files in this folder, I used the cloud shell to provision a cluster and perform the deployent in the following steps:

1.  Create cluster:
    ```
    gcloud container clusters create-auto yolo-cluster --location=us-central1
    ```
2.  Clone my repository:
     I cloned my repo my running 

     ```
     git clone https://github.com/Thazes/yolo.git

     ```
     

3.  Change and directory to the yolo folder then to the manifest folder

    Change directory to the repository and apply the manifests files to deploy and create services
    Create deployments by running commands in the following order:

    Create database configurations
    ```
    kubectl apply -f mongo.yaml
    ```

    Create backend configurations

    ```
    kubectl apply -f backend-configuration
    ```

    Create client configurations
    ```
    kubectl apply -f client-configuration.yaml
    ```

    Get services:

    ```
    kubectl get services
    ```

Then I got the IP from the External_IP column for the client service.
