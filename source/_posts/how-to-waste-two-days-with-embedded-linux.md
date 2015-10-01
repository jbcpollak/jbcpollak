title: How to waste two days with Embedded Linux
id: 16
comment: false
categories:
  - Tech
date: 2006-06-27 14:42:00
tags:
---

Have you ever seen this?
<pre>localhost login: root
login: This applet requires root priviledges!</pre>
Chances are, you haven't. Chances are you aren't building a custom home-rolled embedded Gentoo Linux system with busybox.

But if you are, and your using uclibc 0.9.28 or older, make sure you turn on "General setup-&gt;Enable 16-bit UID system calls" in your kernel. Otherwise uclibc will be confused about root's UID, and not thing will work.

For example, 'id' will report the uid as being 4294967295, and getuid() will return -1\. Excellent!

Hopefully this will save some poor shlub two days of debugging work.
