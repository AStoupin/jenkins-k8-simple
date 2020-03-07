The sketch is based on the article
https://medium.com/faun/deploying-and-scaling-jenkins-on-kubernetes-2cd4164720bd

Some preparations:

1. Create a to grand some kube commands
kind: ClusterRole
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  namespace: default
  name: service-reader
rules:
- apiGroups: [""] # "" indicates the core API group
  resources: ["services","pods","pods/exec"]
  verbs: ["get", "pods/exec", "watch", "list","create","delete"]
   
2.  Give that role to default:default (jenkins account will work with)
kubectl create clusterrolebinding service-reader-pod   --clusterrole=service-reader  --serviceaccount=default:default