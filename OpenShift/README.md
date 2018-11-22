# OpenShift Cheat Sheet


## oc get resources
`oc get`

`oc get all`

`oc get events`

`oc get nodes`

`oc get pods` <br />
`oc get pods -o wide` Includes the IP

## oc describe resources
`oc describe`

Describe resources only from a specified namespace <br />
`oc describe -n name-space` 

`oc describe pod pod-name`

`oc describe is image-stream-name`

## oc edit resuources
`oc edit`

## export resources
`oc export`

`oc export pod pod-name`

Export multiple resources as a template <br />
`oc export svc,dc docker-registry --as-template=docker-registry` 

### Logging in
`oc login -u username -p password https://master.example.com`

### Creating a new project
`oc new-project project-name`

### Change project
`oc project project-name`

### Return high level status of current project
`oc status`
`oc status -v`

### Install the oc command
`sudo yum install atomic-openshift-clients`

### Deploying a new application
`oc new-app --name=app-name image:tag https://registry-url.example.com`

### Scale up pods
`oc scale --replicas=2 dc dc-name`

### Create Route
`oc expose service service-name --name route-name --hostname=quoteapp.apps.lab.example.com`

### SSH into pod
`oc rsh <pod>`

### Execute commands against a pod
`oc exec pod-name command`

### Logging resources
`oc logs resource-name`
