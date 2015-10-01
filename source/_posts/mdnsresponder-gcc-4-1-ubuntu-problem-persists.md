title: mDNSResponder / GCC 4.1 / Ubuntu Problem persists
tags:
  - bonjour
  - compiler
  - gcc
  - linux
  - mdnsresponder
  - ubuntu
  - zeroconf
id: 43
categories:
  - Tech
date: 2007-05-04 14:52:08
---

A "while back":http://www.offthehill.org/articles/2007/01/23/mdnsresponder-and-gcc-4-1-compiling-issues
I reported on an obscure problem when compiling applications against the dnssd library that comes with Apple's mDNSResponder.

This post is just to report that these problems persist in mDNSResponder 108.4\. As I reported before, here is what you'll see when compiling your program:

`
hidden symbol `__stack_chk_fail_local'
in /usr/lib/libc_nonshared.a(stack_chk_fail_local.oS) is referenced by DSO
/usr/bin/ld: final link failed: Nonrepresentable section on output
`

As you can see, its all very intuitive.
