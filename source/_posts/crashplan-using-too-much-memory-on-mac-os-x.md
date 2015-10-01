title: CrashPlan using too much memory on Mac OS X
id: 188
categories:
  - Tech
date: 2010-05-04 15:57:58
tags:
  - backup
---

If you have noticed CrashPlan is using too much memory on your 64 bit Mac, one solution might be to run its server process in 32 bit mode. I've tried this, and so far it hasn't caused any problems, and definitely seems to keep memory usage lower.

This requires a bit of hacking, but its not too terrible.

<!--more-->

Start by opening your 'Terminal' program. You can find it in _/Applications/Utilities/Terminal_

At the command prompt, type this (all on one line):

`sudo nano /Library/LaunchDaemons/com.crashplan.engine.plist`

Find these two lines:

&lt;string&gt;-Dapp=CrashPlanService&lt;/string&gt;
&lt;string&gt;-Xmn10m&lt;/string&gt;

And insert a line so that it now looks like this:

&lt;string&gt;-Dapp=CrashPlanService&lt;/string&gt;
&lt;string&gt;-d32&lt;/string&gt;
&lt;string&gt;-Xmn10m&lt;/string&gt;

_Optional:_ A little further down the file, you will see this line:

&lt;string&gt;-Xmx512m&lt;/string&gt;

You can change that line to be:

&lt;string&gt;-Xmx150m&lt;/string&gt;

This will restrict CrashPlan to _AT MOST_ 150 mb of ram. [According to CrashPlan tech support](https://crashplan.zendesk.com/entries/116068) this is perfectly safe (and you could go even lower if aren't backing up 120gb like I am), but you might need to monitor CrashPlan for out-of-memory errors and such. If you see errors, just change that 150 back to a 512, and everything should be fine.

Now save the file and exit by pressing "Control-O", Enter, then "Control-X".

You are almost done.

The last step is to reload and relaunch CrashPlan with these commands:

`sudo launchctl unload /Library/LaunchDaemons/com.crashplan.engine.plist`
`sudo launchctl load /Library/LaunchDaemons/com.crashplan.engine.plist`

Now CrashPlan should be using much less memory.

**Update:** I neglected to point out _HOW_ to check how much memory Crashplan is using. You can use Activity Monitor to do this, you can find it at _/Applications/Utilities/Activity Monitor_. Look for a process called 'java', started by 'root'. There might be more than one 'java', so you might have to do some digging to figure out which one is Crashplan. I can't find a specific way in Activity Monitor to check this, but one hint is to close any applications you have running and see if other 'java' instances go away. In my case, I normally just have the 'Crashplan' java running.
