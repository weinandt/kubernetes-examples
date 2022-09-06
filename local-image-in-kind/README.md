# Build docker image and load into kind kubernetes cluster

## Installation Pre-Reqs
1. Docker
2. kind
3. kubectl (may come with kind)

## Instructions
1. Build image locally: `docker build -t nick-express:unique-id .`
    - Container listens to requests on port 3000.
2. Create a new kubernetes cluster with kind: `kind create cluster`
3. 