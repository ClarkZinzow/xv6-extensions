# xv6-extensions

A collection of extensions to xv6, the ANSI C reimplementation of Dennis Ritchie's and Ken
Thompson's Unix Version 6.  These extensions include:

* A CPU scheduler supporting two pricing schemes similar to those used by AWS and other cloud
  services: reserved processes and spot processes.  The former is implemented with a lottery
  scheduler.
* A few modern virtual memory features, including:
  * Null-pointer dereference handling.
  * A stack rearrangement, with the stack placed at the high end of the address space.
* Kernel threads.
* Protection from data corruption via the addition of file checksums.

### Getting Started

To run xv6, I suggest that you install the QEMU PC emulator.  You can get a version of QEMU with
patched debugging facilities from the IAP 6.828 crew at MIT.  To build your own patched version of
QEMU, do the following:

1. Clone the IAP 6.828 QEMU git repository
```
$ git clone http://web.mit.edu/ccutler/www/qemu.git -b 6.828-2.3.0
```
2. On Linux, you may need to install several libraries. We have successfully built 6.828 QEMU on
Debian/Ubuntu 16.04 after installing the following packages: libsdl1.2-dev, libtool-bin,
libglib2.0-dev, libz-dev, and libpixman-1-dev.

3. Configure the source code (optional arguments are shown in square brackets; replace PFX with a path of your choice)
   * Linux:
   ```
   $ ./configure --disable-kvm [--prefix=PFX] [--target-list="i386-softmmu x86_64-softmmu"]
   ```
   * OS X:
   ```
   $ ./configure --disable-kvm --disable-sdl [--prefix=PFX] [--target-list="i386-softmmu x86_64-softmmu"]
   ```

     The prefix argument specifies where to install QEMU; without it QEMU will install
to /usr/local by default. The target-list argument simply slims down the architectures QEMU will
build support for.
4. Run make && make install

To simulate one of the xv6 extensions in this repository, do the following:

1. Clone or download this repository.
2. Navigate to the `src` directory of the repository.
```
$ cd /path/to/repository/xv6-extensions/src
```
3. Choose which extension you want to emulate.  E.g., if you want to simulate the kernel thread
   extension of xv6, we would proceed as follows:
```
$ cd xv6-kernel
```
4. Run the QEMU emulator.
```
$ make qemu
```
5. Test it out!
