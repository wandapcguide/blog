---
title: "How to install 2BWM"
date: 2016-12-25T13:14:37+07:00
draft: false
comments: true
---

hi guys. now, i wanna update my tutorial about 2bwm. maybe you little bit confusion about tutorial how to install 2bwm especially on ubuntu. now, i wanna change into easy step. this is how to install 2bwm, lets follow!

1. Installing library

>xcb-randr: libxcb-randr0-dev

>xcb-ewmh: libxcb-ewmh-dev

>xcb-icccm: libxcb-icccm4-dev

>xcb-keysyms: libxcb-keysyms1-dev

>xcb-xrm: lets follow bellow

```
sudo add-apt-repository ppa:aguignard/ppa
sudo apt-get update
sudo apt-get install libxcb-xrm-dev
```
>optional: gcc

2. installing 2bwm
```
$ git clone git://github.com/venam/2bwm.git
$ cd 2bwm
$ make
# make install
```
3. add 2bwm into login session
make file desktop entries with name 2bwm.desktop at /usr/share/xsession/
and copy this code into your desktop entries file

```
[Desktop Entry]
Encoding=UTF-8
Name=2BWM CUK
Comment=Binary space partitioning window manager
Exec=2bwm
Type=Application
```
and save it!

4. Testing 2bwm
after complete the installation run this code on the terminal
```
$sudo service lightdm restart
```
note: if you use lightdm

5. what ? the desktop entries dont show after i made desktop entries file above!
you can install 2bwm form this git://github.com/Dante08/2bwm.git  how to? its same step at above..
```
$git clone git://github.com/Dante08/2bwm.git
$ cd 2bwm
$ make
# make install
```
and repeat step 4

oke, i feel only that. i hope you can do, and if any minus leave comment below.
