title: 'Mozy for Mac: database locked!'
tags:
  - mac
  - mozy
  - online backup
id: 153
categories:
  - Tech
date: 2009-07-07 12:52:28
---

I've been using Mozy on my Mac for a while, but I'm strongly considering canceling my subscription. It took nearly a month to get the backup complete. Once it was, it ran successfully for about a month, but now I get errors like this in the logs, and the backup never finishes successfully:

`
2009-07-07 13:26:04.668 MozyBackup[7933:3603] WRN (updater) Error adding changes to scan cache: database is locked
2009-07-07 13:27:04.736 MozyBackup[7933:3603] WRN (updater) Error adding changes to scan cache: database is locked
2009-07-07 13:28:06.563 MozyBackup[7933:3603] WRN (updater) Error adding changes to scan cache: database is locked
2009-07-07 13:29:06.670 MozyBackup[7933:3603] WRN (updater) Error adding changes to scan cache: database is locked
2009-07-07 13:30:07.005 MozyBackup[7933:3603] WRN (updater) Error adding changes to scan cache: database is locked`

I found [this blog post](http://defenestrated.typepad.com/defenestrated/2008/08/mozy-for-mac--.html), but I seem to have a slightly different issue, even though the errors listed are the same. I'm not using any backup sets at all, instead, I'm only having Mozy backup my home-directory (with specific exclusions setup, to avoid backing up a few virtual machines).

Granted, I have 300,000 files totaling over 100 gb to keep backed up, but I don't modify many files on any given day. If this is too much data for Mozy to handle, the client should let the user know!
