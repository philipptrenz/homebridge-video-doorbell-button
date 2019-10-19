# homebridge-video-foorbell

ffmpeg plugin for [Homebridge](https://github.com/nfarina/homebridge)

## Installation

1. Install ffmpeg on your Raspberry
2. Install this plugin using:

```
npm install -g npm i homebridge-video-doorbell-button --unsafe-perm
```

3. Edit `config.json` and add the camera and add Mi/Aqara Button.
4. Run Homebridge
5. Add extra camera accessories in Home app. The setup code is the same as homebridge.

### config.json example

```
{
  "platform": "Video-DoorbellV2",
  "buttonSid": "158d00029088e3",
  "camera": {
    "name": "Домофон",
    "videoConfig": {
      "source": "-rtsp_transport tcp -i rtsp://ip-addres/unicast",
      "stillImageSource": "-i rtsp://ip-addres/unicast -vframes 1 -r 1",
      "maxStreams": 2,
      "maxWidth": 1280,
      "maxHeight": 720,
      "maxBitrate": 1600,
      "maxFPS": 20,
      "audio": true,
      "vcodec": "h264_omx"
    }
  },
  "lock": {
    "name": "Lock mechanism"
  },
  "gpio": 7,
  "motion": true
}
```

### buttonSid

sid for Mi or Aqara switch.

### gpio

GPIO number, to trigger plug to ground.

### motion

virtual motion accessory and switch for trigger motion.

Incidentally, check [iSpyConnect's camera database](https://www.ispyconnect.com/sources.aspx) to find likely protocols and URLs to try with your camera.
