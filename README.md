# WORK IN PROGRESS...

# openwrt-build-ht-tm02-nim
Cross compile **nim** code for the HooToo HT-TM02 running OpenWrt. I'm using it like this:

Create a shell script (named `ht02nim`) with this content:

```
#!/bin/bash
docker run --rm -v ${PWD}:/src davidsblog/openwrt-build-ht-tm02-nim \
     /bin/sh -c "cd /src; $*"
```
Then, you can use nim as normal, when *prefixed* with `ht02nim`, like this:

`ht02nim nim -v`

...which should print the version of the nim compiler, or to compile `myprog.nim`:

`ht02nim nim c --cpu:mipsel --os:linux myprog.nim`

Compilation is done inside the *container*, but the source code (and resulting binary) will be in the current directory of the *host* machine.  I find it to be an easy way to cross-compile from many different machines.
