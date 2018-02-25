## Settingup Virtual Sound Card on ESXi

I run my Ubuntu Server as a host on VMWare (ESXi 6.5). Since the real "Servers" by default don't come with Graphics and/or Sound Cards, you either need to have a physical sound card, or install virtual sound card. From VMWare 6.0 onwards (I think) Virtual sound card option is no longer available in the configuration settings. To enable virtual sound card running on ESXi 6.0 or above, log in to your ESXi console using SSH, and add the following content to the corresponding host's `.vmx` file using `vi` or your favorite editor. Make sure you the host is stopped before updating `.vmx` file, and **remember** to take a backup prior to making changes.

```
sound.present = "true"
sound.allowGuestConnectionControl = "false"
sound.virtualDev = "hdaudio"
sound.fileName = "-1"
sound.autodetect = "true"
```
After making changes, restart the Host, and the `hdaudio` will be visible in the host configuration settings.

[Back to home page](README.md)
