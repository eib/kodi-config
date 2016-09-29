
```bash
# Configure wireless
sudo iwlist wlan0 scan | less # Check for wi-fi networks (by ESSID)

# Internet
cat <<EOD > /etc/network/interfaces
source-directory /etc/network/interfaces.d

auto lo
iface lo inet loopback

iface eth0 inet manual

allow-hotplug wlan0
iface wlan0 inet manual
    wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf

iface wifi inet static
    address XXX
    netmask 255.255.255.0
    gateway XXX.1

iface default inet dhcp
EOD

# Wifi networks
cat <<EOD > /etc/wpa_supplicant/wpa_supplicant.conf
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
        ssid="???"
        key_mgmt=WPA-PSK
        psk="???"
        id_str="wifi" #Matches a route in /etc/network/interfaces
        priority=100
}

network={
        ssid="???"
        key_mgmt=WPA-PSK
        psk="???"
        priority=1000
}
EOD

sudo ifdown wlan0 # Bring the wireless NIC down
sudo ifup wlan0 # Bring it back up (with new WPA-supplicant config)
ifconfig -a # Sanity check
```

See also:
* https://www.raspberrypi.org/forums/viewtopic.php?f=91&t=22660
