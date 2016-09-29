How to set up the Raspberry Pi (after first boot-up)

```bash

# HDMI fixes (forcing 1080i and removing black borders)
echo "hdmi_group=1" | sudo tee -a /boot/config.txt
echo "hdmi_mode=5" | sudo tee -a /boot/config.txt
echo "disable_overscan=1" | sudo tee -a /boot/config.txt

sudo raspi-config
# Internationalisation Options > Change Locale > uncheck en_GB.whatever, check en_US.UTF-8
# Internationalisation Options > Keyboard
# Internationalisation Options > Change Timezone

# sudo reboot
```

Sanity-checks:
```bash
sudo nano /etc/default/locale # Expecting LANG=en_US.UTF-8
sudo nano /etc/default/keyboard # Expecting XKBMODEL="pc104" and/or XKBLAYOUT="us"
```

See also:
* http://elinux.org/RPiconfig#Video
* http://elinux.org/R-Pi_Troubleshooting#Big_black_borders_around_small_image_on_HD_monitors

