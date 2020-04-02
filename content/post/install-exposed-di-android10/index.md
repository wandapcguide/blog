---
title: "Cara install Xposed di Android 10"
date: 2020-04-01T15:45:06+07:00
draft: false
comments: true
---

halo guys, apa kabar nya ? semoga sehat selalu ya. kali ini saya akan membahas gimana sih cara memasang exposed installer atau install exposed pada Android 10 atau Android Q, karena ada pembaruan sistem dan tentu saja pembaruan keamaan pada system tersebut jadi cara nya agak sedikit berbeda guys.<br>

bagi player lama pasti sudah tahu lah apa itu exposed, sekali lagi saya jelaskan (maaf kalo salah ye :D). jadi exposed itu adalah sebuah framework yang berfungsi sebagai pengubah atau alat modifikasi sebuah system atau aplikasi tanpa menyentuh aplikasi yang dimaksud. keuntungan nya sih dia bisa jalan pada system yang berbeda dan juga rom yang berbeda jadi gak ribet lah, alias universal. sayang nya sang developer orisinil dari Xposed tak melanjutkan project tersebut setelah android oreo (android 8) maka dari itu sekarang android 10 menggunakan EDXposed dan taichi (disini kita menggunakan EDXposed btw karena saya sudah coba yang taichi ada yang gak support dengan beberapa module nya dari Xposed yang original)<br>

baik lantas gimana caranya tuh ? baiklah berikut cara menginstal Xposed pada android Q atau android 10
1. update magisk manager dan magisk binary (magiskSU) nya terlebih dahulu ke latest version
{{< image src="/xposed10/1.jpg" alt="Hello Friend" position="center" style="border-radius: 8px;" >}}
2. klik bagian modul lalu cari "riru - core" (tanpa tanda petik)
{{< image src="/xposed10/4.png" alt="Hello Friend" position="center" style="border-radius: 8px;" >}}
3. lalu install module tersebut, jika sudah selesai jangan di reboot terlebih dahulu hp nya dan mari kita lanjut ke step 4
4. dan cari lagi module bernama "riru - edxposed" (tanpa tanda petik) untuk ini pilih sesuai device kalian. jika kalian menggunakan ASUS MAX PRO M1 bisa di dowload [>>DISINI<<](http://j.gs/DveZ) untuk uninstaller nya dapat di download [DISINI](http://j.gs/Dvea) "keduanya link google drive"
{{< image src="/xposed10/3.png" alt="Hello Friend" position="center" style="border-radius: 8px;" >}}
5. lalu install module tersebut, jika sudah selesai jangan di reboot terlebih dahulu hp nya dan mari kita lanjut ke step 6
6. kemudian install APK EDXposed nya yang dapat kalian download [>>disini<<](http://j.gs/Dveb) (wajib) "link google drive"
7. reboot device kalian.
8. dan selamat... anda telah berhasil memasang Xposed pada android 10 atau android Q
{{< image src="/xposed10/5.jpg" alt="Hello Friend" position="center" style="border-radius: 8px;" >}}
<br>
apabila kalian bootloop kalian dapat mengikuti langkah dibawah ini.
- masuk ke twrp
- pilih advance kemudian pilih file manager
- lalu masuk ke direktori data/adb/modules
- kemudian pilih folder sesuai module magisk yang bikin bootloop kemudian hapus. dengan cara mengeklik tanda centang di bawah dan pilih delete.

nah guys, disini kita membutuh kan magisk sekarang semenjak ada nya magisk kita dipermudahkan. jika ada yang ingin di tanyakan silakan tinggalkan komentar dibawah ya :D