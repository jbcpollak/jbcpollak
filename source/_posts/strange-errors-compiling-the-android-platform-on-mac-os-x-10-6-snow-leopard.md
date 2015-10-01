title: Strange Errors Compiling The Android Platform on Mac OS X 10.6? (Snow Leopard)
id: 170
categories:
  - Tech
date: 2009-12-13 00:13:46
tags:
---

If you are having trouble compiling Android on Snow Leopard, first make sure you've installed the Leopard 10.5 Java 1.5 SDK, according to [these instructions](http://chxor.chxo.com/post/183013153/installing-java-1-5-on-snow-leopard "Java 1.5 on Snow Leopard").

Second, make sure you have the latest XCode installed, and make sure you have installed the optional 10.4 SDK. In my case, it appeared that the 10.4 sdk was installed, but it was either corrupt or out of date, resulting in many strange errors like the following:

[**Issue 993**](http://code.google.com/p/android/issues/detail?id=993 "Android Issue 993")
<pre>(out/target/common/obj/JAVA_LIBRARIES/framework_intermediates/javalib.jar)
Docs droiddoc: out/target/common/docs/framework
Could not load 'clearsilver-jni'
java.library.path = out/host/darwin-x86/lib
make: *** [out/target/common/docs/framework-timestamp] Error 45</pre>
**[Issue 5000](http://code.google.com/p/android/issues/detail?id=5000 "Android Issue 5000")**
<pre>host C: emulator &lt;= external/qemu/distrib/zlib-1.2.3/adler32.c
host C: emulator &lt;= external/qemu/distrib/zlib-1.2.3/compress.c
host C: emulator &lt;= external/qemu/distrib/zlib-1.2.3/crc32.c
host C: emulator &lt;= external/qemu/distrib/zlib-1.2.3/deflate.c
host C: emulator &lt;= external/qemu/distrib/zlib-1.2.3/gzio.c
In file included from external/qemu/distrib/zlib-1.2.3/gzio.c:601:
/Developer/SDKs/MacOSX10.4u.sdk/usr/include/stdarg.h:4:25: error: stdarg.h:
No such file or directory
external/qemu/distrib/zlib-1.2.3/gzio.c: In function ‘gzprintf’:
external/qemu/distrib/zlib-1.2.3/gzio.c:610: warning: implicit declaration
of function ‘va_start’
external/qemu/distrib/zlib-1.2.3/gzio.c:628: warning: implicit declaration
of function ‘va_end’</pre>
So if these issues strike you, follow the directions to switch to Java 1.5, and reinstall XCode, then run:
<pre>make clean &amp;&amp; make</pre>
In the android platform's main directory.

Unfortunately, I'm still stuck with this build error I haven't gotten past yet:
<pre>host Prebuilt: libSDL (out/host/darwin-x86/obj/STATIC_LIBRARIES/libSDL_intermediates/libSDL.a)
ranlib: file: out/host/darwin-x86/obj/STATIC_LIBRARIES/libSDL_intermediates/libSDL.a(SDL_getenv.o) has no symbols
ranlib: file: out/host/darwin-x86/obj/STATIC_LIBRARIES/libSDL_intermediates/libSDL.a(SDL_malloc.o) has no symbols
ranlib: file: out/host/darwin-x86/obj/STATIC_LIBRARIES/libSDL_intermediates/libSDL.a(SDL_qsort.o) has no symbols
ranlib: file: out/host/darwin-x86/obj/STATIC_LIBRARIES/libSDL_intermediates/libSDL.a(SDL_stdlib.o) has no symbols
ranlib: file: out/host/darwin-x86/obj/STATIC_LIBRARIES/libSDL_intermediates/libSDL.a(SDL_audiodev.o) has no symbols
ranlib: file: out/host/darwin-x86/obj/STATIC_LIBRARIES/libSDL_intermediates/libSDL.a(SDL_mixer_MMX.o) has no symbols
ranlib: file: out/host/darwin-x86/obj/STATIC_LIBRARIES/libSDL_intermediates/libSDL.a(SDL_yuv_mmx.o) has no symbols
ranlib: file: out/host/darwin-x86/obj/STATIC_LIBRARIES/libSDL_intermediates/libSDL.a(SDL_nullmouse.o) has no symbols
host Prebuilt: libSDLmain (out/host/darwin-x86/obj/STATIC_LIBRARIES/libSDLmain_intermediates/libSDLmain.a)
host Executable: emulator (out/host/darwin-x86/obj/EXECUTABLES/emulator_intermediates/emulator)
Undefined symbols:
  "_xml_builtin", referenced from:
      _xml_builtin$non_lazy_ptr in gdbstub.o
ld: symbol(s) not found
collect2: ld returned 1 exit status
make: *** [out/host/darwin-x86/obj/EXECUTABLES/emulator_intermediates/emulator] Error 1</pre>

So if anyone has any tips on that, I'd appreciate it!
