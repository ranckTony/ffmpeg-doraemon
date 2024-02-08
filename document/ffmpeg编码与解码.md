# 编码与解码

```
ffmpeg -i rtmp://localhost:1935/live/lion -c copy -y ./ffmpeg/video/AK_PHAROS1_000003/1ZNBJ4800C006B/video.m3u8
```

```
ffmpeg -y -i lion.mp4  -vcodec copy -acodec copy -vbsf h264_mp4toannexb m3u8\lion.ts

```

```
ffmpeg -y -i lion.mp4  -vcodec copy -acodec copy -vbsf h264_mp4toannexb m3u8\lion.ts
```

```
// mp4 转码成m3u8
ffmpeg -i lion.mp4 -strict -2 -f hls -hls_list_size 0 -hls_time 5 m3u8/lion.m3u8
ffmpeg -re -i ./m3u8/lion.m3u8 -c copy -f  rtmp://localhost:1935/live/lion

```
