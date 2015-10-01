title: Fixing Delete and Backspace in OS X Terminal
tags:
  - backspace
  - bsd
  - delete
  - linux
  - mac
  - OS X
  - ssh
  - terminal
id: 84
categories:
  - Tech
date: 2008-09-25 11:24:28
---

I'm constantly having trouble with getting the backspace and delete keys to work properly in OS X. Whenever it works right on the Mac, one or the other key is broken when I Â SSH to a Linux or FreeBSD box.

After some searching, I've found this solution, which seems to be working:

1.  First, got to the Terminal menu, and choose _Preferences..._Â Under the _Settings_Â section, choose the _Advanced_Â tab. Make sure _Delete sends Ctrl-H_Â is **checked**.
2.  Then, in the same window, go to the _Keyboard_ tab (right next to _Advanced_). Find the line for _forward delete_, and set it to this value:
`\033[3~`
3.  Lastly, you need to run the following line at the terminal. The trick with the line below though is that you need to type the ^H byÂ pressing Control-V and then Control-H. You **can not**Â just cut and paste the line below, you need to type it:
`echo -e "stty erase Ë†H" >> ~/.bash_profile`
Now you can restart Terminal, and your backspace and delete should work correctly everywhere!

For further reading on this topic check out these two links:

*   [Linux Backspace/Delete mini-HOWTO](http://www.tldp.org/HOWTO/BackspaceDelete/)
*   [Consistent BackSpace and Delete Configuration](http://www.ibb.net/~anne/keyboard/)

This problem, and various solutions are documented all over the net, but I found and used [this](http://fredericiana.com/2006/10/16/fixing-backspace-and-delete-for-ssh-in-os-xs-terminalapp/) page most recently.