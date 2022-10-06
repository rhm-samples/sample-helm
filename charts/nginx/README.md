# sample-helm
command used to run helm chart from container

```
git clone https://github.com/bitnami/charts.git
cd charts/bitnami/nginx
helm repo add my-repo https://charts.bitnami.com/bitnami
helm dependency build
helm install nginxchart . --namespace targetns
``` 
(Target ns was created manually before installing the chart)


**Role permissions**

```
kind: Role
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: helmrole
  namespace: demo
rules:
  - verbs:
      - list
      - get
      - watch
      - create
      - delete
    apiGroups:
      - ''
    resources:
      - pods
  - verbs:
      - create
    apiGroups:
      - ''
    resources:
      - pods/exec
  - verbs:
      - get
    apiGroups:
      - ''
    resources:
      - pods/log
  - verbs:
      - list
      - get
      - create
      - delete
      - update
    apiGroups:
      - ''
    resources:
      - pods/attach
  - verbs:
      - list
      - get
      - create
      - delete
      - update
    apiGroups:
      - ''
    resources:
      - secrets
  - verbs:
      - list
      - get
      - create
      - delete
      - update
    apiGroups:
      - ''
    resources:
      - services
  - verbs:
      - list
      - get
      - watch
      - create
      - delete
      - update
      - patch
    apiGroups:
      - '*'
    resources:
      - deployments

```
