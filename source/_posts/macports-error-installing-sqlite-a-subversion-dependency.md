title: 'MacPorts: Error installing sqlite (a Subversion dependency)'
tags:
  - mac
  - macports
  - OS X
  - sqlite
  - subversion
  - unix
id: 76
categories:
  - Tech
date: 2008-09-18 12:26:31
---

This morning I decided to upgrade my Mac to Subversion 1.5 using [MacPorts](http://www.macports.org/). But during the install process, one of the dependencies, _sqlite_, failed with the following error:

`
--->  Building sqlite3 with target all
Error: Target org.macports.build returned: shell command " cd "/opt/local/var/macports/build/_opt_local_var_macports_sources_rsync.macports.org_release_ports_databases_sqlite3/work/sqlite-3.6.2" && gnumake all " returned error 2
Command output: sort -n -b -k 3 opcodes.h |  -f ./mkopcodec.awk >opcodes.c
/bin/sh: -f: command not found
gnumake: *** [opcodes.c] Error 127
`

It took a bit of searching, but it turns out the solution was pretty simple:

`
~$ sudo port clean sqlite3 ; sudo port install sqlite3
Password:
--->  Cleaning sqlite3
--->  Fetching sqlite3
--->  Verifying checksum(s) for sqlite3
--->  Extracting sqlite3
--->  Configuring sqlite3
--->  Building sqlite3 with target all
--->  Staging sqlite3 into destroot
--->  Installing sqlite3 3.6.2_0
--->  Activating sqlite3 3.6.2_0
--->  Cleaning sqlite3
`

Once that was done, I was able to complete the subversion install without trouble.

Overall, MacPorts has been a huge asset, and worked so well that I haven't really needed to learn much about it. If you need unix tools installed on your OS X Mac, I highly recommend it.
