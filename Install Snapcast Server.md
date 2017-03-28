## Install Snapcast Server

The easiest part in the whole set up is installing Snapcast server and client components.

Before executing the commands, go to [https://github.com/badaix/snapcast/releases](https://github.com/badaix/snapcast/releases){:target="_blank"} and copy the location of the latest snapserver installer file. The Installer file for Raspberry Pi usually has `armhf` in it as the RPis have arm processors.

Make sure you update file name in the command below `snapclient_x.xx.x_armhf.deb` below and execute the command.

```
wget https://github.com/badaix/snapcast/releases/download/v0.11.0/snapclient_x.xx.x_armhf.deb
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

The snapserver configuration can be edited by using the following command:
```
sudo vi /etc/default/snapserver
```

You can check the status by running the following command
```
systemctl status snapserver
```


[Back to home page](README.md)
