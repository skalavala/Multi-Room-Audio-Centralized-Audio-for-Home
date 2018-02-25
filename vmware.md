## Settingup Virtual Sound Card on ESXi

I run Ubuntu Server as a host on VMware (ESXi 6.5). Since the Servers by default don't come with Graphics and Sound Cards, You either need to have a physical sound card, or install virtual sound card. From VMWare 6.0 onwards (I think) Virtual sound card option is no longer available in the configuration settings. To enable virtual sound card running on ESXi 6.0 or above, log in to your ESXi server using SSH, and add the following content to the corresponding host's `.vmx` file. Make sure you the host is stopped before updating `.vmx` file.

```
sound.present = "true"
sound.allowGuestConnectionControl = "false"
sound.virtualDev = "hdaudio"
sound.fileName = "-1"
sound.autodetect = "true"
```
**Remember** to make a backup of the file before modifying. After making changes, restart the Host, and the `hdaudio` will be visible in the host configuration settings.

[Back to home page](README.md)
