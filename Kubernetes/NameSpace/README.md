# Kubernetes

> NameSpace
### List the Namespace 
```
kubectl get namespace 
```
or
```
kubectl get ns 
```
![image](https://github.com/itsmanibharathi/Docker_Kubernetes/assets/76097762/d86c8762-5b13-4d89-b712-f6e80eb5dd8f)

### Create new Namespace 
Create new file namespace.yaml
```
---
apiVersion: v1
kind: Namespace
metadata:
  name: production
```
```
kubectl apply -f ./namespace.yaml
```
![image](https://github.com/itsmanibharathi/Docker_Kubernetes/assets/76097762/84ce86c2-fb44-41f6-ab5f-79ecc8739c30)



