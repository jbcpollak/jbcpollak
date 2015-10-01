title: 'Solved: Mac OS X Locks-Up When Waking from Screensaver'
tags:
  - keychain
  - Leopard
  - mac
  - OS X
  - snow leopard
  - ssh keychain
id: 172
categories:
  - Tech
date: 2010-01-16 12:48:31
---

**The Problem**

Frequently, say, one out of 10 times, when I try and log back into my Mac from the screensaver, or when I wake it from sleeping, I will get a spinning beachball and be unable to type my password. Other times I will be able to log in, but I am prompted to enter my password multiple times for various applications, and invariably one of them (usually gconsync) will get stuck after I enter my password with a spinning beach ball. I can still use most applications, but application that needs keychain authorization locks up.

I happen to be using a very handy tool called SSHKeychain, which turned out to be the culprit.

If you are using SSHKeychain, this post will walk you through fixing the unstable-wake-from-screensaver, and also solves the problem of having to type your keychain password  3-5 times when I returned to my computer.

<!--more-->

**The Solution**

1.  On your Mac's menubar, near the clock, look for SSHKeychain, it looks like a keyring with three keys.
2.  If you have that, click the keyring, and choose "Preferences..."
3.  On the security tab, make sure "Use custom security settings" is checked.
4.  Set all the drop downs to "No action"
5.  Close the window and you are all set.
[caption id="attachment_177" align="alignnone" width="555" caption="The SSHKeychain Security Settings Dialog"][![](http://www.offthehill.org/wp-content/uploads/2010/01/SSHKeychain-Security-Settings.png "SSHKeychain Security Settings")](http://www.offthehill.org/wp-content/uploads/2010/01/SSHKeychain-Security-Settings.png)[/caption]

**Note**

This is a bit more insecure, since your keychain will be unlocked, but its protected by the password for your screensaver (you do have a password on your screensaver, right?). There may be a security hole if people gain shell access to your computer, I'm not sure if the keychain memory is encrypted, but overall I think your keychain information is still pretty safe.
