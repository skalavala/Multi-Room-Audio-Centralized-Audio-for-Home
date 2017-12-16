# Enable AirPlay on your Multi-room Audio System

I use shairport-sync (`https://github.com/mikebrady/shairport-sync`) to enable airplay, so that I can stream YouTube and other content straight to my multi-room audio setup.

The set is pretty straight forward, you just need to install `shairport-sync` libraries on your machine using the following command
```
sudo apt-get install shairport-sync
```

After instaling `shairport-sync`, it automatically creates a daemon, that runs when the machine gets restarted. If you want to make sure that happens, run the following commands:

```
sudo systemctl start shairport-sync

sudo systemctl enable shairport-sync

sudo systemctl status shairport-sync

```

After making sure the service runs on your machine, it is time to configure basic settings on how the `shairport-sync` plays the content received from aitplay.

To set the options, you need to modify `shairport-sync.conf` file. The file by default will be in `/etc` folder. Makesure you make a backup, so that it is easy to revert or rollback changes.

In my case, I changed the name as "Multi Room Audio", so that when I click on Airplay from my device, I see that name.

I also set the output_backend to `pipe`. The default setting is `ALSA`, which means, it plays using Advanced Linux Sound Adapter - basically speakers connected to your device. 

In my case, I don't have any speakers connected to my device... I use Snapcast server, where the content will be sent to a file using pipe, and I specify the pipe path as the target. Then my Snapcast server receives the content, and distributes the content to all the connected clients.

The following is the file that is modified to fit my needs. The configuration is fairly easy. Feel free to change the settings to your needs, and once you are done making changes, make sure you restart `shairport-sync`  service using the following command:

```
sudo systemctl restart shairport-sync
```

```
// Sample Configuration File for Shairport Sync
// Commented out settings are generally the defaults, except where noted.

// General Settings
general =
{
        name = "Multi Room Audio"; // This is the name the service will advertise to iTunes. The default is "Shairport Sync on <hostname>"
//      password = "secret"; // leave this commented out if you don't want to require a password
//      interpolation = "basic"; // aka "stuffing". Default is "basic", alternative is "soxr". Use "soxr" only if you have a reasonably fast processor.
        output_backend = "pipe"; // Run "shairport-sync -h" to get a list of all output_backends, e.g. "alsa", "pipe", "stdout". The default is the first one.
//      mdns_backend = "avahi"; // Run "shairport-sync -h" to get a list of all mdns_backends. The default is the first one.
//      port = 5000; // Listen for service requests on this port
//      udp_port_base = 6001; // start allocating UDP ports from this port number when needed
//      udp_port_range = 100; // look for free ports in this number of places, starting at the UDP port base (only three are needed).
//      statistics = "no"; // set to "yes" to print statistics in the log
//      drift = 88; // allow this number of frames of drift away from exact synchronisation before attempting to correct it
//      resync_threshold = 2205; // a synchronisation error greater than this will cause resynchronisation; 0 disables it
//      log_verbosity = 0; // "0" means no debug verbosity, "3" is most verbose.
//  ignore_volume_control = "no"; // set this to "yes" if you want the volume to be at 100% no matter what the source's volume control is set to.
//  volume_range_db = 60 ; // use this to set the range, in dB, you want between the maximum volume and the minimum volume. Range is 30 to 150 dB. Leave it commented out to use mixer's native range.
};

// How to deal with metadata, including artwork
metadata =
{
//      enabled = "no"; // et to yes to get Shairport Sync to solicit metadata from the source and to pass it on via a pipe
//      include_cover_art = "no"; // set to "yes" to get Shairport Sync to solicit cover art from the source and pass it via the pipe. You must also set "enabled" to "yes".
//      pipe_name = "/tmp/shairport-sync-metadata";
};

// Advanced parameters for controlling how a Shairport Sync runs
sessioncontrol =
{
//      run_this_before_play_begins = "/full/path/to/application and args"; // make sure the application has executable permission. It it's a script, include the #!... stuff on the first line
//      run_this_after_play_ends = "/full/path/to/application and args"; // make sure the application has executable permission. It it's a script, include the #!... stuff on the first line
//      wait_for_completion = "no"; // set to "yes" to get Shairport Sync to wait until the "run_this..." applications have terminated before continuing
//      allow_session_interruption = "no"; // set to "yes" to allow another device to interrupt Shairport Sync while it's playing from an existing audio source
//      session_timeout = 120; // wait for this number of seconds after a source disappears before terminating the session and becoming available again.
};

// Back End Settings

// These are parameters for the "alsa" audio back end, the only back end that supports synchronised audio.
alsa =
{
//  output_device = "default"; // the name of the alsa output device. Use "alsamixer" or "aplay" to find out the names of devices, mixers, etc.
//  mixer_control_name = "PCM"; // the name of the mixer to use to adjust output volume. If not specified, volume in adjusted in software.
//  mixer_device = "default"; // the mixer_device default is whatever the output_device is. Normally you wouldn't have to use this.
//  audio_backend_latency_offset = 0; // Set this offset to compensate for a fixed delay in the audio back end. E.g. if the output device delays by 100 ms, set this to -4410.
//  audio_backend_buffer_desired_length = 6615; // If set too small, buffer underflow occurs on low-powered machines. Too long and the response times with software mixer become annoying.
};

// These are parameters for the "pipe" audio back end, a back end that directs raw CD-style audio output to a pipe. No interpolation is done.
pipe =
{
  name = "/tmp/snapfifo"; // there is no default pipe name for the output
//  audio_backend_latency_offset = 0; // Set this offset to compensate for a fixed delay in the audio back end. E.g. if the output device delays by 100 ms, set this to -4410.
//  audio_backend_buffer_desired_length = 44100; // Having started to send audio at the right time, send all subsequent audio this many frames ahead of time, creating a buffer this size.
};

// These are parameters for the "stdout" audio back end, a back end that directs raw CD-style audio output to stdout. No interpolation is done.
stdout =
{
//  audio_backend_latency_offset = 0; // Set this offset to compensate for a fixed delay in the audio back end. E.g. if the output device delays by 100 ms, set this to -4410.
//  audio_backend_buffer_desired_length = 44100; // Having started to send audio at the right time, send all subsequent audio this many frames ahead of time, creating a buffer this size.
};

// These are parameters for the "ao" audio back end. No interpolation is done.
ao =
{
//  audio_backend_latency_offset = 0; // Set this offset to compensate for a fixed delay in the audio back end. E.g. if the output device delays by 100 ms, set this to -4410.
//  audio_backend_buffer_desired_length = 44100; // Having started to send audio at the right time, send all subsequent audio this many frames ahead of time, creating a buffer this size.
};

// The following static latency settings are deprecated -- do not use them for new installations. Shairport Sync now sets latencies automatically.
// To compensate for a delay in the output device please use the alsa/stdio/pipe "audio_backend_latency_offset" setting.

// Static latencies for different sources. These have been estimated from listening tests.
latencies =
{
//      default = 88200; // used for unrecognised sources and for iTunes up to and including iTunes 9.X.
//      itunes = 99400; // used for iTunes 10 or later
//      airplay = 88200;
//      forkedDaapd = 99400;
};

```

After you restart the service, check the status and make sure there are no errors:

```
sudo systemctl status shairport-sync

```

Now, you can stream any content you want to your airplay supported devices.

## additional reading material:

[Snapcast](https://github.com/badaix/snapcast)
[Airplay](https://github.com/badaix/snapcast/blob/master/doc/player_setup.md#airplay)
[shairport-sync](https://github.com/mikebrady/shairport-sync)


[Back to home page](README.md)

