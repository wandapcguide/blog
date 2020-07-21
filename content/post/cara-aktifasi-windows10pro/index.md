---
title: "Cara Aktivasi Windows 10 pro yang mengalami error saat aktivasi"
date: 2020-07-17T23:56:44+07:00
draft: false
comments:  true
---
Hallo, balik lagi di blog wandapcguide. Semoga kita semua sehat selalu ya agar tetap semangat menjalani hidup dan membaca artikel ini, hehehe. Untuk saat ini os windows sendiri yang sering dipergunakan adalah windows 10, seiring berkembang nya teknologi windows 7 pun mulai di tinggalkan dan dimatikan update nya yang berarti windows 7 pun tidak di rekomendasikan lagi pada saat ini. Tapi pernah gak sih saat mengaktifkan windows 10 nya mengalami error atau gagal aktifasi ? misalkan error code 0x80072ee7, atau error code 0x803fa067 pada saat aktifasi. Nah tepat banget nih, saya akan memberikan solusi bagi yang sedang mengalami error pada saat aktifasi.
<br>
{{< image src="/windows10/fail.png" alt="gagal aktifasi" position="center" style="border-radius: 8px;" >}}
<br>
<br>
Jika kalian mengalami error 0x80072ee7, atau error code 0x803fa067 saat aktifasi itu berarti kita harus menggunakan kms client secara manual. Dan cara ini pun legal ada nya, kalian bisa lihat sumber legalitas nya di bawah ini<br>
```
https://docs.microsoft.com/en-us/windows-server/get-started/kmsclientkeys
https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn502531(v=ws.11)
```
oke kalau begitu kita langsung saja menuju caranya.
1. pertama kalian pilih terlebih dahulu key nya
```
Professional: W269N-WFGWX-YVC9B-4J6C9-T83GX
Professional N: MH37W-N47XK-V7XM9-C7227-GCQG9
```
2. jika sudah buka command promt / cmd dan bisa juga powershell dengan run administrator, dengan cara tekan tombol windows + x di keyboard kemudian pilih sesuai gambar dibawah ini
<br>
{{< image src="/windows10/1.png" alt="cmd atau powershell" position="center" style="border-radius: 8px;" >}}
<br>
3. lalu gunakan perintah dibawah ini untuk menginstall lisensi key nya.
```
slmgr /ipk keylisensiyangkamubutuhkan
```
jangan lupa tekan tombol enter, apabila berhasil akan muncul seperti ini
<br>
{{< image src="/windows10/2.png" alt="sukses install key" position="center" style="border-radius: 8px;" >}}
<br>
4. kemudian ketikan dan masukan perintah ini untuk menghubungkan ke KMS server.
```
slmgr /skms kms8.msguides.com
```
kemudian tekan enter, dan apabila berhasil maka akan keluar tampilan seperti ini.
<br>
{{< image src="/windows10/3.png" alt="sukses konek kms server" position="center" style="border-radius: 8px;" >}}
<br>
5. langkah terakhir dalam aktifasi ini, ketikan perintah dibawah ini
```
slmgr /ato
```
tekan enter, maka jika berhasil akan muncul gambar seperti ini
<br>
{{< image src="/windows10/5.png" alt="suksess" position="center" style="border-radius: 8px;" >}}
<br>

<br>

Sudah selesai deh, kalian bisa menggunakan windows kalian sepenuhnya. dan gambar dibawah ini adalah bukti bahwa windows kita telah teraktivasi.
<br>
{{< image src="/windows10/6.png" alt="suksess" position="center" style="border-radius: 8px;" >}}
<br>

Oke baik begitulah cara nya, semoga bermanfaat. jika ada yang ingin di tanyakan tinggalkan komentar dibawah ya, dan share artikel ini ke kerabat kalian.