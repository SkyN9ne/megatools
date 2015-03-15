megatools - command line client application for Mega
====================================================

Megatools is a collection of programs for accessing Mega service from 
a command line of your desktop or server.

Megatools allow you to copy individual files as well as entire directory 
trees to and from the cloud. You can also perform streaming downloads for 
example to preview videos and audio files, without needing to download 
the entire file.

Megatools are robust and optimized for fast operation - as fast as Mega 
servers allow. Memory requirements and CPU utilization are kept at minimum.

You can register account using a 'megareg' tool, with the benefit of having 
true control of your encryption keys.

Mega website can be found at http://mega.co.nz.

Megatools can be downloaded at http://megatools.megous.com


Tools
=====

  megareg      Register and verify a new mega account
  megadf       Show your cloud storage space usage/quota
  megals       List all remote files
  megamkdir    Create remote directory
  megarm       Remove remote file or directory
  megamv       Move and rename remote files
  megaput      Upload individual files
  megaget      Download individual files
  megadl       Download file from a "public" Mega link
               (doesn't require login)
  megastream   Streaming download of a file
               (can be used to preview videos or music)
  megasync     Upload or download a directory tree
  megafs       Mount remote filesystem locally.


All of these tools do:

- Local caching of remote session/filesystem information 
  for faster execution. Cache is encrypted with your password 
  key.
- Support loading login credentials from a configuration file


Usage
=====

See man pages for how to use individual tools and how to configure them:

  man megatools


Windows Quirks
==============

On Windows, if you see weird characters in your megals output, you'll need
to set correct CHARSET environment variable. For example on Czech Windows 
this would mean executing this command in cmd before using the tools:

  set CHARSET=CP852

This is just a cosmetic issue. Internally, megatools always work with UTF-8
file names, and even if the tool's terminal output is corrupted, files names
of downloaded/uploaded files will be correct.


Installation on Mac OS X (Mountain Lion)
========================================

Thanks to Carl Moden, megatools is available in Homebrew (http://brew.sh/).

You can therefrore install megatools with:

  brew install megatools

To install megatools by hand you need to:

1. Install glib-networking with a ca-bundle:

  export BUNDLE=/usr/local/share/ca-bundle.crt
  curl http://curl.haxx.se/ca/cacert.pem -o $BUNDLE
  /usr/bin/sed -ie "s|--without-ca-certificates|--with-ca-certificates=$BUNDLE|" /usr/local/Library/Formula/glib-networking.rb
  brew install glib-networking

2. Make the pkgconfig (.pc) file for libcurl findable by megatools configure script:

  export PKG_CONFIG_PATH=/usr/local/Library/ENV/pkgconfig/10.8

3. Untar megatools, run `./configure`, `make` and `make install` as usual.


Installation on Gentoo
======================

Third-party ebuild is available at:

  https://github.com/megabaks/stuff/tree/master/app-misc/megatools


Installation on Debian
======================

Megatools is available in sid thanks to Alberto Garcia:

  https://packages.debian.org/unstable/megatools


Installation on FreeBSD
=======================

Megatools is available in freshports thanks to Maxim V. Kostikov:

  http://www.freshports.org/net/megatools/


Building megatools from source code
===================================

You will need to install dependnencies first, to be able to do the build from
source code tarball.

On Debian, Ubuntu:

  apt-get -y install build-essential libglib2.0-dev libssl-dev libcurl4-openssl-dev libgirepository1.0-dev

On Fedora:

  yum -y install gcc make glib2-devel libcurl-devel openssl-devel gmp-devel tar

On OpenSUSE:

  zypper -n install gcc make glib2-devel libcurl-devel openssl-devel gmp-devel

On Arch Linux:

  pacman -Sy --noconfirm --needed pkg-config gcc make glib2 curl gmp nettle


Author
======

Megatools were written by Ondřej Jirman <megous@megous.com>, 2014
Webiste: http://megatools.megous.com


Support and bug reports
=======================

If you think you've found bug in megatools, send a report including enough
information for recreating the issue to: megous@megous.com


License
=======

Megatools are licensed under GPLv2 with OpenSSL exemption, see LICENSE
file for details.

This product includes software developed by the OpenSSL Project for use
in the OpenSSL Toolkit. (http://www.openssl.org/)
