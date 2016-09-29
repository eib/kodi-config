How to customize Kodi to work with LIRC remotes, etc.


```bash
which kodi || sudo apt-get install -y kodi
sudo cp usr_share_kodi_system_Lircmap.xml /usr/share/kodi/system/Lircmap.xml
sudo cp usr_share_kodi_system_keymaps_remote.xml /usr/share/kodi/system/keymaps/remote.xml
# And reboot/restart kodi
```
