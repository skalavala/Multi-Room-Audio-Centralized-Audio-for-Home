## Settingup Virtual Sound Card on ESXi

I run my Ubuntu Server as a host on VMWare (ESXi 6.5). Since the real "Servers" by default don't come with Graphics and/or Sound Cards, you either need to have a physical sound card, or install virtual sound card. From VMWare 6.0 onwards (I think) Virtual sound card option is no longer available in the configuration settings. 

To enable virtual sound card running on ESXi 6.0 or above, log in to your ESXi console using SSH, and add the following content to the corresponding host's `.vmx` file using `vi` or your favorite editor. 

Note: If SSH is not enabled for any specific reason, you can enable by :
1. Click on the ESXi server name in the vSphere Client, 
2. Go to "Configuration" tab
3. Click on "Security Profile" link on the left navigation menu
4. Click on "Properties" link on the right side of the Security Profile -> Services section.
5. Select SSH in the dialog box, and run the SSH Server.

Before making changed to the host configuration, it is always a good idea to properly shutdown the server. Make sure you the host is stopped before updating `.vmx` file, and **remember** to take a backup prior to making changes.

To find out where all the `vmx` files are, run the following command in the CLI from the root folder:

```
find . -type f -name "*.vmx"
```


The commandabove should show you all the `.vmx` files with full path. Typically they are under `./vmfs/volumes/` folder with a GUID as the folder name for the host.

```
sound.present = "true"
sound.allowGuestConnectionControl = "false"
sound.virtualDev = "hdaudio"
sound.fileName = "-1"
sound.autodetect = "true"
```
After making changes, restart the Host, and the `hdaudio` will be visible in the host configuration settings.

[Back to home page](README.md)
