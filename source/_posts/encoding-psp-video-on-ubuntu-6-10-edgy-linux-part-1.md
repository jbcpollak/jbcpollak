title: Encoding PSP Video on Ubuntu 6.10 (Edgy) Linux
id: 36
date: 2007-02-17 14:37:00
tags:
categories:
  - Tech
---

h3\. Part 1 - A better ffmpeg

You would think transcoding video for playback on the PSP would be something trivial to do these days on Linux, with a nice gui frontend and everything, but as is typical, we'll have to wait until approximately when the PSP2 is releases before its easy to do anything with the PSP1 on Linux.

_Anyway_, here's how I got my Linux box (running "Ubuntu":http://www.ubuntu.org) to encode video from my Tivo to my PSP.

Since these write-ups are going to be long, I've broken them into multiple posts. This article deals with compiling and installing ffmpeg with additional codecs Ubuntu didn't ship with.

h3\. The short cut

If you want, you can try skipping the instructions and just install my "ffmpeg deb":http://www.offthehill.org/files/0.cvs20060823-3.1ubuntu2-1_i386.deb, but I haven't added any dependancies to the deb, so it may or may not work, and I haven't tried it. Give it a shot, and if it doesn't install, come back here and try the rest of these instructions.

h3\. Get out your compiler

The ffmpeg that ships with Ubuntu can't encode h264, the preferred format for the PSP. To fix this, I followed "these instructions":http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu-edgy/ (thanks for doing the hard part Paul). I would recommend following that link and following the instructions there, but for people who want the summary, or if that link dies, I've posted what to do below.You'll need GCC installed and the multiverse repositories enabled, and I assume you know your want around Ubuntu fairly well.

<pre>
`
sudo apt-get build-dep ffmpeg

sudo apt-get install liblame-dev libfaad2-dev libfaac-dev \
libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev libx264-dev \
checkinstall build-essential

cd /tmp

apt-get source ffmpeg

cd ffmpeg-*

./configure --enable-gpl --enable-pp --enable-vorbis \
--enable-libogg --enable-a52 --enable-dts \
--enable-dc1394 --enable-libgsm --disable-debug \
--enable-mp3lame --enable-faad --enable-faac \
--enable-xvid --enable-pthreads --enable-x264

make
`
</pre>

When the compile is done, build a new deb file with checkinstall, but before you do that, figure out what version of ffmpeg you already have installed with this:

@apt-cache show ffmpeg | grep Version@

Note down the version, and run checkinstall:

@sudo checkinstall@

When prompted for a version number, enter a newer version number. IE, if you got this:

@3:0.cvs20060823-3.1ubuntu1@

Enter this:

@3:0.cvs20060823-3.1ubuntu2@

This will ensure your version will install over the existing one.

h3\. Check your work

Run @ffmpeg -formats 2>/dev/null | grep h264@

If you see 'DE', that means you can now both Decode and Encode h264:
<pre>
`
pardsbane@Talon:~$ ffmpeg -formats 2>/dev/null | grep h264
 DE h264            raw H264 video format
 DEV DT h264
`
</pre>

h3\. Clean up

Now that the new ffmpeg is installed, you can remove the ffmpeg source code by doing this:
<pre>
`
cd /tmp

rm -rf ffmpeg*
`
</pre>
You can always get it back with @sudo apt-get source ffmpeg@.
