### Tarballs
`tar xvzf file.tar.gz` Extract tar.gz file

`tar -cvzf tarballname.tar.gz path/` Compress directory

### Configuring Static IPs
`vi /etc/sysconfig/network-scripts/ifcfg-eth0`

```
TYPE=Ethernet
PROXY_METHOD=none
BROWSER_ONLY=no
BOOTPROTO=static
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
IPV6INIT=yes
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_FAILURE_FATAL=no
IPV6_ADDR_GEN_MODE=stable-privacy
NAME=eth0
UUID=d0ec43b3-a5c3-4ab0-9fae-cfadd2e0b55a
DEVICE=eth0
ONBOOT=yes
IPADDR=192.168.122.25
NETMASK=255.255.255.0
GATEWAY=192.168.122.1
```
