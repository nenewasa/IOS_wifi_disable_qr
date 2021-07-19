# IOS_wifi_disable_qr
https://twitter.com/vm_call/status/1405937492642123782 -> QR code. and hostapd set up. 

![](thumbnail_iphone-strings-wifi-bug-QR.png)




## install deps

`sudo apt install hostapd dnsmasq`

## stop for configuration

```
sudo systemctl stop hostapd
sudo systemctl stop dnsmasq
```

## get your wireless interface name

`ifconfig or ip addr`

## edit .conf file.

`sudo nano /etc/hostapd/hostapd.conf`

## insert interface name and copy paste.

```
interface= (YOUR INTERFACE)
bridge=br0
hw_mode=g
channel=7
wmm_enabled=0
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
ssid=%p%s%s%s%s%n
wpa_passphrase=password1
```

## set conf file to be used

`sudo nano /etc/default/hostapd`

## change/uncomment
```
#DAEMON_CONF=""
DAEMON_CONF="/etc/hostapd/hostapd.conf"
```

## reboot

`reboot`


## systmctl commands. to turn on and off the AP enable/disable the hostapd service

if asked to unmask then run the unmask command as well.
```
sudo systemctl status hostapd
sudo systemctl enable hostapd
sudo systemctl unmask hostapd
sudo systemctl disable hostapd
```
