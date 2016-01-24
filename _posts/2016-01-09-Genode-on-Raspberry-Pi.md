---
layout: post
title: Genode on Raspberry Pi
categories: Genode, RaspberryPi
---
This is a recipe for installing Genode on the Raspberry Pi.
<!--more-->
It is mostly based on the <a href='http://genode.org/documentation/release-notes/13.11#Raspberry_Pi'>release notes</a> on Genode.org.
<br>
It has only been tested on Linux (Ubuntu).

<h3>Prerequisites</h3>
You need a SD card with a Raspberry Pi installation.<br>
Follow the <a href='https://www.raspberrypi.org/documentation/installation/installing-images/README.md'>guide</a> on raspberrypi.org.
<p>
Genode needs the Genode toolchain:

<ul>
	<li>Download the <a href='http://sourceforge.net/projects/genode/files/genode-toolchain/15.05/genode-toolchain-15.05-x86_64.tar.bz2/download'>Genode toolchain</a></li>
	<li>Install the toolchain by running:<br>
		<pre>sudo tar xPfj genode-toolchain-15.05-x86_64.tar.bz2</pre>
	</li>
</ul>
<h3>Fetch Genode and dependencies</h3>
Run the following script to fetch Genode and various dependencies.<br>
The script will also create a build directory for a Genode build with Fiasco.OC for Raspberry Pi.
<p>
<pre>
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

</pre>

<h3>Change build configuration</h3>
The build is configured using the <code>build.conf</code> file in <code>build/etc/</code>. <br>
You should at the very least add the <code>dde_linux</code> repository by uncommenting that line.

<h3>Build Genode ELF</h3>
Run <code>make run/demo</code> from the <code>build/foc_rpi</code> folder to build  Genode.<br>
The result is a <code>genode.elf</code> file.
<p>
The ELF file needs to be converted into a IMG file, since the Raspberry Pi can’t handle ELF files:
</p>

<pre>/usr/local/genode-gcc/bin/genode-arm-objcopy -Obinary var/run/demo/image.elf genode.img</pre>
<br>
<p>
Copy the resulting `genode.img` to the SD card root.<br>
Add the following lines to the `config.txt` file in the the SD card root:
</p>
<pre>

	kernel=genode.img
	kernel_address=0x00800000

</pre>
<p>
With that, the Raspberry Pi should boot into Genode and open the demo app.
</p>