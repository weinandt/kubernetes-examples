# Build docker image and load into kind kubernetes cluster

## Installation Pre-Reqs
1. Docker
2. kind
3. kubectl (may come with kind)

## Instructions
1. Build image locally: `docker build -t nick-express .`
    - Container listens to requests on port 3000.
1. Create a new kubernetes cluster with kind: `kind create cluster`
1. Load the image into the cluster: `kind load docker-image nick-express`
1. Create the deployment and service in the kubernetes cluster: `kubectl apply -f deployment/deployment.yml`
    - As the image is untagged, it is important that the image pull policy is set to never in the deployment.
        - If the image is set to latest, they pull policy is "Always" by default in kubernetes. We don't want to pull the image as we loaded into the cluster in the previous step.
    -  `kubectl get pods` should show two pods running.
1. Port forward so the service inside the kubernetes cluster can be hit from a browser over localhost: `kubectl port-forward service/example-service 3000:80`
1. Go to http://localhost:3000