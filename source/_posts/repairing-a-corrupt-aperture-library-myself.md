title: Repairing a Corrupt Aperture Library Myself
tags:
  - aperture
  - apimportgroup
  - apple
  - approject
  - ilife
  - Leopard
  - library
  - mac
  - OS X
  - raw
  - screen saver
  - screensaver
id: 68
categories:
  - Tech
date: 2008-03-26 20:44:31
---

When I upgraded from a PowerBook to a new MacBook Pro, I used Windows File Sharing (also known as Samba or SMB sharing) to transfer all of my files from one computer to the other via a network, and it looks like that corrupted my Aperture Library.

It look me a few days to realize the problem, but here are a few symptoms I noticed:

1.  Images that were in the library BEFORE the move were not visible in iLife applications (iPhoto, the screen saver, etc). The projects appeared in the listings, but the images themselves were not visible. For example, the screen saver would always say "The selected folder contains no pictures. Please choose a new folder that contains pictures or add images to the folder."
2.  Managed RAW images would not display correctly. I would click on them and the image would appear with a 'loading' message, and then eventually I would see a solid red or maroon background with the text "Unsupported Image Format".

Knowing that the Aperture Libary is just a special directory (called a bundle in Mac-speak), I started poking around inside, comparing a good project (one that I had imported on my new MacBook) to a bad project (one that has been around BEFORE the upgrade).

It turns out that there were directories within the Aperture project directories whose names must have gotten corrupted when I copied the project over from my old computer.

So I wrote a small program to repair the damage.Â If you have a similar problem, feel free to use this script to help recover your library.

**Make sure you close Aperture and BACK UP your Aperture Library before you start!**

Ok, now that you've backed up your library, download the [fixApProject.sh](http://www.offthehill.org/wp-content/uploads/2008/03/fixapproject.sh "fixApProject.sh") script and save it to your home directory.

Open up Terminal.app (Application-&gt;Utilities) and cd **INTO** your Aperture Library.

If your library is in the default location, do it like this:
`cd ~/Pictures/Aperture\ Library.aplibrary/`

Now, assuming you've put `fixApProjech.sh` in your home directory, run the following commands:

`chmod +x ~/fixApProject.sh`

`find . -name "*.approject" -type d -exec ~/fixApProject.sh \{\} \;`
