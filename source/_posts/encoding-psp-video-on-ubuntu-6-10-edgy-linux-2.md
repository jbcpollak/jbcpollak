title: Tivo Video on your PSP with Linux
id: 37
date: 2007-02-17 15:02:34
tags:
categories:
  - Tech
---

Tivos are great for recording video at home and Sony PSPs are great for watching video away from home. But how do you take you Tivo videos on the road with you? This guide will show you how.

h3\. Required Software

First you'll need to get "ffmpeg installed correctly":http://www.offthehill.org/articles/2007/02/17/encoding-psp-video-on-ubuntu-6-10-edgy-linux-part-1, before you can start encoding video for you PSP or iPod.

You also need "tivodecode":http://tivodecode.sourceforge.net/. This is a simple little tool that will strip the tivo encryption from your .tivo files. I recommend you put it in ~/bin, but anywhere you like is fine. You'll need to adjust my script (later down) if you put it somewhere else.

h3\. Helper Scripts

I've written two scripts which this guide uses: "pspenc":http://www.offthehill.org/files/pspenc and "tivo2psp":http://www.offthehill.org/files/tivo2psp. pspenc will take any file ffmpeg understands and convert it into a format playable on your PSP. tivo2psp goes one step farther by downloading a file straight from the tivo and sending it to pspenc.

Download both files and put them in ~/bin/, or wherever you put tivodecode. Make sure wherever you put them is on your $PATH.

h3\. MAK daddy

Now you'll need to find your Tivo's MAK (meda access key).

Go to your TiVo box and go to TiVo Central. From TiVo Central choose Messages & Settings to open the Messages & Settings menu on your TV screen. Next, choose Account & System Information to open the Account & System Information menu on your TV screen. Choose Media Access Key to view your Media Access Key.

Put the MAK into ~/.tivodecode_mak:

  cat XXXXXXXXX > ~/.tivodecode_mak

Doing this is easier than setting your mak each time you run tivodecode, but if you have multiple Tivos, this might not work for you.

h3\. Getting the videos off the TiVo

Unfortunately, I haven't found a good solution to this. If you are on Windows, you can use Tivo Desktop and if you are on a Mac, you can use "tdm":http://tdm.sourceforge.net/. If you are using Linux, you currently have to do it the hardway. There is also "Galleon":http://galleon.tv, but I find it clunky to use and it seems to be a dead project now.

I'm using a combination of my web browser and curl (through my tivo2psp script) to access Tivo's built in webserver to download the files directly. All you need to do is browse to https://<your-tivos-ip-address>/ and log in with the username tivo and your MAK as the password.

From there, find the show you want to watch, and right click. Choose 'copy link location' to copy the URL to the clipboard.

h3\. Running The Conversion

This is the last, and possibly the easiest step. Open up your terminal window and type "tivo2psp <url>" where <url> is the pasted url you just copied. Press enter, and the script should do it thing. Sit back and wait, and in an hour you should have a video file for your psp. You'll want to rename it, unfortunately the Tivo doesn't provide sensible filenames for your downloads.
