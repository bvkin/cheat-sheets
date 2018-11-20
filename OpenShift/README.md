# OpenShift Cheat Sheet

`oc get`

`oc describe`

### Return everything
`oc get all`

### Install the oc command
`sudo yum install atomic-openshift-clients`

### Logging in
`oc login -u username -p password https://master.example.com`

### Creating a new project
`oc new-project project-name`

### Deploying a new application
`oc new-app --name=app-name php:7.0 https://registry.example.com`

### Scale up pods
`oc scale --replicas=2 dc dc-name`

### Pods with IP
`oc get pods -o wide`

### Create Route
`oc expose service service-name --name route-name --hostname=quoteapp.apps.lab.example.com`

### SSH into pod
`oc rsh <pod>`
