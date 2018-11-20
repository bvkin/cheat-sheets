# Setting Up WiFi

`sudo vi /etc/wpa_supplicant/wpa_supplicant.conf`

Add the following:

```
network={
       ssid="Network Name"
       psk="Network Password"
}
```

# Setting up a static IP address

`sudo vi /etc/dhcpcd.conf`

Add the following to the end of the file

```
interface wlan0

static ip_address=192.168.1.28/24
static routers=192.168.1.1
static domain_name_servers=192.168.1.1
```
