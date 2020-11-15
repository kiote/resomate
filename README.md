# resomate

we can just organize "streaming" as described here: http://www.heidislab.com/tutorials/audio-streaming-with-raspberry-pi-zero-w-and-adafruits-i2s-mic

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
