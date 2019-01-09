## Regirstries

#### Create secret with docker credentials
```
kubectl create secret docker-registry regcred \
--docker-server=<your-registry-server> \ 
--docker-username=<your-username> \
--docker-password=<your-password> \
--docker-email=<your-email> 
```
- (`--docker-server` defaults to dockerhub)

#### Use credentials for a pod
```
apiVersion: v1
kind: Pod
metadata:
  name: private-reg
spec:
  containers:
  - name: private-reg-container
    image: <your-private-image>
  imagePullSecrets:
  - name: regcred
```