## Settingup Virtual Sound Card on ESXi

I run Ubuntu Server as a host on VMware (ESXi 6.5). Since I have a DELL PowerEdge Server, by default servers don't come with sound card, and from VMWare 6.0 onwards (I think) there is no support for virtual sound card. To enable virtual sound card running on ESXi 6.5, log in to your ESXi server using SSH, and add the following content to the  `.vmx` file. 

Note: Prior to making changes, make sure you the host is stopped/shutdown first.

Add the following at the end:

```
sound.present = "true"
sound.allowGuestConnectionControl = "false"
sound.virtualDev = "hdaudio"
sound.fileName = "-1"
sound.autodetect = "true"
```
**Make sure** you make a backup of the file before modifying. After making changes, restart the Host, and  `hdaudio` will be visible in the host configuration settings.
