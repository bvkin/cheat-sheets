### Configuring Static IPs
`vi /etc/sysconfig/network-scripts/ifcfg-*` <br/>
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

### Configuring network bridges
`vi /etc/sysconfig/network-scripts/ifcfg-br-*` <br/>
```
DEVICE=br-demo
TYPE=Bridge
IPADDR=172.25.249.100
PREFIX=24
ONBOOT=yes
```

`/etc/sysconfig/network-scripts/ifcfg-eth*`
```
DEVICE=eth3
BRIDGE=br-demo
ONBOOT=yes
```

***


### Add a DNS server
`vi /etc/resolv.conf`
```
# Generated by NetworkManager
nameserver 192.168.122.1
```

### Check out device type
`ethtool -i <device>`

### Netcat
`nc <host> <port>` Connect to a port <br />
`nc -z -v <host> <port>-<port>` Scan for open ports between a range <br />
`nc -l <port> | <remote-file-name>.txt` Listen for a connectino on a specific port <br />
`cat <local-file-name>.txt | nc <host> <port>` Send file over a tcp connection <br />

### Ip
`ip a` Get interface ip addresses <br />
`ip link` Show link layer mac addresses <br />
`ip link set dev <interface> up/down` Set network interface up or down <br />
`ip a add/del <ip-address>/<mask> dev <interface>` Add or delete ip address to a network interface <br />
`ip route show` Display the kernel's routing table <br />
`ip route add <destination> via <gateway> dev <interface>` Add route to routing table <br />
`ip route del <destination>` Remove route from routing table <br />
`ip neigh show` Display ARP table <br />
`ip neigh add|del <ip-address> lladdr <mac> nud permanent dev <interface>` Manually add pr delete entries from ARP table <br />
`ip netns list` List all network namespaces <br />
`ip netns add <namespace>` Add network namespace <br />
`ip netns delete <namesapce>` Delete network namespace <br />

***

## `brctl` Commands
`brctl addbr <bridge>` Adds a bridge <br />
`brctl delbr <bridge>` Deletes a bridge <br />
`brctl addif <bridge> <device>`	Adds a network interface to a bridge <br />
`brctl delif <bridge> <device>`	Deletes an interface from a bridge <br />
`brctl show` Lists all available bridges <br />
`brctl showmacs <bridge>`	Lists the MAC addresses used by a bridge <br />

#### Enslave a newtwork device to a bridge
`ip address flush ethX` Flush the device to remove it's current configuration/ip <br />
`brctl addif <bridge> ethX` Enslave the bridge <br />
`ip address add <ip> dev <bridge>` Attach an ip to the bridge <br />
`ip link set <device> <bridge-name> up` bring the bridge up <br />
***

## Open vSwitch Commands
`ovs-vsctl show` Displays an overview of Open vSwitch database contents <br />
`ovs-vsctl add-br <bridge>` Defines a new bridge named BRIDGE <br />
`ovs-vsctl del-br <bridge>` Deletes the BRIDGE bridge and its ports <br />
`ovs-vsctl list-br`	Lists all bridges <br />
`ovs-vsctl add-port <bridge> <port>` Adds the PORT network device to the BRIDGE <br />
`ovs-vsctl del-port <bridge> <port>` Removes the PORT network device from the BRIDGE <br />
`ovs-vsctl list-ifaces <bridge>` Lists all interfaces on BRIDGE <br />
`ovs-vsctl iface-to-br <interface>`	Displays the bridge that contains the specified interface <br />
`ovs-vsctl list-ports <bridge>`	Displays ports attached to the BRIDGE <br />
`ovs-vsctl set bridge <bridge-name> other-config:hwaddr=\"52:54:00:04:00:01\"` Give the vswitch specified mac address <br />

#### Capture tcp packets
`tcpdump` All packets <br />

## Firewall
`firewall-cmd --list-all` List all enabled services <br />
`firewall-cmd --add-service=<service-name>` Allow packets through of a specified service <br />
`firewall-cmd --add-service=<service-name> --permanent` Make allow rule permanent <br />


## Selinux
`tail -f /var/log/audit.log` Selinux logs <br />
`ausearch -m avc --start recent` For more human friendly logs <br />

Log Parts

| Log Part                                     | Name             |
|----------------------------------------------|------------------|
| type=AVC                                     | Log type         |
| msg=audit(1363289005.532:184)                | Timestamp        |
| avc:                                         | Log type (again) |
| denied                                       | State            |
| { read }                                     | Permission       |
| for pid=29199                                | Process PID      |
| comm="Trace"                                 | Process CMD      |
| name="online"                                | Target name      |
| dev="sysfs"                                  | Device           |
| ino=30                                       | inode number     |
| scontext=staff_u:staff_r:googletalk_plugin_t | Source context   |
| tcontext=system_u:object_r:sysfs_t           | Target context   |
| tclass=file                                  | Target class     |

`semodule -DB` Remove obscuring of logs <br />
`semodule -B` Re-obscure logs <br />

`seinfo` Query whole selinux policy <br />

`setenforce 0` Set to permissive mode <br />
`setenforce 1` Set to enforcing mode <br />

### View Ports in use
`netstat -tulpn`

### View Process Running on a port
`lsof -i TCP:<port-number>


## NetworkManager
`nmcli dev status` Get device status  <br />
`nmcli dev wifi list` List reachable wifi networks <br />
`nmcli connection up <connecton-name>` Bring a connection up  <br />
`nmcli connection add con-name <connection-name> type <connection-type> ssid <ssid-name> device <device-name>` Add a new connection <br />
`nmcli connection add con-name <connection-name> type <connection-type> ip4 <address> gw4 <gateway> ipv4.dns <dns>` Configure static ip <br />
`nmcli con modify <connection-name> wifi-sec.key-mgmt wpa-psk` Configure for wifi passwords <br />
`nmcli con modify <connection-name> wifi-sec.psk <password>` Give connection a password <br />

### Adding network bridges
`nmcli con add type bridge autoconnect yes con-name br0 ifname br0` <br/>
`nmcli con add type bridge-slave autoconnect yes con-name en01s0 ifname eno1 master br0` <br/`>
`nmcli con modify br0 ipv4.addresses <subnet-ip> ipv4.method manula` <br />
`nmcli con modify br0 ipv4.gateway <gw>` <br />
`nmcli con modify br0 ipv4.dns <dns>` <br />