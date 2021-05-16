# rtmp-to-webrtc

This repo demonstrates a RTMP server that on every RTMP publish makes the audio/video available via WebRTC playback.

## How to use

* `go run *.go`
* Open [http://localhost:8080/](http://localhost:8080/)
* Publish an RTMP feed to `rtmp://localhost:1935/publish/foobar`. It must be H264 and alaw

#### GStreamer
`gst-launch-1.0 videotestsrc ! video/x-raw,format=I420 ! x264enc speed-preset=ultrafast tune=zerolatency key-int-max=20 ! flvmux name=flvmux ! rtmpsink location=rtmp://localhost:1935/publish/foobar audiotestsrc ! alawenc ! flvmux.`

#### OBS
![](https://user-images.githubusercontent.com/49592759/118397671-c1036f00-b687-11eb-85cc-984a0331e8fe.png)
