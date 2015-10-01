title: OS X Slow Login and Terminal Startup
tags:
  - apple
  - iterm
  - ldap
  - mac
  - OS X
  - terminal
id: 21
categories:
  - Tech
date: 2006-10-19 08:14:11
---

 A while back my Mac starting taking really long to wake from sleep. I'd get a spinning beachball (SBOD) for 30 seconds before the login screen would appear, and it would take a while for my password to authenticate.

I also noticed that when I started Terminal or iTerm, it took forever. First it took forever for the window to even appear, and then when it did the "last login" line would appear, pause, and then about 30 seconds or more later, the prompt would finally appear and you could use the terminal normally.

I searched the web all over for help on this and did a few maintenance things, but nothing helped. One person online found the solution to their problem by running 'top' and watching the login process, but nothing out of the ordinary was happening on my machine.

Then it dawned on me: The exact same thing happens on my Linux machines when the LDAP settings aren't working correctly, because the LDAP timeout defaults to around 30 seconds.

So I started Directory Access, and sure enough, there was an LDAP server listed under the Authentication tab. I had recently added the same server for the Contacts tab, but I didn't expect or want to use it for authentication.

Removing the LDAP server cleared up my slow logins and terminal starts, so make sure you check Directory Access if you are having a similar problem.
