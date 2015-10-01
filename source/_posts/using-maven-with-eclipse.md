title: Using Maven with Eclipse
tags:
  - devlopment
  - eclipse
  - java
  - maven
id: 46
categories:
  - Tech
date: 2007-09-05 15:22:24
---

I uninstalled "M2Eclipse":http://m2eclipse.codehaus.org/ and installed "q4e":http://code.google.com/p/q4e/ and gave it a shot. All the core functionality seems to be there (dependancy management is the big one for me) and importing from a project pom seems to work (although It didn't seem to import a multilayer project, I had to import each module separately, but thats ok for me).

Its nice to add dependancies manually, although I'd like to see a dependancy search page like m2eclipse has and a place to cut and paste dependancy XML chunks (I use mvnrepository.com a lot). The dependancy graph is a nice feature although the controls on the side seem a bit buggy.

A pom view somewhat like the built in Ant view would be nice, where I can double click a phase or a plugin:goal and run it, although I understand it might make sense to be able to manually which goals / phases appear in the workspace.

So far so good, I hope the m2eclipse and q4eclipse projects can work together in the future.
