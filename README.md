# resomate

we can just organize "streaming" as described here: http://www.heidislab.com/tutorials/audio-streaming-with-raspberry-pi-zero-w-and-adafruits-i2s-mic

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

## what doesn't work

I'm trying to start streaming like that: `cvlc alsa://hw:1,0 --sout '#transcode{acodec=ulaw,samerate=8000,ab=128}:rtp{sdp=rtsp://192.168.8.109:8000/front.dsp}'` and getting this error: `VLC is unable to open the MRL 'alsa://hw:1,0'.` probably mic divice should be named somehow differently

