title: MacFUSE for 64-bit Snow Leopard
tags:
  - 64bit
  - beta
  - compile
  - mac
  - macfuse
  - OS X
  - snow leopard
  - truecrypt
  - tuxera
id: 220
categories:
  - Tech
date: 2010-12-31 11:01:39
---

**UPDATE**: _**OS X Lion** users, according to [this thread](http://groups.google.com/group/macfuse/browse_thread/thread/217a91cb665dfab5 "this thread") there is a new project called OSXFUSE that picks up where MacFuse left off. The project incorporates the source code below and already supports OS X Lion natively. The project is just getting started, but a beta binary release is promised in the next few days. You can find more information at the [project homepage](http://osxfuse.github.com/ "project homepage") (not online yet) or find the source code on [github](https://github.com/osxfuse "github")._

### So What Is The Story?

If you would like to be able to use MacFUSE on 64-bit Snow Leopard, you may have noticed a lot of mis-information on the net. In short, all of the latest official MacFUSE releases, including both **2.0.3** and the **2.1.7 beta** are not compatible with 64-bit Snow Leopard.  My understanding is that these releases will work with 64-bit Leopard, or with 32 bit Snow Leopard, but I cannot confirm this.

This article describes the current situation, and provides usable binary and source packages to download.

<!--more-->

A company called Tuxera has made the necessary modifications to MacFUSE, and has published the source code as an un-official beta they call **2.1.9**. As of write now, the best source of information for this build can be found at this MacFUSE Google Groups thread:

[Unofficial MacFUSE 2.1.7 release for Mac OS X 10.6 (32/64-bit)](http://groups.google.com/group/macfuse/t/9e5ec92932f27f46)

### Just Give Me Something To Install!

If you trust me and would just like a working version of MacFUSE to install, you can download an image I compiled myself: [macfuse-core-10.5-2.1.9.zip](http://www.offthehill.org/wp-content/uploads/2010/12/macfuse-core-10.5-2.1.9.zip).

### I Want To Compile It Myself

You can download the original source code [directly from Tuxera](http://www.tuxera.com/mac/macfuse-rebel-2.1.9-src.tar.bz2) or from [my local mirror](http://www.offthehill.org/wp-content/uploads/2010/12/macfuse-rebel-2.1.9-src.tar.bz2).

You will obviously need XCode installed to compile MacFUSE. Once you have downloaded the source, open a terminal and run the following commands:

`Downloads $ cd macfuse-rebel-2.1.9
macfuse-rebel-2.1.9 $ cd core/
core $ ./macfuse_buildtool.sh -t smalldist `

It generates a directory in the /tmp directory called "macfuse-core-10.5-2.1.9". Inside this directory is a .pkg file called "MacFUSE Core.pkg". Just double click this file to install, and MacFUSE will be installed. Then, once installed, you can install TrueCrypt or whatever Fuse implementation you need, and it should work fine.

### The Standard Disclaimer

I make no claims about how stable this code is, and I have no idea about anything in the MacFUSE internals, so please report any problems you have with this version of the code to the [MacFUSE Google Group](http://groups.google.com/group/macfuse).
