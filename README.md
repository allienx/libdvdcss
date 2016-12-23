# libdvdcss

From the [website](http://www.videolan.org/developers/libdvdcss.html):

> `libdvdcss` is a simple library designed for accessing DVDs like a block device without having to bother about the decryption.

This repository hosts the compiled `libdvdcss-2.dll` for Windows. Download
the `.dll` from this repository and drop it into the Handbrake installation
folder to convert your DVDs to mp4 files.

## Instructions

* Find out if your machine is 32 or 64-bit.
* Download the appropriate `libdvdcss-2.dll` from this repository (use the highest version).
* Move `libdvdcss-2.dll` into the Handbrake installation folder.
* Enjoy.

## Compile libdvdcss yourself

**Windows 10 is required for these instructions.**

These instructions are tailored for those familiar with the command line on a Linux machine.
I documented them so I don't forget them.

* Download the `libdvdcss` source code for version you want from [here](http://download.videolan.org/pub/libdvdcss/).
* Open the Ubuntu VM built into Windows 10 (Windows Subsystem for Linux).
* `cd` to the directory the source code was downloaded to (the path to your Downloads folder in the Ubuntu VM is `/mnt/c/Users/username/Downloads`).

Run the following commands to build `libdvdcss-2.dll`:

```sh
# the following command is needed when compiling for Ubuntu
# sudo apt-get install build-essential checkinstall

sudo apt-get install mingw-w64
tar -xjf /path/to/libdvdcss.tar.bz2
cd /path/to/libdvdcss

# to fix an error like "WARNING: 'aclocal-1.15' is missing on your system."
touch aclocal.m4 Makefile.am Makefile.in

# 32-bit
./configure --host=i686-w64-mingw32

#64-bit
./configure --host=x86_64-w64-mingw32

make
```

The library will be output to `\path\to\libdvdcss\libs\libdvdcss-2.dll`.
