title: "Use a Mac to Repair a Sansa Clip with the 'Not enough space for Music DB, please free 30 mb' error"
tags:
  - clip
  - format
  - mac
  - partition
  - sansa
id: 196
categories:
  - Tech
date: 2010-09-28 21:45:19
---

First of all, the fact that you need to leave free space on your Clip is the most irritating issue I've ever seen on a modern electronics device. I'm sure there are thousands of people out there who have thrown their Clips in the garbage because of this.

Anyway, here is the situation:

You've got the "_Not enough space for Music DB, please free 30 mb_" message on your Sansa Clip.
You have a Mac

Read on for the fix.

<!--more-->

Here is the fix:

Open Disk Utility
Click on the Sansa Clip listing on the left
- Not the disk itself, the DEVICE.
Click the 'Partition' tab
Under Volume Scheme, choose '1 Partition'
Click the 'Options...' button
Choose 'Master Boot Record', then click ok _(this is IMPORTANT!)_
Click the drop down next to 'Format:' and choose "MS-DOS (FAT)"
Click Apply

When this is complete, you can eject the disk if needed, and your clip should be back to normal.

I found that by default the formatting process doesn't use the 'Master Boot Record' partition table system, so even though I had formatted the disk repeatedly, it wasn't working correctly till I manually specified to use an MBR.
