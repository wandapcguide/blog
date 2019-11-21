---
title: "Cara mengatasi mtp tidak terdeteksi pada debian9"
date: 2018-05-10T23:02:13+07:00
draft: false
---
hi guys, apa kabar ? semoga sehat selalu yah. pernah gak sih kalian mengalami ketika usb di masukan terbaca di pc yang run Debian sebagai OS nya dan ketika menyambungkan ponsel android sebagai media transfer data atau tersambung sebagai mtp devices tetapi di pc tersebut tidak terbaca bahkan tidak termount padahal terdapat notifikasi MTP pada android kita ?

nah kali ini saya akan membagikan solusinya nih, asalkan distro yang kalian gunakan support dengan FUSE dan mungkin ada sedikit perbedaan. disini saya menggunakan Debian 9 sebagai OS pada pc saya jika ada perbedaan depedencies harap disesuaikan terhadap distro masing masing ya mungkin saja hanya beda nama packet, baik kita langsung saja ke caranya.

1 install terlebih dulu depedencies atau packet nya
```
#apt-get install libmtp-common go-mtpfs mtp-tools
```
2 lalu buatlah direktori untuk membuat mount point untuk ponsel android yang ingin kita gunakan, dan beri akses pada direktori tersebut
```
#mkdir /media/andromtp

#chmod 775 /media/andromtp
```
3 kemudian masukan ponsel mu dan mount melalui terminal

```
$sudo go-mtpfs -allow-other /media/andromtp
```

jika di ponsel mu ada notifikasi meminta izin seperti gambar dibawah ini klik izinkan lalu mount kembali melalui terminal

<center><img class="special-img-class" src="/mtp/1.png" /></center>

lalu di terminal akan terlihat gambar seperti dibawah ini

<center><img class="special-img-class" src="/mtp/2.png" /></center>

lalu buka file eksplorer seperti thunar dan coba klik andromtp apakah bisa sekarang ? jika bisa maka akan seperti gambar dibawah ini

<center><img class="special-img-class" src="/mtp/3.png" /></center>

pada gambar diatas saya membuat direktori dengan nama j5prime, perlu diingat sebelum mencabut ponsel android mu alangkah baiknya ikuti step nomor 4


4 untuk unmountin kita ketikan ini

```
$sudo umount /media/andromtp
```

5 agar kalian tidak menulis sudo go-mtpfs ........ lagi dan lagi maka ikuti langkah ini
```
$sudo visudo (tambahkan line ini)
user ALL=(ALL) NOPASSWD: /usr/bin/go-mtpfs -allow-other /media/andromtp
user ALL=(ALL) NOPASSWD: /bin/umount /media/andromtp
```
dan ketikan lagi dibawah ini:
```
$vim .bashrc (tambahkan line ini dibagian aliases)
alias mount-mtp='sudo /usr/bin/go-mtpfs -allow-other /media/andromtp'
alias unmount-mtp='sudo /bin/umount /media/androku'
```

kemudian anda bisa menjalankan nya tanpa mengisi password root dan dengan kalimat sedikit hanya dengan mengetikan
mount-mtp = untuk mounting ponsel android melalui terminal, dan
unmount-mtp = untuk unmounting ponsel android melalui terminal

note : pada visudo user diganti dengan nama user kalian di OS yang kalian pake

mudah bukan ? , seperti yang saya sebutkan ada sedikit perbedaan di beberapa distro untuk nama packet nya jadi keep-on-eyes yah btw kalo step mount dan unmount nya sama saja yang membedakan hanyalah masalah di packet nya tadi. jika ada yang salah mohon dikoreksi dan apabila ada yang ingin ditanyakan silakan komentar dibawah ini, jaga kesopanan agar tertib sekian terimakasih..
