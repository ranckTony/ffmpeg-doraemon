# ffmpeg 基础指令

## 下载安装

https://ffmpeg.org

windows 需要设置环境变量

## 指令

```bash
ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...
```

```bash
// -i代表输入文件，-c代表输出文件，copy代表和原视频音视频编码保持一致
ffmpeg -i test.mp4 -c copy test.avi
```

| 指令 | 说明         | 解释 |
| ---- | ------------ | ---- |
| -i   | 输入         |      |
| -c   | 输出         |      |
| copy | 编码保持一致 |      |
| -r   | 视频帧率     |      |
| -s   | 视频分辨率   |      |
| -vb  | 视频码率     |      |
| -ab  | 音频码率     |      |

## 功能

```bash
// 把视频分解成连续的图片
ffmpeg -i video.mpg image%d.jpg
```

```bash
// 图片合成视频
ffmpeg -f image2 -i image%d.jpg video.mpg
```

```bash
// ts合成mp4
ffmpeg -i "concat:input1.ts|input2.ts" -c:v libx264 -c:a copy output.mp4
```

```bash
ffmpeg -i test.avi -c:v h264 -c:a aac -r 25 -s 1280x720 -vb 6000k test.mp4
//-c:v代表指定视频video编码
//-c:a代表指定音频audio编码
//-r代表指定视频帧率frame
//-s代表指定视频分辨率solution
//-vb代表指定视频码率video bitrate
//-ab代表指定音频码率audio bitrate（代码中未指定）

//代码整体意思为：将avi转码为视频编码为h264、音频编码为aac、
//帧率为25fps、分辨率为720p、视频码率为6M的mp4文件。
```

```bash
// 将视频分离成视频和音频
ffmpeg -i test.avi -c:v h264 test.mp4 -c:a aac test.aac
```
