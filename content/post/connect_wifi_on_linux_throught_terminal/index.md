---
title: "Connect wifi on linux throught terminal"
date: 2017-11-05T14:49:56+07:00
draft: false
---

hi sobat, apa kabar ? semoga sehat semua ya. oke malam ini saya akan memberikan tips tentang menghubungkan wifi atau connect wifi melalui terminal dengan cara yang simple pastinya. hal ini berguna ketika anda sedang menggunakan linux kalian pada mode TTY atau non-gui atau bahkan gui tapi menggunakan window manager tanpa ada tray icon wifi alias tidak menginstall panel seperti tint2, gnome-panel, dll. oke berikut langkah nya.

<p>1. pada TTY mode atau terminal ketikan teks di bawah ini</p>

```
nmcli dev wifi connect ESSID_NAME password ESSID_PASSWORD
```

dengan catatan :
ESSID_NAME itu berarti nama dari wifi kamu atau biasa disebut SSID

ESSID_PASSWORD itu berarti password dari nama wifi kamu atau SSID kamu

untuk melihat jaringan wifi disekitar mu bisa dengan mengetikan.
```
nmcli dev wifi
```

<p>2. tunggu sebentar hingga proses penyambungan selesai.</p>

<p>3. jika connect cek dengan mengetikan ini</p>
```
iwgetid -r
```
nanti bakalan muncul nama wifi atau ssid yang telah anda sambungkan tadi..

oke begitu aja guys, semoga bermanfaat. sekian terimakasih... 