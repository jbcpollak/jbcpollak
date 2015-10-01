title: Recovering a Terastation Live From Scratch
tags:
  - buffalo
  - linux
  - raid
  - terastation
  - terastation live
id: 94
categories:
  - Tech
date: 2008-11-04 03:11:17
---

I recently ordered a Buffalo Terastation Live from eCost for around $260, which seemed like a pretty darn good deal. Of course, it was 'Factory Reconditioned', whatever that meant...

...Turns out that means it arrives in a plain brown box, with no manual, and completely hosed. I naively thought I'd be able to plug it in, browse to the admin website, set it up, and in a few minutes I'd be copying all my data to my new RAID system. Nope.

To make a long story short, after many "E04" boot errors and all sorts of other crap, I ended up ripping all the disks out of the sucker, deleting the partition tables on them, and slapping them back it.

It looks like once that was done, the Terastation would [boot over TFTP](http://buffalo.nas-central.org/index.php/Revive_your_arm9_box_from_scratch) and I could then do a [firmware update](http://www.buffalotech.com/support/downloads).

Unfortunately, these seems to be a problem with the zip extractor on the version of the software my Terastation originally shipped with, so it wasn't able to extract the /boot/hddrootfs.img file (which is really a zip). What is supposed to happen is that this file gets extracted to /boot/hddrootfs.buffalo.updated, which is a tar.gz image of the root file system. On boot, if that file exists, it is used to overwrite the root file system, but since the boot system couldn't extract the zip, I was stuck.

My solution was to extract the hddrootfs.buffalo.updated file onto a ext3 formatted USB stick, mount the stick on the Terastation, and copy it to /boot. I had to use a USB stick because the Terastation didn't have an of the standard file transfer apps (ftp, tftp, scp, etc), or at least, I couldn't find them. You'll need root console access to do this, so make sure you have a copy of the acp_commander.jar file.

The only trick is you'll need the password for the zip file, which I found [here](http://buffalo.nas-central.org/index.php?title=Create_a_custom_firmware_image#Collected_passwords "Create_a_custom_firmware_image#Collected_passwords").

I found the [Resetting To English](http://buffalo.nas-central.org/index.php/TeraStation:_Resetting_to_English) invaluable as well, because once the new firmware was installed, the damn thing started up in Japanese!

**Update:** Everything was going swimmingly, and I had been able to setup the box and have it start building a RAID5 Array across all four disks. A few minutes after the RAID started building, the website stopped working, and the next morning, when the RAID was finished building, the box was completely inaccessible.

Now the box reboots to Emergency Mode. When I try and flash the device with firmware again, a few minutes after the disk starts formatting the box throws off all sorts of bells and alarms and displays "DISK1 signature fail". I called Buffalo Tech support (yeah 24/7 tech support!), and the tech support guy walked me through a firmware update again, and when I got to the "DISK1 signature fail" for a second time, he disappeared for about 5 minutes. I started to think he had hung up on me, but I stayed on the line and eventually came back and told me I'd be getting RMA information in the mail.

So now I've got to pay to ship the sucker back and I'll get a new one. Ugh.

Oh well, despite all that, I'm pretty excited by the product and I'm looking forward to finally getting it up and running.
