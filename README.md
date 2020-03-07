The sketch is based on the articles
https://medium.com/faun/deploying-and-scaling-jenkins-on-kubernetes-2cd4164720bd
https://github.com/jenkinsci/kubernetes-plugin

Some preparations:

1. Create a to grand some kube commands
kind: ClusterRole
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  namespace: default
  name: service-reader
rules:
- apiGroups: [""] # "" indicates the core API group
  resources: ["services","pods","pods/exec","deployments"]
  verbs: ["get", "pods/exec", "watch", "list","create","delete", "apply"]
- apiGroups: ["extensions", "apps"]
  resources: ["deployments","replicasets"]
  verbs: ["get", "list", "watch", "create", "update", "patch", "delete", "apply"]
  
 /*
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: service-reader-pod
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: service-reader
subjects:
  - kind: ServiceAccount
    name: default
    namespace: default
*/      
   
2.  Give that role to default:default (jenkins account will work with)
kubectl create clusterrolebinding service-reader-pod   --clusterrole=service-reader  --serviceaccount=default:default