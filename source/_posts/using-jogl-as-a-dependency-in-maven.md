title: Using JOGL as a Dependency in Maven
tags:
  - eclipse
  - java
  - jogl
  - maven
id: 161
categories:
  - Tech
date: 2009-09-08 14:14:04
---

At work, we need to start using JOGL as a dependency of our project, which we build with Maven. JOGL, the Java OpenGL interface, uses platform specific binaries, which introduces some complexity to the build process.

After a brief websearch, I found the appropriately titled [using-jogl-as-dependency-in-maven](http://tastyimportant.blogspot.com/2008/11/using-jogl-as-dependency-in-maven.html), unfortunately, it appears to be a private blog, so I can't see if the information is useful or not.

I did find on [mvnbrowser.com](http://www.mvnbrowser.com/artifacts-browse.html?groupId=net.java.dev.jogl) that jogl-1.1.1-rc6 (as of this writing) is on the dev.java.net Maven2 repository, but I couldn't find a usage guide.

Oh well, I'll keep looking. For now its not a hugely pressing issue, so the one developer who is using has just hacked his Eclipse setup.
