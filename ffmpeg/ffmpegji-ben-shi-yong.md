### apt-get安装ffmpeg

```
sudo add-apt-repository ppa:kirillshkrogalev/ffmpeg-next 
sudo apt-get update 
sudo apt-get install ffmpeg
sudo apt-get install libavformat-dev libswscale-dev libx264-dev libx265-dev libavfilter-dev libavdevice-dev
```

### 源码安装ffmpeg

```
sudo apt-get install libvorbis-dev libmp3lame-dev libfdk-aac-dev
tar xvf ffmpeg-3.2.1.tar.bz2 
cd ffmpeg-3.2.1
./configure --enable-libx264 --enable-libx265 --enable-libfdk-aac --enable-libvorbis --enable-librtmp --enable-libmp3lame --enable-libtheora --enable-gpl --enable-nonfree --disable-yasm
```

### 多音轨转码

```
ffmpeg -re -i King.Of.Comedy.1999.mkv -map 0:v -vcodec libx264 -map 0:a:1 -acodec aac -strict -2 -y -f flv rtmp://10.10.10.188/hls/test
```

### srt转webvtt

```
ffmpeg -i pbs5e6.srt -map s -y index.vtt
```

### 编辑mp4文件

可以修改original\_network\_id、transport\_stream\_id、service\_id等等，streamid代表音视频pid，可以修改video pid和audio pid

```
ffmpeg -i input.mp4 -vcodec libx264 -strict -2 -acodec aac -streamid 1:2595 -
mpegts_original_network_id 0x1122 -mpegts_transport_stream_id 0x3344 -
mpegts_service_id 0x02 -mpegts_pmt_start_pid 0x0A20 -mpegts_start_pid
0x0A21 -metadata service_provider="yakir" -metadata service_name="yakir"
-bsf h264_mp4toannexb -f mpegts output.ts
```

### m3u8切片

```
ffmpeg -re -i input.mp4 -vcodec libx264 -strict -2 -acodec aac -hls_list_size 0 -f hls input/index.m3u8
```

如果音视频都是copy的话，去掉re参数可以快速进行切片

### 分辨率及视频比例设置

```
ffmpeg -i input.mp4 -vf scale=1280x720,setdar=16:9 output
```

### udp转码切片

```
ffmpeg -i "udp://@225.0.0.100:9001?buffer_size=1000000&fifo_size=1000000" -vcodec libx264 -acodec aac -strict -2 -r 25 -preset ultrafast -crf 23 -vf w3fdif -f flv -y rtmp://10.0.0.100:1935/live/xugaoxiang/index
```



