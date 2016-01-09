---
layout: post
title: Genode on Raspberry Pi
categories: Genode, RaspberryPi
---
# Genode on Raspberry Pi
The following is a recipe for installing Genode on the Raspberry Pi.
It is mostly based on http://genode.org/documentation/release-notes/13.11#Raspberry_Pi

It has only been tested on Linux (Ubuntu).

## Prerequisites
You need a SD card with a Raspberry Pi installation. Follow the guide on https://www.raspberrypi.org/documentation/installation/installing-images/README.md

Genode needs the Genode toolchain:

	- Download http://sourceforge.net/projects/genode/files/genode-toolchain/15.05/genode-toolchain-15.05-x86_64.tar.bz2/download
	- Install the toolchain by running `sudo tar xPfj genode-toolchain-15.05-x86_64.tar.bz2`

## Fetch Genode and dependencies
Run the following script to fetch Genode and various dependencies. The script will also create a build directory for a Genode build with Fiasco.OC for Raspberry Pi.

	# Genode
	git clone git://github.com/genodelabs/genode.git

	# USB drivers
	cd genode/repos/dde_linux 
	make prepare

	# CLib
	cd genode/repos/
	make -C libports prepare PKG=libc

	# libports
	cd genode/repos/libports
	make prepare

	# ports
	cd genode/repos/ports
	make prepare

	# dde rump
	cd genode/repos/dde_rump
	make prepare

	# foc
	cd genode/repos/base-foc
	make prepare

	# Create build dir
	../tool/create_builddir foc_rpi

## Change build configuration
The build is configured using the `build.conf` file in `build/etc/`. You should at the very least add the `dde_linux` repository by uncommenting that line.

## Build Genode ELF
Run `make run/demo` from the `build/foc_rpi` folder to build  Genode. The result is a `genode.elf` file.

The ELF file needs to be converted into a IMG file, since the Raspberry Pi can’t handle ELF files:

	/usr/local/genode-gcc/bin/genode-arm-objcopy -Obinary var/run/demo/image.elf genode.img

Copy the resulting `genode.img` to the SD card root.
Add the following lines to the `config.txt` file in the the SD card root:

	kernel=genode.img
	kernel_address=0x00800000  


With that, the Raspberry Pi should boot into Genode and open the demo app.



 
