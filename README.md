python-arm-xcompile
===================

This is a build script and patches for cross-compiling Python to target the ARM architecture.

You must have a cross-compile toolchain already set up. [This guide](http://akanto.wordpress.com/2012/10/02/cross-compiling-kernel-for-raspberry-pi-on-fedora-17-part-2/) is an excellent resource for setting up crosstool-ng.

1. Edit `build.sh` and change the variables at the top to match your environment.
2. Run `build.sh`. This will download Python and build it for you.

Assuming the build succeeds, a list of modules will be printed out. Some modules
will not build statically since they need to be dynamically linked to glibc (TODO).

Python 2.7.4 unsupported
------------------------

Note that Python 2.7.4 introduced breaking changes to _sre.MAXREPEATS that will
fail to cross-compile statically. You must use 2.7.3 instead (for now) --
`build.sh` will download and extract this for you.

Credits
-------

* The `files/Python-2.7.3-xcompile.patch` file is modified from the patch given by
Lothsahn on the [Cross Compiling Python for Embedded Linux](http://randomsplat.com/id5-cross-compiling-python-for-embedded-linux.html) post.
* http://stackoverflow.com/a/1155092 for statically compiling Python interpreter.
