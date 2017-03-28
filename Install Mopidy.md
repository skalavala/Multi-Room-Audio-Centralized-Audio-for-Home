## Please follow the commands below to install Mopidy on the Raspberry Pi


1. Add the archive’s GPG key:
```
wget -q -O - https://apt.mopidy.com/mopidy.gpg | sudo apt-key add -
```

2. Add the APT repo to your package sources:
```
sudo wget -q -O /etc/apt/sources.list.d/mopidy.list https://apt.mopidy.com/jessie.list
```

3. Install Mopidy and all dependencies:
```
sudo apt-get update
sudo apt-get install mopidy
```

Run this when Mopidy releases a new version:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Add the following in ~/.config/mopidy/mopidy.conf file
```
[mpd]
hostname = ::

[http]
Hostname = ::
```

Check config:
sudo mopidyctl config
	

## Running Mopidy as Service
On Debian systems (both those using systemd and not) you can enable the Mopidy service by running:
sudo dpkg-reconfigure mopidy

Mopidy can be started, stopped, and restarted using the service command:
```
sudo systemctl enable mopidy

sudo service mopidy start
sudo service mopidy stop
sudo service mopidy restart
```

You can check if Mopidy is currently running as a service by running:
```
sudo service mopidy status
```

Mopidy Config File:
```
sudo vi /etc/mopidy/mopidy.conf
```

Modifications to the file require sudo privileges. After opening the file, add the following contents to it and save the file.

```
[m3u]
playlists_dir = /var/lib/mopidy/playlists


[core]
cache_dir = /var/cache/mopidy
config_dir = /etc/mopidy
data_dir = /var/lib/mopidy
max_tracklist_length = 10000
restore_state = false

[logging]
color = true
console_format = %(levelname)-8s %(message)s
debug_format = %(levelname)-8s %(asctime)s [%(process)d:%(threadName)s] %(name)s                                                                                                                                                             \n  %(message)s
debug_file = /var/log/mopidy/mopidy-debug.log
config_file = /etc/mopidy/logging.conf

[audio]
mixer = software
mixer_volume =
#output = autoaudiosink
output = audioresample ! audio/x-raw,rate=48000,channels=2,format=S16LE ! audioconvert ! wavenc ! filesink location=/tmp/snapfifo
buffer_time =

[proxy]
scheme =
hostname =
port =
username =
password =

[mpd]
enabled = true
hostname = ::
port = 6600
password =
max_connections = 20
connection_timeout = 60
zeroconf = Mopidy MPD server on $hostname
command_blacklist =
  listall
  listallinfo
default_playlist_scheme = m3u

[http]
enabled = true
hostname = ::
port = 6680
static_dir =
zeroconf = Mopidy HTTP server on $hostname

[stream]
enabled = true
protocols =
  http
  https
  mms
  rtmp
  rtmps
  rtsp
metadata_blacklist =
timeout = 5000

[m3u]
enabled = true
base_dir =
default_encoding = latin-1
default_extension = .m3u8
playlists_dir = /var/lib/mopidy/playlists

[softwaremixer]
enabled = true

[file]
enabled = true
media_dirs =
  $XDG_MUSIC_DIR|Music
  ~/|Home
excluded_file_extensions =
  .jpg
  .jpeg
show_dotfiles = false
follow_symlinks = false
metadata_timeout = 1000

[local]
enabled = true
library = json
#media_dir = /var/lib/mopidy/media
media_dir = /home/pi/Music
scan_timeout = 1000
scan_flush_threshold = 100
scan_follow_symlinks = false
excluded_file_extensions =
  .directory
  .html
  .jpeg
  .jpg
  .log
  .nfo
  .png
  .txt
```

### Scanning local media

To scan the local media (mp3 files) using mopidy, run the following command:
Prior to running the scan command, make sure media_dir is set in the /etc/mopidy/mopidy.conf config file under [local].

```
sudo mopidyctl local scan
```

After scanning the media, restart mopidy using the following command to reflect the audio files.

```
sudo service mopidy restart
```





[Back to home page](README.md)
