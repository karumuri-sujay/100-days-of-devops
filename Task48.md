### Task:
The Nautilus DevOps team is diving into Kubernetes for application management. One team member has a task to create a pod according to the details below:

    Create a pod named pod-nginx using the nginx image with the latest tag. Ensure to specify the tag as nginx:latest.

    Set the app label to nginx_app, and name the container as nginx-container.

Note: The kubectl utility on the jump-host has been configured to work with the Kubernetes cluster.

#### Solution:
Use this yaml file
```
apiVersion: v1
kind: Pod
metadata:
  labels:
    app: httpd_app
  name: pod-httpd
spec:
  containers:
  - image: httpd:latest
    name: httpd-container
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}
```
Run the command
```kubectl apply -f pod.yaml```
