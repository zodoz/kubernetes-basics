# kubernetes-basics
Kubernetes presentation on the basics plus hands on

## Prereqs

1. Create google cloud account
2. Create gcloud cluster `gcloud container --project [PROJECT ID] clusters create "kubernetes-basics" --zone "us-west1-a" --machine-type "n1-standard-1" --image-type "GCI" --disk-size "100" --scopes "https://www.googleapis.com/auth/compute","https://www.googleapis.com/auth/devstorage.read_only","https://www.googleapis.com/auth/logging.write","https://www.googleapis.com/auth/servicecontrol","https://www.googleapis.com/auth/service.management.readonly","https://www.googleapis.com/auth/trace.append" --num-nodes "3" --network "default" --enable-cloud-logging --enable-cloud-monitoring --enable-autoupgrade`
3. login `gcloud auth application-default login`
...
4. Destroy cluster `gcloud container clusters delete kubernetes-basics --zone "us-west1-a"`

## demos


### Deployment

`kubectl create -f services/01-hello-k8s/deployment.yaml`

`kubectl get pods` - yay, they're running, but how do I know its correct?

    kubectl exec _____ -it -- bash
    apt-get update
    apt-get install curl
    curl localhost

### Service

This is how you make it available:

`kubectl expose hello-k8s-deployment --type=LoadBalancer --name=hello-k8s-service`

How do I get the IP?

    > kubectl get service
    NAME               CLUSTER-IP      EXTERNAL-IP      PORT(S)        AGE
    hello-k8s-expose   10.31.123.456   35.123.456.789   80:30678/TCP   53s
    kubernetes         10.31.123.1     <none>           443/TCP        38m

### Sidecar pattern

Create service which polls github every 5 seconds and updates local FS

### Inter-service connection and communication

create service which responds either "I'm lonely" or "I see xxx". Spin up twice pointing to each other. Show first one before connection.

### Detecting OOM

Note to self: create process which just eats memory. Deploy as 100M limit to demonstrate OOM on pod.

