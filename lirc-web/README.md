For running   as a (systemd) service.

Run (from this directory):
```bash
# Install NVM (Node Version Manager)
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.32.0/install.sh | bash
nvm install 6

# Install lirc_web node app
sudo mkdir /opt/lirc_web
sudo chown pi.pi /opt/lirc_web
git clone https://github.com/alexbain/lirc_web.git /opt/lirc_web
echo "{}" > /home/pi/.lirc_web_config.json
nvm use 6
cd /opt/lirc_web && npm install && cd -

# Set up lirc-web.service
sudo cp lib_systemd_system_lirc-web.service /lib/systemd/service/lirc-web.service
sudo cp etc_default_lirc-web /etc/default/lirc-web
sudo systemctl enable lirc-web.service
sudo systemctl daemon-reload

# Start the service
sudo systemctl start lirc-web
```
