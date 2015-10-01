title: Sticking it to the Cable Company
tags:
  - azureus
  - bittorrent
  - rss
  - tivo
id: 41
categories:
  - Tech
date: 2007-03-13 12:38:34
---

We recently returned our rented cable modem and cable box (neither of which we wanted anyway, we have our own cable modem) and downgraded out TV service to 'basic', which is pretty much the old 2 through 13 of yester-year. Combined with the cable modem charge of $60/month, or total monthly bill should be around $75.

*But we can't watch BattleStar Galactica!*

What to do?

*Step one: BitTorrent plus RSS*

I'm using "Azureus":http://azureus.sourceforge.net/ and one of its RSS plugins, but Windows users might want to try uTorrent. Setting this up is well documented on the internet, so I'll let you figure it out. Oh, "http://tvrss.net/":http://tvrss.net/ will be helpful. I'm using the legacy RSS feeds, but I'm not sure if it matters.

*Step two: "Tivo.NET":http://www.satellite-of-love.org/Default.aspx?Page=TiVoDotNet*

This tool is fantastic. Point it at the directory of your downloaded videos, and it will seemlessly transcode and send them _back_ to your TiVo using "ffmpeg":http://www.offthehill.org/articles/2007/02/17/encoding-psp-video-on-ubuntu-6-10-edgy-linux-part-1\. It runs in the background as a service or a daemon, and it provides a web page for management. I can't imagine a better tool.

If you are on Windows, download the MSI installer, if you are on Linux, download the TivoMono zip file. Here are some getting started tips.

* If you are using the zip file, create a directory before you extract it:

    mkdir Tivomono`
    `cd Tivomono`
    `unzip ../Tivomono*

* When you are editing the 'settings.xml' file for the first time, make sure you put a trailing slash after the install directory, TiVoMono gets confused otherwise:

`<installpath>/home/user/Tivomono/</installpath>`

* Start the server with --verbose:

`mono TivoMono.exe --verbose`

* The admin page is here:

`http://localhost:9033`
