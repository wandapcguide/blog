---
title: "Fix eror mounting The disk contains an unclean file system"
date: 2020-03-22T22:07:00+07:00
draft: false
comments: true
---
hello guys, apa kabar nya ? semoga sehat selalu ya. hari ini saya ingin berbagi sesuatu tentang linux nih, apakah kalian dual boot dengan windows ? pernah gak sih kalian mengalami hal error mounting ? nah kalau pernah maka pas sekali. karena disini saya ingin membahas hal tersebut.
{{< image src="/eror_mounting/1.png" alt="Hello Friend" position="center" style="border-radius: 8px;" >}}

failed to mount blablabla please resume and shutdown windows fully (no hibernation or fast restarting) kenapa hal demikian dapat terjadi ? karena setau saya pada windows 10 itu shutdown nya tidak benar benar shutdown melainkan hibernation, mengapa demikian ? pada windows 10 terdapat fitur fastboot yang sebernarnya fitur tersebut di perkenal kan pada windows 8 yang dimana fitur fastboot tersebut mencampurkan proses shutdown dengan proses hibernasi dan oleh seba b itu pc dengan windows 10 booting nya lebih cepat ketimbang windows 7.
<br>
itu sebab nya mengapa kalian tidak dapat memounting partisi kalian di linux karena hardisk belum sepenuh nya bersih dari proses sebelum nya yaitu proses apa yang kalian lakukan di windows. lalu jika kalian baru saja menghapus windows nya, atau malas balik ke windows nya bagaimana dong ?? tenang masih bisa kok. mari kita simak cara nya di bawah ini..
<br>
kalian buka terminal lalu ketikan baris perintah ini<br>
```
$sudo ntfsfix /dev/sdaX
```
<br>
dimana X adalah angka dari jumlah partisi yang ada pada di perangkat kalian.
eitts, lakukan hal ini terhadap semua partisi kalian jika kalian menggunakan partisi kalian seluruhnya.

oke begitu saja tutorial nya, jika ada ketikan yang salah mohon benarkan di komentar hehe. serta jika ada yang ada ingin di tanyakan mohon tinggalkan komentar dan kita belajar bersama. and you not indonesian ? and you visiting this article and this site to learn ? we deserve some article using english, and it's not much. please using translate, to translate to your language and dont hesitate to comment using english cause we understand. 
