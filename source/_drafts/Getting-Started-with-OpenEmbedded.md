title: Getting Started with OpenEmbedded
tags:
  - embedded
  - linux
  - open embedded
  - open moko
id: 66
categories:
  - Tech
---

I've been experimenting with OpenEmbedded meta-distribution lately, trying to build a uclibc distribution to install on a Soekris board.

Before you begin, I highly recommend you read the "OE and Your Distro":http://www.openembedded.org/wiki/OEandYourDistro page. There are a good number of detail issues related to building with OpenEmbedded on your host operating system of choice. For example, there may be issues with Ubuntu's default use of dash instead of bash, and this page explains how to correct it.

Once you've got your host environment setup correctly, you can follow the "getting started directions":http://www.openembedded.org/wiki/GettingStarted . This page has a throughout tutorial on how to get started and build your first image. I recommend following the instructions closely.

As a first sanity check, change only what the getting started guide tells you to in your local.conf file, and nothing else. Don't get fancy and change your DISTRO, TARGET_OS, or MACHINE settings for you first run.