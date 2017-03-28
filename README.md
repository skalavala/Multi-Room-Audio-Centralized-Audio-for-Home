# Wireless Multi-Room Audio System For Home

I have always wanted to have a centralized audio system for my home, since my home is not currently wired for that, I decided to maky my own centralized audio system using nothing but Raspberry Pi's and some {cheap} bluetooth speakers from amazon and leverage any old speakers lying at home that can be plugged into a 3.5mm audio jack. I documented all the steps here, for those who want to do the same.

I use Mopidy, Snapcast server and client software(s) to achieve this functionality. The Mopidy is just a media player, and the output of the mopidy is directed to a pipe, where the Snapcast server is listening to. When any audio/music content is streamed to that pipe, Snapcast server receives the media, and broascasts to all of it's clients (snapcast clients) accordingly.

The ideal set up would be to install Mopidy, Snapcast Server and Snapcast client on one Raspberry Pi, and use other Raspberry Pis as clients - where it will only have Snapclient software running on it.

All Raspberry Pis are connected to corresponding speakers (possibly in each room) using 3.5mm audio jack. In my case, those Raspberry Pis are either behind the couch, or under the bed hidden, but always powered. The bluetooth speakers can be powered from Raspberry Pi itself - just make sure you have the right power supply that has at least 2.5 amps.

1. [Install Mopidy](https://github.com/skalavala/Multi-Room-Audio-Centralized-Audio-for-Home/blob/master/Install%20Mopidy.md)

2. [Install Snapcast Server](https://github.com/skalavala/Multi-Room-Audio-Centralized-Audio-for-Home/blob/master/Install%20Snapcast%20Server.md)

3. [Install Snapcast client on each Raspberry Pi](https://github.com/skalavala/Multi-Room-Audio-Centralized-Audio-for-Home/blob/master/Install%20Snapcast%20Client.md)

4. [Setting up PulseAudio](https://github.com/skalavala/Multi-Room-Audio-Centralized-Audio-for-Home/blob/master/Setup%20Pulseaudio.md)

All set! That's all there is to it! Enjoy the whole house audio system, play music, connect to home assistant, and make announcements, notifications, write a program that pulls headlines/breaking news from news sites; call amazon polly and play the tts audio, or even connect to online radio channels! Sky is the limit! 

Good luck!
:smile: 

Special thanks to [@mgolisch](https://github.com/mgolisch) , [@happyleavesaoc](https://github.com/happyleavesaoc)
