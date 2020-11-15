# resomate

we can just organize "streaming" as described here: http://www.heidislab.com/tutorials/audio-streaming-with-raspberry-pi-zero-w-and-adafruits-i2s-mic

this article I also found userful: http://iltabiai.github.io/2018/03/17/rpi-stream.html

## what has to be installed on raspberry

pulseaudio: `sudo apt-get install alsa-base pulseaudio`

vlc: `sudo apt-get install vlc`

## what works so far

### audio recording to wav file

`arecord --device=hw:1,0 --format S16_LE --rate 44100 -c1 test.wav -V mono`

```
cat ~/.asoundrc 
pcm.!default {
       type hw
       card 0
}

ctl.!default {
        type hw
        card 0
}
```

### starting the streaming

first check where the mic is: `aplay -l`

#### stream 

`cvlc -vvv alsa://hw:1,0 --sout  '#transcode{acodec=mp3,ab=128}:rtp{mux=ts,dst=192.168.8.109,sdp=sap}'`

#### listen to the stream

`cvlc rtp://192.168.8.109`

