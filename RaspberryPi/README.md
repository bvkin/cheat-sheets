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

`sudo vi /etc/ssh/ssh_config`

Add:
`PermitRootLogin yes`
`PermitRootLogin without-password`

### Backup image
`sudo dd bs=4M if=/dev/sdb of=raspbian.img` Create backuo <br />
`sudo dd bs=4M if=raspbian.img of=/dev/sdb` Restore backup <br />
`sudo dd bs=4M if=/dev/sdb | gzip > raspbian.img.gz` Create compressed backup <br />
`gunzip --stdout raspbian.img.gz | sudo dd bs=4M of=/dev/sdb` Restore compressed backup <br />
