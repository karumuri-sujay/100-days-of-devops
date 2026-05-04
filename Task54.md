### Task:
kubernetes shared volumes

#### Solution:
```apiVersion: v1
kind: Pod
metadata:
  labels:
    run: volume-share-xfusion
  name: volume-share-xfusion
spec:
  volumes:
  - name: volume-share
    emptyDir: {}
  containers:
  - image: debian:latest
    name: volume-container-xfusion-1
    command: ["/bin/sh", "-c", "while true; do sleep 10; done"]
    volumeMounts:
    - name: volume-share
      mountPath: /tmp/beta
    resources: {}
  - image: debian:latest
    name: volume-container-xfusion-2
    command: ["/bin/sh", "-c", "while true; do sleep 10; done"]
    volumeMounts:
    - name: volume-share
      mountPath: /tmp/games
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}```


use this command to go inside of the container and check the files
```kubectl exec -it volume-share-xfusion -c volume-container-xfusion-2 -- /bin/sh```
