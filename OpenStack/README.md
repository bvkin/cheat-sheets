`openstack global-options command command-action arguments`

### Create an instance
`openstack server create --flavor default --image rhel7 demo-server1`

### Delete an instance
`openstack server delete server-name`

### Logs of an instance
`openstack console log show server-name`

### Get url
`openstack console url show server-name`

### List Commands
`openstack server list` <br/>
`openstack volume list` <br/>
`openstack network list` <br/>
`openstack flavor list` <br/>
`openstack image list` <br/>

### Modifeid list Command
`openstack server list -c"ID" -c"Name"`-Example only show server ID and name

### Show Commands
`openstack server show server-name` <br/>
`openstack network show network-name` <br/>
`openstack flavor show flavor-name` <br/>
`openstack project show project-name` <br/>
`openstack user show user-name` <br/>

### Output as json
`openstack server list -f json` <br/>

### Output as shell variables
`openstack server show -f shell --prefix my_ demo-server1`

### Debug info
`openstack server create --flavor nodefault --image rhel7 --debug demo-server1

### Change server root password
openstack server set --root-password demo-server1
