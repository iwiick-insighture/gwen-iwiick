My Gwen Project
===============

Document your [Gwen](https://gweninterpreter.org) project here.


## Tekton
* `kind create cluster`
* `kubectl cluster-info --context kind-kind`
* `kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml`
* `kubectl get pods --namespace tekton-pipelines --watch`
* `kubectl apply --filename https://storage.googleapis.com/tekton-releases/dashboard/latest/release.yaml`
* `kubectl get pods --namespace tekton-pipelines --watch`
* kubectl proxy
* kubectl --namespace tekton-pipelines port-forward svc/tekton-dashboard 9097:9097
* Install Tekton Git Clone Task
  `kubectl apply -f https://raw.githubusercontent.com/tektoncd/catalog/main/task/git-clone/0.9/git-clone.yaml`
  * ` kubectl apply -f  tekton/git-pvc.yaml`
  * ` kubectl apply -f  tekton/docker-compose-task.yaml`
  * ` kubectl apply -f  tekton/compose-pipeline.yaml`
  * ` kubectl apply -f  tekton/compose-pipeline-run.yaml`

* install pvc
* pipeline
* then do run

* 