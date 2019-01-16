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

#### Display PV 
`pvdisplay` Display info about all pvs <br /> 
`pvdisplay /dev/{dev-name}` Display info about specified pv <br />

## Logical Volumes
#### Create logical volume
`fdisk /dev/{device-name}` Format device of type logocal volume (0xe8) <br />
`partprobe` Register the device with the kernel <br />
`pvcreate <device-1> <device-2> ...` Initialize phisical volumes for use as logical volumes <br />
`vgcreate <vg-name> <device-1> <device-2> ...` Create a logical volume group <br />
`lvcreate -n <lv-name> -L 2G <vg-name>` Create a new Logical volume (use lowercase l option for size by physical extant)<br /> 
`mkfs -t xfs /dev/<vg-name>/<lv-name>` Put a file system on logical volume <br /> 

#### Remove logical volume
`umount /mnt/<lv-name>` Unmount volume <br />
`lvremove /dev/vg-alpha/<lv-name>` Remove logical volume <br />
`pvremove <device-1> <device-2> ...` Remove physical volumes <br />

#### Changing logical volume size
`vgextend <vg-name> <device>` Adds device to volume group <br />
`lvextend -L +300M /dev/{vg-name>}/{lv-name}` Extend logical volume by specified size <br /> 

`pvmove <device>` Moves all physical extends off of device so that it can be removed from a vg <br />
`vgreduce vg-alpha <device>` Removes device from volume group <br />
`xfs_growfs /mnt/{lv-mount}` Extend file system that logical volume uses (xfs)<br />
`resize2fs /dev/{vg-name}/{lv-name}` Extend file system that logical volume uses (ext4) <br />

***

#### Display LV
`vgdisplay` Display info about all volume group <br /> 
`vgdisplay <vg-name>` Display info about specified volume groups <br />
`lvdisplay` Display info about all lvspv <br /> 
`lvdisplay /dev/{vg-name}/{lv-name}` Display info about specified lv <br />

### List what is listening on each port
`netstat -tulpn`

### fidsk
`fdisk -l` List device types <br />
`fdisk -l <device-name>` List partitions of a device <br />

### Logs
`journalctl -u [service]` - View logs for a specified service

### Background Processes
`show` Print background processes liked to terminal <br />
`kill %<process-number>` Kill a lined process <br />

### Kernel Modules
`lsmod` List Modules <br />
`lsmod | grep bridge` List network bridges <br>
