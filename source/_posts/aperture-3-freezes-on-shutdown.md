title: Aperture 3 Freezes on Shutdown
tags:
  - aperture
  - apple
  - database
  - freeze
  - repair
  - photography
id: 236
categories:
  - Art
date: 2011-02-27 21:22:16
---

Ever since I upgraded my main Aperture library from version 2 format to version 3, I have been having a problem when exiting Aperture where it would get stuck "updating information for sharing previews". It would sit forever and never finish. I found this happened whenever I made adjustments to an image, but if I just opened the library and immediately quit, I wouldn't have this problem. I found [many people](http://discussions.info.apple.com/thread.jspa?threadID=2386221&tstart=0) were having the same problem too.

For me, the solution was to use Apertures "Rebuild Library" option, which seems to have fixed the problem.

To do this, follow these steps...

<!--more-->

**First Backup your Library**!!!

Ok, now that you've done that, hold the _Option_ and _Command_ keys down when starting Aperture. You should see a dialog box like this:

[![](http://www.offthehill.org/wp-content/uploads/2011/02/Screen-shot-2011-02-27-at-9.06.28-PM-300x170.png "Aperture First Aid Dialog")](http://www.offthehill.org/wp-content/uploads/2011/02/Screen-shot-2011-02-27-at-9.06.28-PM.png)

First run the "Repair Permissions" option, since it can't hurt. You will need an administrator password to your computer, but the actual repair is pretty painless.

Once that is done, quit Aperture and restart, again holding down the _Option_ and _Command_ keys.

This time, choose "Repair Database". This option is less dangerous than the "Rebuild Database" option. In my case, Aperture immediately detected that there were problems that could only be repaired with the "Rebuild" option, so I allowed it to do the rebuild.

Once the Rebuild was done, which only took a few minutes, everything worked great, and Aperture has been happy every since.
