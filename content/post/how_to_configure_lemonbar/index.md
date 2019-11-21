---
title: "How to configure lemonbar"
date: 2017-10-28T14:56:24+07:00
draft: false
---

today, i wanna tell you how to configuration lemonbar or lemonbar configruation. lemonbar (formerly known as bar) is a lightweight bar entirely based on XCB. Provides full UTF-8 support, basic formatting, RandR and Xinerama support and EWMH compliance without wasting your precious memory. so lets begin.

to install lemonbar and load font on lemonbar you can go here > ![installing lemonbar and load font on lemonbar](/post/how_to_install_n_load_font_on_lemonbar)

remember lemonbar is statusbar, not panel. so, its not any taskbar. just print the output.

we wanna fetching information about :
1. date
2. ssid of wifi
3. batery
4. sound level
5. clock
6. window active status
7. music
8. icon for this item

<p>1. fetching the date</p>

we would use date command to print out that

```
date '+%d %b' #this print day number of the month and month
```

<p>2. ssid of wifi</p>

we would use iwgetid command to make simply setup but powerfull. let's se bellow

```
iwgetid -r  # it just print the ssid no other
```

<p>3. battery</p>

its important to avoid the low battery status and urged you to chare your laptop. i use acpi command to make it simple

```
acpi | cut -d, -f2 #its only  print battery level
```

<p>4. sound level</p>

sound level can print into two type of output. can be proggesbar and can be text. if you wanna proggressbar use mkb and if you want text lets follow me.
we use amixer command.

```
amixer get master | grep "Front Left:" | awk '{print $5}' | cut -d [ -f2 | cut -d ] -f1 # its only print sound level
```

<p>5. clock</p>

as same as with date we use date command

```
date '+%H:%M'
```

<p>6. window active status</p>

window active status only print the name of focused window not like panel clickable and print the name. we use xdotool command

```
xdotool getwindowfocus getwindowname
```

<p>7. music</p>

we use mpd and mpc command to print the listening music status

```
mpc -p 6601 -f "%artist% >> %title%" | head -1
```

<p>8. icon for this item</p>

you must install siji font to get icon for this ouput and to make more beautiful setup of bar.
if you already install that font let's follow

run this command to get the glymphes code
```
xfd -fa Siji
```
and choose icon what you want to print at your bar setup for example:
the glymphes code of music icon is : 0x00e05c to print on the bar just run like this
```
echo -e "\ue05c" | lemonbar -f "Siji-8" -p #this print with bar standalone not fetch with all
```
<br>
**PRINT THEM ALL ONLY WITH LEMONBAR**

this setup will be eat more reosources of ram, coz you will run two lemonbar to get bar on right and left. but, not much eat resource. on this setup we would use bash script, if statement, case statement, while true do, and function like a C. oke let's follow.

make bash script like this
1. for status item of lemonbar
```
$vim statusquh

#!/bin/bash
#arg
#ndow="$(xdotool get_desktop | grep 0)"
#inf="$(mpc -p 6601 -f "%artist%" | head -1 | wc -l)"
#wifikek='iwgetid -r | wc -l'
#bat='acpi -i | head -1 | cut -d, -f1 | cut -d: -f2 | sed 's/ //g' | grep "Charging" | wc -l'


case $1 in

 window)
 ndow=`xdotool get_desktop | wc -l`
 if [ $ndow -eq 1 ]; then
 xdotool getwindowfocus getwindowname
 fi
 ;;

 musik)
 inf=`mpc -p 6601 -f "%artist%" | head -1 | wc -l`
 if [ $inf -eq 1 ]; then
 mpc -p 6601 -f "%artist% >> %title%" | head -1
 else
 echo not playing
 fi
 ;;

 volume)
 amixer get Master | grep "Front Left:" | awk '{print $5}' | cut -d [ -f2 | cut -d ] -f1
 ;;

 wifi)
 wifiqu=`iwgetid | wc -l`
 if [ $wifiqu -eq 0 ]; then
 echo "off"
 else
 iwgetid -r
 fi
 ;;

 infobat)
 bat=`acpi -i | head -1 | cut -d, -f1 | cut -d: -f2 | sed 's/ //g' | grep "Charging" | wc -l`
 if [ $bat -eq 1 ]; then
 echo "Charging"
 else
 echo "Discharging"
 fi
 ;;

 desktop)
 des=`xdotool get_desktop | wc -l`
 if [ $des -eq 1 ]; then
 xdotool get_desktop
 fi
 ;;

 batre)
 acpi | cut -d, -f2
 ;;

 jam)
 date '+%H:%M'
 ;;

 tanggal)
 date '+%d %b'
 ;;

esac
```
>save this code and move into /usr/local/bin/ with this command
```
 sudo mv statusquh /usr/local/bin
```

<p>2. now then, for left lemonbar</p>

```
$vim kiri

#!/bin/bash

#colour
red="#D24D57"
case $1 in
semua)
nda() {
    echo -e "\ue0b1" && statusquh window
}

ndi() {
    echo -e "\ue224" && statusquh infobat
}

ndu() {
    echo -e "\ue10f" && statusquh wifi
}

nde() {
    echo -e "\ue107" && echo Hana
}

while :; do
kok="$(nda)"
kek="$(ndi)"
kuk="$(ndu)"
kik="$(nde)"

echo $kok $kek $kuk $kik
sleep 1
done
;;
esac
```

>save it, and move into /usr/local/bin

<p>3. and this for right lemonbar</p>

```
$vim kanan

#!/bin/bash

#colour
red="#D24D57"
case $1 in
semua)
nda() {
    echo "%{F$red}TGL:%{F-}" && statusquh tanggal
}

ndi() {
    echo "%{F$red}JAM:%{F-}" && statusquh jam
}

ndu() {
    echo "%{F$red}VOL:%{F-}" && statusquh volume
}

nde() {
    echo "%{F$red}BAT:%{F-}" && statusquh batre
}

while :; do
kok="$(nda)"
kek="$(ndi)"
kuk="$(ndu)"
kik="$(nde)"

echo $kok $kek $kuk $kik
sleep 1
done
;;
esac
```

>save it and move into /usr/local/bin

<p>5. for lemonbar to print out that</p>

```
$vim barkiri

#!/bin/bash
kiri semua | lemonbar -p -f "Clean-10" -f "Siji-8" -g 1366x24

save it and move into /usr/local/bin

6. for second lemonbar to print out that

$vim barkanan

#!/bin/bash
kanan semua | lemonbar -p -f "Clean-10" -g 250x24+1116+0

7. testing time !
for testing. run kiri and kanan like this

$barkiri
$barkanan
```

the result is like this

<center><img class="special-img-class" src="/conf-lemonbar/1.png" /></center>


if you want find much more about lemonbar configuration or my dotfile just visit my github page > dante08
oke, i hope you can do about configuration lemonbar. only that for me, littlebit about lemonbar especialy about lemonbar configuration. so thank you much. 