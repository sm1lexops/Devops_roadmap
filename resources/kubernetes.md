# Kubernetes

## Getting started with Kubernetes

Name | Comments
:------ |:--------:
[kubernetes.io](https://kubernetes.io) | Official Kubernetes site by Google
[Kubernetes 101](https://medium.com/google-cloud/kubernetes-101-pods-nodes-containers-and-clusters-c1509e409e16) | Great beginner article on Kubernetes fundamental concepts
[Kubernetes Tutorial for Beginners](https://www.youtube.com/watch?v=X48VuDVv0do&ab_channel=TechWorldwithNana) | Full video of 4 hours on Kubernetes (2020)
[Learning Path: Kubernetes](https://developer.ibm.com/series/kubernetes-learning-path/) | From basic to advanced Kubernetes learning series
[Kubernetes 101 - Concepts and Why It Matters](https://www.magalix.com/blog/kubernetes-101-concepts-and-why-it-matters?fbclid=IwAR10FZlZ9Pw5c94tGRlgsCrVZTa1bSV2mbxEP8p4cXZ5T-k4VXF-3OUKkFo) |
[kubernetes-workshop](https://github.com/eon01/kubernetes-workshop) |
[Kubernetes Deployment Tutorial](https://devopscube.com/kubernetes-deployment-tutorial) |
[Katacoda](https://www.katacoda.com/courses/kubernetes) | Learn Kubernetes using Interactive Browser-Based Scenarios


## Kubernetes Deep Dive

Name | Comments
:------ |:--------:
[Kubernetes Networking](https://github.com/nleiva/kubernetes-networking-links) | Kubernetes Networking Resources
[Liveness and Readiness Probes](https://www.openshift.com/blog/liveness-and-readiness-probes) |

## Kubernetes Deep Dive

Name | Comments
:------ |:--------:
[Kubernetes Troubleshooting Visual Guide](https://learnk8s.io/troubleshooting-deployments?fbclid=IwAR2k6ziNfhBe--CKoYP6qh5_lHYM7_kruDjc1EcyrpgyV_tKJzQlwiuA_Jk) |

## Misc

Name | Comments
:------ |:--------:
[Kubernetes CheatSheet](https://cheatsheet.dennyzhang.com/cheatsheet-kubernetes-A4) |
[OperatiorHub.io](https://www.operatorhub.io) | Kubernetes native applications
[YAML templates](https://cheatsheet.dennyzhang.com/kubernetes-yaml-templates) |

## Videos

Name | Comments
:------ |:--------:
[The Illustrated Children's Guide to Kubernetes](https://www.youtube.com/watch?v=4ht22ReBjno) |
[Learn Kubernetes](https://www.youtube.com/playlist?list=PL34sAs7_26wNBRWM6BDhnonoA5FMERax0) | Over 50 Kubernetes videos
[Kubernetes Ingress Explained Completely For Beginners](https://www.youtube.com/watch?v=GhZi4DxaxxE&ab_channel=KodeKloud) | 2019

## Tools & Projects

Name | Comments
:------ |:--------:
[KubeInvaders](https://github.com/lucky-sideburn/KubeInvaders) | "Chaos Engineering Tool for Kubernetes and Openshift"
[Kubesort](https://github.com/AATHITH/kubesort) | "kubesort helps you sort the results from kubectl get in an easy way"
[IngressMonitorController](https://github.com/stakater/IngressMonitorController) | "A Kubernetes controller to watch ingresses and create liveness alerts for your apps/microservices"

## Certificates

Name | Comments
:------ |:--------:
[CKAD-Practice-Questions](https://github.com/bbachi/CKAD-Practice-Questions) | "a consolidated list for CKAD practice questions"
[CKAD Prep Exam Video](https://www.youtube.com/watch?v=TPXwVmvzlV4&ab_channel=TheFrontOpsGuy) | A video of doing a CKAD prep exam (2020)

### CheatSheet

#### Minikube

* Minikube version: `minikube version`
* Start cluster: `minikube start`
* Delete cluster: `minikube delete`

#### Service Accounts

* List service accounts: `kubectl get serviceaccounts`

### Cluster

* Cluster version: `kubectl version`
* Cluster information: `kubectl cluster-info`
* List nodes: `kubectl get nodes`

### Pods

* List of Pods in current namespace: `kubectl get po`
* List of Pods in all amespaces: `kubectl get po --all-namespaces`
* Get containers names: `kubectl get po <POD_NAME> -o jsonpath="{.spec.containers[*].name}"`

* Create a Pod from file: `kubectl create -f pod_definition.yaml`
* Delete a Pod using a YAML definition: `kubectl delete -f pod_definition.yaml`
* Delete a Pod using the Pod name: `kubectl delete <POD_NAME>`
* Delete a Pod instantly: `kubectl delete <POD_NAME> --grace-period=0 --force`

* Execute commands inside a container: `kubectl exec -it -c <CONTAINER_NAME> <POD_NAME> ls`

* Display logs of a Pod: `kubectl logs <POD_NAME>`
* Display logs of a specific container in a Pod: `kubectl logs <POD_NAME> -c <CONTAINER_NAME>`

### User

* Creating a new user

```
openssl genrsa -out user.key 2048 # create key
openssl req key user.key user.csr -subj "/CN=user /O=sgroup" # create csr
openssl x509 -req -in user.csr -CA ca.crt -CAkey ca.key -CAcreateseral -out user.crt -days 365
kubectl config set-credentials myuser --client-certificates=$PWD/user.crt --client-key=$PWD/user.key
kubectl config set-context myuser-context --cluster=k8s-cluster --user=user
```
