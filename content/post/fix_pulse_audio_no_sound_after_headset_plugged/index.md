---
title: "Fix pulse audio no sound after headset plugged"
date: 2018-01-27T13:14:37+07:00
draft: false
---

hi, today i wanna tell you about fixing about how to fix pulseaudio no sound after headphone or headset plugged in. yes, i do this on debian and maybe work on your linux distro what you use now. ok, let's into the point
<p>1. first run this command</p>

```
cd /usr/share/pulseaudio/alsa-mixer/paths/
```

<p>2. make a restore point</p>

```
sudo cp analog-output-headphones.conf analog-output-headphones.bak
```

<p>3. edit this file with this command</p>

```
sudo nano analog-output-headphones.conf
```

scroll the down and find this "[Element Speaker] " (without quote) and change into look like this

```
[Element Speaker]
switch = on
volume = ignore
```

<p>4. now make restore point again for fixed configuration</p>

```
sudo cp analog-output-headphones.conf analog-output-headphones.fixed
```

<p>5. and reboot</p>

okey, this is how to fix pulseaudio no sound after headphone or headset plugged in. i hope this method work perfectly on your distro. any question ? leave command below. and i will say thanks ! 