title: 'A* in Clojure: Part Two'
tags:
  - 'a*'
  - a-star
  - astar
  - astar-in-clojure
  - clojure
  - git
  - github
  - java
id: 180
categories:
  - Tech
date: 2010-01-24 23:56:23
---

Today, I decided to flush out and clean up my [A*](http://en.wikipedia.org/wiki/A*_search_algorithm) implementation in [Clojure](http://clojure.org/). I cleaned up the namespaces, removed some cruft, got the Java integration working (which required by-passing RT.loadResourceScript() since it seems to be broken), and moving my graph structure definition out of code and into a separate XML file (which is read and parsed directly in Clojure).

I'm still not sold on functional programming, these minor changes took me more hours than I care to admit and gave me a crazy headache, but that could just be because I'm unfamiliar with the language.

I also uploaded the code to GitHub, because I figured where's the fun in learning a new algorithm in a new language without tossing in the risk of losing all your code to an silly mistake with an unfamiliar version control system?

Luckily no data was lost, and if you have any interest in Clojure, Clojure-Java integration, or A-Star search, check it out here:

[http://github.com/jbcpollak/AStar-Clojure](http://github.com/jbcpollak/AStar-Clojure)

My next steps are going to be more rigorous unit testing and perhaps some benchmarking. I'd like to see how this implementation does against a large graph.
