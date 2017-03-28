## Install Snapcast Client

Before executing the commands, go to https://github.com/badaix/snapcast/releases and copy the location of the latest snapserver installer file. The Installer file for Raspberry Pi usually has armhf in it as the RPis have arm processors.

Make sure you update file name in the command below snapserver_x.xx.x_armhf.deb below and execute the command.
```
wget https://github.com/badaix/snapcast/releases/download/v0.11.0/snapsrver_x.xx.x_armhf.deb
```
after downloading the file, execute the following command to install the software. Again, replace the file name with correct version.
```
sudo dpkg -i snapserver_x.xx.x_armhf.deb
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


[Back to home page](README.md)


