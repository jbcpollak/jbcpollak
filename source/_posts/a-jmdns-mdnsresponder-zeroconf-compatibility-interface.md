title: A JmDNS / mDNSResponder Zeroconf Compatibility Interface
tags:
  - apple
  - bonjour
  - dns service discovery
  - dns-sd
  - java
  - jmdns
  - mdns
  - mdnsresponder
  - zeroconf
id: 64
categories:
  - Tech
date: 2008-01-08 11:54:35
---

My company has given me permission to release a Java [Zeroconf](http://en.wikipedia.org/wiki/Zeroconf) API. The advantage of this API is that it allows the application to select which implementing library to use at runtime, and eases developer work implementing mDNS / DNS-SD. I also think my API is easier to understand than the raw interfaces of the underlying implementations.

Currently there are two implementing backends, one for [JmDNS](http://jmdns.sourceforge.net/) and one for Apple's [mDNSResponder](http://developer.apple.com/networking/bonjour/). I would really like to see one written for [Avahi](http://avahi.org/), but I probably won't get to it myself.

The API is in the _org.jmdns.api_ package, which both implementations are in the _org.jmdns.impl_ package. A unit test is also included which demonstrates usage and verifies operation.

I've implemented this version within the JmDNS source tree, but ideally the API, JmDNS and mDNSResponder portions of the code would be broken out to be separately distributed, with the JmDNS and mDNSResponder portions functioning as plugins implementing the API.

I've only tested this against mDNSResponder 107.5\. I'm not sure if Apple's dnssd.jar is compatible with newer mDNSResponder versions or not.

You can download the full implementation here: [jmdns-kiva-1.1.3.tar.bz2](http://www.offthehill.org/wp-content/uploads/2008/01/jmdns-kiva-113tar.bz2 "jmdns-kiva-1.1.3.tar.bz2")

I hope the JmDNS project will pick this effort up and incorporate this into the official release!
