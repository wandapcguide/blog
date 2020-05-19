---
title: "Cara membuat bootable dan multi bootable dengan mudah dengan Ventoy"
date: 2020-05-19T06:44:31+07:00
draft: false
comments: true
---

Hi guys, dimanapun kalian berada saat membaca blog kami semoga sehat selalu dan terhindar dari virus corona ini. Pada kesempatan disituasi #DirumahAja semoga tetap produktif, untuk menunjang produktifitas kita semua saya akan berbagi info mengenai bootable pada flash drive atau biasa kita sebut flash disk. Ada sebuah tool yang memudahkan kita untuk membuat dua bootable atau bahkan lebih pada satu buah flash drive atau flashdisk, yaitu [ventoy](https://www.ventoy.net/en/index.html). 
<br>

Ventoy ini merupakan tool opensource yang digunakan untuk membuat bootable ISO file pada flashdrive atau flashdisk yang dimana pembedanya, kita tidak perlu memformat berulang ulang flashdrive ketika kita hendak membuat bootable dari ISO file yang lain jadi hanya tinggal mengcopy kan banyak ISO file sesuai kebutuhan kita kedalam flashdrive lalu tinggal pakai (support BIOS Legacy maupun UEFI). Ventoy tersedia untuk Sistem Operasi windows dan linux, jadi makin lebih gampang pula kalian saat di linux untuk membuat bootable di flashdisk kalian.
<br>
{{< image src="/ventoy/1.png" alt="ventoy" position="center" style="border-radius: 8px;" >}}
<br>

Berikut keunggulan ventoy diantaranya:

● 100% opensource

● simple to use

● suport Legacy+UEFI

● direct boot melalui ISO file dan tak perlu di ekstak.

● ISO file dengan ukuran lebih dari 4GB support.

Dan masih banyak lagi, serta Hal yang menarik saya untuk membuat artikel ini adalah dengan keunggulan direct boot nya yang membuat kita semua menjadi mudah untuk membuat bootabe, sehingga tak perlu repot dan menghemat umur flashdrive itu sendiri.
<br>

Cara menggunakan ventoy sangatlah gampang sekali, dan saya sangat merekomendasikan tool ini karena cocok untuk kalangan pro dan juga pemula. Baiklah, berikut dibawah ini cara cara nya :
1. Download ventoy sesuai OS yang anda gunakan sekarang. (Kebetulan Saya menggunakan windows jadi jika anda menggunakan linux tinggal ikuti saja instruksi pada cli nya nanti karena file pada linux berekstensi .sh di windows nya juga mudah sekali jadi pada linux nya juga mudah hanya berbasis cli saja) 
2. Ekstrak file ventoy nya
3. Kemudian cari file Ventoy2Disk.exe (Ventoy2Disk.sh kalau pada linux) pada folder hasil ekstrak tadi kemudian double klik file exe tersebut jika ada prompt yes atau no pilih saja yes karena ventoy ini butuh administrator untuk melakukan operasi nya (kalau di linux jalankan dengan ./Ventoy2Disk.sh)
4. Laly klik INSTALL jika muncul prompt untuk memformat flashdisk klik yes jika muncul lagi klik yes lagi. Unik nya ventoy ini jika ada versi terbaru kalian tidak peru memformat ulang flashdisk kalian hanya klik update saja.
{{< image src="/ventoy/2.jpg" alt="ventoy" position="center" style="border-radius: 8px;" >}}
5. Lalu tunggu installasi selesai
6. Jika sudah nanti kalian akan melihat isi dari flashdisk kalian kosong dan nama nya pun berganti menjadi ventoy lalu kalian bisa mengcopy ISO file kalian kedalam fashdisk tersebut, kalian dapat mengcopy file nya bebas dalam flashdisk tersebut di folder manapun nanti si ventoy nya akan mendeteksi otomatis letak ISO file didalam flashdisk tersebut.
{{< image src="/ventoy/3.png" alt="ventoy" position="center" style="border-radius: 8px;" >}}
7. Dan here we go.. Masuklah boot option jika sukses maka tampilan akan seperti ini
{{< image src="/ventoy/4.jpg" alt="ventoy" position="center" style="border-radius: 8px;" >}}
Dan setelah boot masuk ke iso seperti ini
{{< image src="/ventoy/5.jpg" alt="ventoy" position="center" style="border-radius: 8px;" >}}
<br>

Sudah 200+ iso file yg compatible dengan ventoy untuk lebih detil bisa kunjungi situs ventoy disini. Dan jika ada pertanyaan, dan sebagainya silakan tinggalkan komentar dibawah ini. Sekian dan terimakasih semoga sehat selalu.