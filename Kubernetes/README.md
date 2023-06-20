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

### Delete a Namespace

```
kubectl delete -f ./namespace.yaml
```
![image](https://github.com/itsmanibharathi/Docker_Kubernetes/assets/76097762/cb77c571-0592-4850-b2b1-c2644ec92171)

> Deployment
### create deployment 
create new deployment.yaml file
```
---
apiVersion: v1
kind: Namespace
metadata:
  name: development
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: pod-info-deployment
  namespace: development
  labels:
    app: pod-info
spec:
  replicas: 4
  selector:
    matchLabels:
      app: pod-info
  template:
    metadata:
      labels:
        app: pod-info
    spec:
      containers:
      - name: pod-info-container
        image: kimschles/pod-info-app:latest
        ports:
        - containerPort: 3000
        env:
          - name: POD_NAME
            valueFrom:
              fieldRef:
                fieldPath: metadata.name
          - name: POD_NAMESPACE
            valueFrom:
              fieldRef:
                fieldPath: metadata.namespace
          - name: POD_IP
            valueFrom:
              fieldRef:
                fieldPath: status.podIP
```
```
kubectl apply -f deployment.yaml
```
![image](https://github.com/itsmanibharathi/Docker_Kubernetes/assets/76097762/7d74a6a2-cd74-4d13-a5c3-4eb452b3db10)

#### List all pods
```
kubectl get pods -A 
```
![image](https://github.com/itsmanibharathi/Docker_Kubernetes/assets/76097762/a6fe8ca7-e91f-4328-8172-79d53ed214cb)

### List only namespace pods
```
kubectl get pods -n development
```
![image](https://github.com/itsmanibharathi/Docker_Kubernetes/assets/76097762/a8180a21-ff0d-4eef-b81b-6d93ee68ac39)

### Get the Event log of pods
```
kubectl describe pods [pods-id] -n [name-space]
```
![image](https://github.com/itsmanibharathi/Docker_Kubernetes/assets/76097762/4cb27aca-78f0-4e5b-ac7b-a666582d1d02)

### Get the Short log of pods
```
kubectl logs [pods-id] -n [name-space]
```
![image](https://github.com/itsmanibharathi/Docker_Kubernetes/assets/76097762/190700ec-6336-4155-96f0-c07be842ccec)

### Delete a Deployment
```
kubectl delete -f deployment.yaml
```
![image](https://github.com/itsmanibharathi/Docker_Kubernetes/assets/76097762/4c0ad4de-2d21-46a8-9fdb-744918610bae)

> Security

![image](https://github.com/itsmanibharathi/Docker_Kubernetes/assets/76097762/8bd1ca5b-768f-472e-80e0-cf5e4b4e7c17)

