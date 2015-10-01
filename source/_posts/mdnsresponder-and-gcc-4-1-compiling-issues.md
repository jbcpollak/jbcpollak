title: 'mDNSResponder and GCC 4.1 compiling issues '
id: 34
date: 2007-01-23 09:15:32
tags:
  - bonjour
  - compiler
  - gcc
  - linux
  - mdnsresponder
  - ubuntu
  - zeroconf
categories:
  - Tech
---

I have found an issue with compiling mDNSResponder-107.6 (and probably
older versions) with GCC 4.1\. This will bite you if you are using Ubuntu Edgy or another gcc-4.1 based-distro.

In short, you'll get this error message:

    cc dns-sd.c -L../mDNSPosix/build/prod/ -ldns_sd -I../mDNSShared -o build/dns-sd
    /usr/bin/ld: build/dns-sd: hidden symbol `__stack_chk_fail_local'
    in /usr/lib/libc_nonshared.a(stack_chk_fail_local.oS) is referenced by DSO
    /usr/bin/ld: final link failed: Nonrepresentable section on output
    `</pre>

    The solution is below...Here is the full output of the compile command you should see:

    <pre>`
    jpollak@moya:/tmp/mDNSResponder-107.6/mDNSPosix$ make os=linux
    Responder daemon done
    Client library done
    make[1]: Entering directory `/tmp/mDNSResponder-107.6/Clients'
    cc dns-sd.c -L../mDNSPosix/build/prod/ -ldns_sd -I../mDNSShared -o build/dns-sd /usr/bin/ld: build/dns-sd: hidden symbol __stack_chk_fail_local'
    in /usr/lib/libc_nonshared.a(stack_chk_fail_local.oS) is referenced by DSO
    /usr/bin/ld: final link failed: Nonrepresentable section on output
    collect2: ld returned 1 exit status
    make[1]: *** [build/dns-sd] Error 1
    make[1]: Leaving directory `/tmp/mDNSResponder-107.6/Clients'
    make: *** [../Clients/build/dns-sd] Error 2
    `</pre>

    *Solution*:

    Edit mDNSResponder-107.6/mDNSPosix/Makefile, and find line 271:

    @LD = ld -shared@

    and change it to:

    @LD = gcc -shared@

    Now when you build, everything works:
    <pre>`
    jpollak@moya:/tmp/mDNSResponder-107.6/mDNSPosix$ make os=linux clean
    make[1]: Entering directory `/tmp/mDNSResponder-107.6/Clients'
    rm -rf build
    make[1]: Leaving directory `/tmp/mDNSResponder-107.6/Clients'
    jpollak@moya:/tmp/mDNSResponder-107.6/mDNSPosix$ make os=linux
    Responder daemon done
    Client library done
    make[1]: Entering directory `/tmp/mDNSResponder-107.6/Clients'
    mkdir build
    cc dns-sd.c -L../mDNSPosix/build/prod/ -ldns_sd -I../mDNSShared -o
    build/dns-sd
    make[1]: Leaving directory `/tmp/mDNSResponder-107.6/Clients'
    Clients done
    Embedded Standalone Client done
    Embedded Standalone Responder done
    Embedded Standalone ProxyResponder done
    Identify done
    NetMonitor done
    dnsextd done
    Name Service Switch module done

To give credit where credit is due, I found the solution "here":http://www.xastir.org/wiki/index.php/HowTo:Ubuntu_6.10
