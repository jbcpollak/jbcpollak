title: Installing Lotus Notes 8 on Ubuntu 7.10 Gutsy
tags:
  - fonts
  - install
  - linux
  - lotus
  - notes
  - ubuntu
id: 62
categories:
  - Tech
date: 2007-12-12 17:16:39
---

Ubuntu isn't a supported platform for installing Lotus Notes 8, but the installation is surprisingly easy, once you know a few tricks. Before you begin, make sure you have the proper fonts by installing the "ttf-xfree86-nonfree" package:

`sudo apt-get install ttf-xfree86-nonfree`

If you don't, your fonts will be horribly ugly, and in many places, down right unreadable.

Next, you need to run the regular setup.sh install script:

`sudo ./setup.sh`

The installation creates a directory called ~/lotus, (in your home directory) but owned as root. I guess it assumes you logged in as root to run the install. I had to remove that (you could also probably just chown the directory, but Notes recreates it, so either way works):

`sudo rm ~/lotus -r -d`

I also had to make the binaries readable and executable by every user:

`sudo chmod o+rw /opt/ibm/lotus/notes/*`

Then I ran this (not sure if it is needed, but I saw it on another website):

`sudo chmod -R 755 /etc/lotus`

Now you should be able run Notes and everything should be fine:

`/opt/ibm/lotus/notes/notes`

You should also find an icon under the Applications-&gt;Office menu.

Good luck.
