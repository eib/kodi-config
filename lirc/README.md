How to set up lirc (with a custom IR receiver/LEDs)

```bash
# ensure running as root
if [ "$(id -u)" != "0" ]; then
  exec sudo "$0" "$@" 
fi

apt-get install lirc

# Configure modules
echo "dtoverlay=lirc-rpi,gpio_in_pin=23,gpio_out_pin=22" >> /boot/config.txt
echo <<EOD >> /etc/modules
lirc_dev
lirc_rpi gpio_in_pin=23 gpio_out_pin=22
EOD


# Configuration files
sudo cp -r etc_lirc/* /etc/lirc/ #Overwrites old/default files

# Start the services
sudo service lirc restart
# Or, just do a reboot?
```


See also:
* http://alexba.in/blog/2013/01/06/setting-up-lirc-on-the-raspberrypi/
* http://opensourceuniversalremote.com/
