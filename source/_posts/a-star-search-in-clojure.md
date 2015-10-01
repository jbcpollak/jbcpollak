title: A-Star Search in Clojure
tags:
  - 'a*'
  - a-star
  - astar
  - astar-in-clojure
  - clojure
  - functional programming
  - java
  - maven
id: 167
categories:
  - Tech
date: 2009-10-16 16:45:20
---

I wanted to refresh my knowledge of functional programming, A-Star search, and I figured learning [Clojure](http://www.clojure.org "Clojure homepage") at the same time couldn't hurt. I figured I'd do all three at once, and throw in a health dose of Maven and Java at the same time.

This project was intended to:

1.  Refresh myself on how to do functional programming
2.  Refresh my knowledge of A* search
3.  Help me learn Clojure
4.  Demonstrate Java interoperating with Clojure
5.  Demonstrate Maven as a viable build system for Clojure
[Download The Demo Here](http://www.offthehill.org/wp-content/uploads/2009/10/astar.zip)

Once downloaded, unzip the zip file and open a terminal.

You now have three options:

**Review the Source Code**

The meat of the code is all in Clojure, here:

_src/main/resources/com/example/clap/astar.clj_

There is a bit of boot-strap Java code in the following file, but I can't say its all that interesting:

_src/main/java/com/example/clap/App.java_

**Running from Source**

If you are on a Mac, or you already have Maven and Java installed, just run the following:

_cd astar &amp;&amp; mvn test_

Maven will download all the needed packages and then compiled and execute the demo.

**Running from Binary**

If you are on Linux, or have cygwin installed on Windows, you can run the following:

_cd astar/bin/ &amp;&amp; ./run-astar_
