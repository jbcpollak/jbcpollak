title: Uninstalled .cab files Wasting Space on Windows Mobile 6
tags:
  - cab
  - missing sync
  - pocket pc
  - windows mobile
  - wing
id: 59
categories:
  - Tech
date: 2007-11-14 20:13:31
---

After about a month and a half, my T-Mobile Wing has started to run out of  free storage space. Whenever I searched the built in storage for large files, nothing ever turned up, but then I stumbled upon something: Missing Sync for Windows Mobile was putting **all** of my .cab files into /Windows/AppMgr/Install, regardless of whether I told it to put the cab on my storage card or not.

Quite a few of those cabs never got installed for whatever reason, so they were just sitting there, unused, taking us space. I just deleted them. So if you've ever installed cabs to your Windows Mobile device, but the program never got installed, check the /Windows/AppMgr/Install directory, they might just be sitting around taking up space.
