title: Enable Built-in OS X / Google Address Syncing
tags:
  - address book
  - android
  - contacts
  - g1
  - gmail
  - google
  - mac
  - OS X
  - t-mobile g1
id: 92
categories:
  - Tech
date: 2008-10-22 14:39:53
---

It turns out that ever since the IPhone came out, IPhone users have been able to sync their Mac Address Books with GMail. But that privilege isn't extended to anyone else. Why every user can sync with Exchange and Yahoo!, but only IPhone users can sync to Google is beyond me.

Anyway, luckily there is a workaround, so if you are a T-Mobile G1 (Android) early adopter like me, you don't have to update your GMail Contact list from scratch.

You can read how to do it on [Lifehacker](http://lifehacker.com/393855/enable-google-contact-sync-without-an-iphone-or-ipod-touch), but the instructions are pretty simple if you are familiar with Mac property files:

1.  If you don't have the Property List Editor (it comes with XCode, which is free, but a very large download) installed, download theÂ [shareware PlistEdit Pro](http://www.apple.com/downloads/macosx/development_tools/plisteditpro.html)Â and install.
2.  Open upÂ `~/Library/Preferences/com.apple.iPod.plist`Â and save a backup copy of it. Then, expand the tree to reveal "Family ID." Change that value toÂ `10001`. My 5th-gen IPod had the value `6` originally.
3.  Save your changes. Launch Address Book and open the Preference pane. The Google contact sync option will be staring right at you.
<div>I've heard this doesn't work for everyone, but it seems to be working great for me. The only issue I have right now is that some of my contact's information isn't making it to Google. For example, some contacts names are missing, while other's phone numbers are missing. I can't explain it, but since most contacts have synced ok, I'll live with it for now.</div>
