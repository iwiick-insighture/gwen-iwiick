

## How to run Gwen with Tekton
This guide will walk you through the process of running Gwen with Tekton.

### Step 1: Create a Cluster

First, we need to create a Kubernetes cluster. We can do this using the kind command:
```bash
kind create cluster
kubectl cluster-info --context kind-kind
```

### Step 2: Install Tekton
Next, we will install Tekton on our cluster. We can do this by applying the Tekton release YAML file:
* `kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml`

Then, we can watch the pods in the tekton-pipelines namespace to ensure that Tekton is installed correctly:

* `kubectl get pods --namespace tekton-pipelines --watch`

We also need to install the Tekton dashboard:

* `kubectl apply --filename https://storage.googleapis.com/tekton-releases/dashboard/latest/release.yaml`
* `kubectl get pods --namespace tekton-pipelines --watch`

To access the Tekton dashboard, we can use kubectl proxy and port-forward the tekton-dashboard service:

* `kubectl proxy`
* `kubectl --namespace tekton-pipelines port-forward svc/tekton-dashboard 9097:9097`
### Step 3: Install Tekton Git Clone Task
We need to install the Git Clone task from the Tekton catalog:

  `kubectl apply -f https://raw.githubusercontent.com/tektoncd/catalog/main/task/git-clone/0.9/git-clone.yaml`

### Step 4: Install PVC in Cluster
Next, we need to install a Persistent Volume Claim (PVC) in our cluster (for cloning the repo):

  * ` kubectl apply -f  tekton/git-pvc.yaml`

### Step 5: Install Docker Compose Task
  * ` kubectl apply -f  tekton/docker-compose-task.yaml`
### Step 6: Install Docker Compose Pipeline
  * ` kubectl apply -f  tekton/compose-pipeline.yaml`

### Step 7: Execute Pipeline
  * ` kubectl apply -f  tekton/compose-pipeline-run.yaml`

That's it! You have now successfully run Gwen with Tekton.


## All these Manual Steps can be automated using SKYU with much ease.