### Package Management 
`rpm -qa` - list installed packages
`rpm -ql <package-name>` List files installed by particular package

`dnf --refresh upgrade` - Update system <br />
`sudo dnf config-manager --add-repo https://example.com/example.repo` - add a repository to system

### Tarballs
`tar xvzf file.tar.gz` Extract tar.gz file <br />
`tar -cvzf tarballname.tar.gz path/` Compress directory <br />
`tar -ztvf my-data.tar.gz` Query files in a directory <br />

### Editing systemd services
`vi /usr/lib/systemd/system/firewalld.service`

## Using Subscription Managaer

#### Enable certain repos example
```
subscription-manager repos \
    --enable="rhel-7-server-rpms" \
    --enable="rhel-7-server-extras-rpms" \
    --enable="rhel-7-server-ose-3.11-rpms" \
    --enable="rhel-7-server-ansible-2.6-rpms"
```

#### List repos
`sudo subscription-manager list --available`

#### Refresh Subscription manager
```
sudo subscription-manager remove --all
sudo subscription-manager unregister
sudo subscription-manager clean

sudo subscription-manager register
sudo subscription-manager refresh
sudo subscription-manager attach --auto
```

### Libvirt Snapshots
```
virsh snapshot-create-as --domain {VM-NAME} --name "{SNAPSHOT-NAME}"
virsh snapshot-delete --domain freebsd --snapshotname 5Sep2016_S2
virsh snapshot-revert --domain freebsd --snapshotname 5Sep2016_S1 --running
virsh shutdown --domain freebsd
```

### List what is listening on each port
`netstat -tulpn`

### fidsk
`fdisk -l` List device types <br />

### Logs
`journalctl -u [service]` - View logs for a specified service
