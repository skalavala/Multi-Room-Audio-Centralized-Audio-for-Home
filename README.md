# Wireless Multi-Room Audio System For Home

I have always wanted to have a centralized audio system for my home. Since my home is currently not wired for that, I decided to maky my own "wireless" centralized audio system using nothing but Raspberry Pi's and some {cheap} bluetooth speakers from amazon and leverage any old speakers lying at home that can be plugged into a 3.5mm audio jack. It works great, and I enjoy the whole house music system thoroughly. I documented all the steps that I did at my home, hoping it will come in handy for myself later, or to others who is thinking of doing the same.

## Basic Hardware:

<table>
  <tr>
    <td>
<a href="http://amzn.to/2p9RVhQ"><img src="https://raw.githubusercontent.com/skalavala/skalavala.github.io/master/images/raspberry-pi3.jpg" alt="Raspberry Pi 3" /></a>
    </td>
    <td>
<a href="https://amzn.to/2Vj7iAW"><img src="https://raw.githubusercontent.com/skalavala/skalavala.github.io/master/images/audio-cable.jpg" alt="3.5mm Audio Cable" /></a>
    </td>
    <td>
<a href="http://amzn.to/2pU2V1Y"><img src="https://raw.githubusercontent.com/skalavala/skalavala.github.io/master/images/bluetooth-speaker.jpg" alt="Bluetooth Speakers" /></a>
    </td>
  </tr>
  <tr>
    <td>Raspberry Pi 3</td>
    <td>3.5mm Audio Cable</td>
    <td>Portable Speakers</td>
  </tr>
</table>

## Software Components 
I used Mopidy, Snapcast server and client software(s) to achieve this functionality. The Mopidy is just a media player, and the output of the mopidy is directed to a pipe, where the Snapcast server is listening to. When any audio/music content is streamed to that pipe, Snapcast server receives the media, and broascasts to all of it's clients (snapcast clients) accordingly.

If you are not familiar with Mopidy, I highly recommend you to read all about it here --> [Mopidy Docs](https://docs.mopidy.com/en/latest/) or [Mopidy Home Page](https://www.mopidy.com/)

The ideal set up would be to install Mopidy, Snapcast Server and Snapcast client on one Raspberry Pi, and use other Raspberry Pis as clients - where it will only have Snapclient software running on it.

All Raspberry Pis are connected to corresponding speakers (possibly in each room) using 3.5mm audio jack. In my case, those Raspberry Pis are either behind the couch, or under the bed hidden, but always powered. The bluetooth speakers can be powered from Raspberry Pi itself - just make sure you have the right power supply that has at least 2.5 amps.

1. [Install Mopidy](https://github.com/skalavala/Multi-Room-Audio-Centralized-Audio-for-Home/blob/master/Install%20Mopidy.md)

2. [Install Snapcast Server](https://github.com/skalavala/Multi-Room-Audio-Centralized-Audio-for-Home/blob/master/Install%20Snapcast%20Server.md)

3. [Install Snapcast client on each Raspberry Pi](https://github.com/skalavala/Multi-Room-Audio-Centralized-Audio-for-Home/blob/master/Install%20Snapcast%20Client.md)

4. [Setting up PulseAudio](https://github.com/skalavala/Multi-Room-Audio-Centralized-Audio-for-Home/blob/master/Setup%20Pulseaudio.md)

5. [Setting Snapcast Client Names](https://github.com/skalavala/Multi-Room-Audio-Centralized-Audio-for-Home/blob/master/Naming%20Clients.md)  

6. **Optional** [Enable Airplay](https://github.com/skalavala/Multi-Room-Audio-Centralized-Audio-for-Home/blob/master/airplay.md)

7. **Optional** [Setup Virtual Sound Card on VMWare ESXi 6.0 or Above](https://github.com/skalavala/Multi-Room-Audio-Centralized-Audio-for-Home/blob/master/vmware.md)

All set! That's all there is to it! Enjoy the whole house audio system, play music, connect to home assistant, and make announcements, notifications, write a program that pulls headlines/breaking news from news sites; call amazon polly and play the tts audio, or even connect to online radio channels! Sky is the limit! 

Optionally, you can also install Mopidy Web Extensions and access Spotify playlists. This Mopidy (mpd) can also be integrated into [Home Assistant (HA)](http://www.home-assistant.io) and see all the media players on the dashboard. Currently, HA only supports older vesions of Snapcast server and clients. 

Good luck!
:smile:

Special thanks to [@mgolisch](https://github.com/mgolisch), [@happyleavesaoc](https://github.com/happyleavesaoc)


![Big Picture](https://raw.githubusercontent.com/skalavala/smarthome/master/images/MultiroomAudioSystem-Kalavala.jpg)

