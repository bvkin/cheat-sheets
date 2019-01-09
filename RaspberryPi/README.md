# Raspberry Pi Cheat Sheet

### Setting Up WiFi

`sudo vi /etc/wpa_supplicant/wpa_supplicant.conf`

Add the following:

```
network={
       ssid="Network Name"
       psk="Network Password"
}
```

### Setting up a static IP address

`sudo vi /etc/dhcpcd.conf`

Add the following to the end of the file

```
interface wlan0

static ip_address=192.168.1.28/24
static routers=192.168.1.1
static domain_name_servers=192.168.1.1
```

### SSH as root

`sudo vi /etc/ssh/sshd_config`

Add the following:
`PermitRootLogin yes` <br />
`PermitRootLogin without-password` <br />

**Note:** Must edit /etc/ssh/sshd_config and not /etc/ssh/ssh_config

### Backup image
`sudo dd bs=4M if=/dev/sdb of=raspbian.img status=progress` Create backuo <br />
`sudo dd bs=4M if=raspbian.img of=/dev/sdb status=progress` Restore backup <br />
`sudo dd bs=4M if=/dev/sdb | gzip > raspbian.img.gz` Create compressed backup <br />
`gunzip --stdout raspbian.img.gz | sudo dd bs=4M of=/dev/sdb status=progress` Restore compressed backup <br />

#### Kubernees backup restore steps:
* Change hostname `hostnamectl set-hostname computeX` as well as loopback in `/etc/hosts`
* Connect to network `vi /etc/wpa_supplicant/wpa_supplicant.conf` (uncomment lines)  and uncomment entry in `/etc/dhcpcd.conf` - remember to change ip address
* Reboot


