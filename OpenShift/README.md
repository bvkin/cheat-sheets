# OpenShift Cheat Sheet


## oc get resources
`oc get`

`oc get resouce-type resource-name -o yaml` - Return as yaml <br />

`oc get all`

`oc get events`
Filter for when things were created <br />
`oc get events --sort-by='.metadata.creationTimestamp'`

`oc get nodes`

`oc get pods` <br />
`oc get pods -o wide` - Includes the IP <br />

`oc get scc` - List all available SCCs <br />
`oc describe scc scc_name` - Detailed info on a specific SCC

## oc describe resources
`oc describe`

Describe resources only from a specified namespace <br />
`oc describe -n name-space` 

`oc describe pod pod-name`

`oc describe is image-stream-name`

`oc describe clusterPolicyBindings :default` - describe who can do what <br />

## oc edit resuources
`oc edit`

`oc patch dc/demo-app --patch '{"spec":{"template":{"spec":{"serviceAccountName": "useroot"}}}}'`

## export resources
`oc export`

`oc export pod pod-name`

Export multiple resources as a template <br />
`oc export svc,dc docker-registry --as-template=docker-registry` 

### Return current user

### Logging in
`oc login -u username -p password https://master.example.com`

### Creating a new project
`oc new-project project-name`
`oc new-project demoproject --description="Project description" --display-name="project-display-name" ` 

### Change project
`oc project project-name`

### Return high level status of current project
`oc status`
`oc status -v`

### Install the oc command
`sudo yum install atomic-openshift-clients`

### Deploying a new application
`oc new-app --name=app-name image:tag https://registry-url.example.com`

### Run a new version of a deployment config
`oc rollout latest hello`

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


## Cluster Administration
![Project Level](./images/oc-adm-project-level.png)

![Cluster Level](./images/oc-adm-cluster-level.png)

### Grant a user or group a specific SCC
```
oc adm policy add-scc-to-user scc_name user_name
oc adm policy add-scc-to-group scc_name group_name
```

### Remove a user or group from a specific SCC
```
oc adm policy remove-scc-from-user scc_name user_name
oc adm policy remove-scc-from-group scc_name group_name
```

### Add policy to service account
`oc adm policy add-scc-to-user anyuid -z useroot`

### Create regular user
`oc create user user-name`

### Create service account
`oc create serviceaccount svc-account-name`
