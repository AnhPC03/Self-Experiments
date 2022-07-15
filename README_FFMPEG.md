# Install ffmpeg version 4 and make default

If you get the following error or something relevant when working with opencv
```bash
/usr/bin/ld: warning: libavcodec.so.58, needed by ..../libopencv_videoio.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libavformat.so.58, needed by ..../libopencv_videoio.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libavutil.so.56, needed by ..../libopencv_videoio.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libswscale.so.5, needed by ..../libopencv_videoio.so, not found (try using -rpath or -rpath-link)
```
This is because you are using the other ffmpeg version than expected (version 4.)
1. First, uninstall old ffmpeg
```bash
sudo apt remove --purge --auto-remove -y ffmpeg
```
2. Install ffmpeg version 4
```bash
sudo add-apt-repository ppa:savoury1/ffmpeg4
sudo apt-get update
sudo apt-get install ffmpeg
```

Check again with command (the output should be greater than version 4.0)
```bash
ffmpeg
```
And then you will see the version of `libavcodec`, `libavformat`, `libavutil`, `libswscale` as expected in the above errors