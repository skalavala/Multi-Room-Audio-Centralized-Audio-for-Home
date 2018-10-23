## Install Snapcast Client

Before executing the commands, go to https://github.com/badaix/snapcast/releases and copy the location of the latest snapclient installer file. The Installer file for Raspberry Pi usually has armhf in it as the RPis have arm processors.

Make sure you update file name in the command below snapclient_x.xx.x_armhf.deb below and execute the command.
```
wget https://github.com/badaix/snapcast/releases/download/v0.11.0/snapclient.xx.x_armhf.deb
```
after downloading the file, execute the following command to install the software. Again, replace the file name with correct version.
```
sudo dpkg -i snapclient_x.xx.x_armhf.deb
```
After installation, run the following to install any missing libraries
```
sudo apt-get -f install
```
It is time to "restart" the Raspberry Pi. Use the following command to restart.
```
sudo reboot
```
The snapclient configuration can be edited by using the following command:
```
sudo vi /etc/default/snapclient
```
You can check the status by running the following command
```
systemctl status snapclient
```

Upon executing the above commands, restart the Raspberry Pi using the following command.
```
sudo reboot
```

After the restart, the snapcast client automatically connects to the snapcast server within the network. If you are using Home Assistant, masure sure you check the version compatibility, and restart Home Assistant (HA), to see these snapcast clients as media players.

## Troubleshooting
When you run snapclient, sometimes you get errors that cookies not found in `/var/lib/snapclient/.config/pulse`. To get around that problem, I simply copy cookie files from `~/.config/pulse` to respective folder in `/var/lib` folder. Run the following commands:

```
cd /var/lib
sudo mkdir snapclient
sudo chmod 777 .
cd snapclient
sudo mkdir .config
sudo chmod 777 .
cd .config
sudo mkdir pulse
sudo chmod 777 .
cd pulse

cd ~
cd .config
cd pulse

sudo cp *.* /var/lib/snapclient/.config/pulse
sudo cp * /var/lib/snapclient/.config/pulse
```

Make sure you restart snapclient after copying the cookies.

```
sudo systemctl restart snapclient
sudo systemctl status snapclient
```

[Back to home page](README.md)

