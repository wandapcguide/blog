---
title: "Cara sync nomor contact yang tersimpan di akun google pada microG"
date: 2020-03-23T00:19:20+07:00
draft: false
comments: true
---
halo guys, sudah lama ya gak update. kali ini saya kembali lagi dengan memberikan hal yang bermanfaat tentunya, walau saya jarang update tapi saya tetap berusaha agar mendapatakan pengalaman pengalaman.

bagi kamu yang pertama kali menginstall microG pasti akan bingung bagaimana caranya agar kontak yang sebelum nya tersimpan di akun google muncul kembali, namun pertama tama microG itu apa sih ? singkat nya microG adalah pengganti layanan google play yang open source, ringan, dan tidak mengonsumsi banyak daya.

lalu bagaimana agar kontak tersebut tersinkronasi kembali ? berikut cara dari mensikronasi nomor hp atau contact yang tersimpan di akun google pada microG :

cara :
1. siapkan googlecontactssync-all.tar.lz dari opengapps yang sesuai dengan versi android kalian (letak file tersebut berada didalam core folder pada zip dari opengapps) 
2. alu kalian ekstrak file tersebut (jika kalian tidak bisa membuka file .tar.lz kalian bisa menggunakan LINK INI disana banyak kalian bisa milih mau di konversi file apa saja)
mount /system menjadi RW (read write)
3. mount /system menjadi RW (read write)
4. jika sudah di ekstrak pindah kan folder GoogleContactsSyncAdapter beserta file apk didalam nya ke /System/App sehingga ururtan nya menjadi /System/App/GoogleContactsSyncAdapter 
5. lalu masih di /system/app, masuk ke dalam folder GoogleContacsSyncAdapter dan ganti permission atau ijin aplikasi menjadi 644 (Owner: read write, Group: read, Other: read)
6. reboot HH kalian
7. masuk ke pengaturan > aplikasi lalu pilih tampilkan sistem (atau yang menggunakan pengaturan bahasa inggris "Show System") 
{{< image src="/sync_contact/1.jpg" alt="Hello Friend" position="center" style="border-radius: 8px;" >}}
8. lalu disana pilih lah aplikasi bernama "Google Contact Sync' 
9. dan ijin kan akses yang ada seperti gambar dibawah ini.
{{< image src="/sync_contact/2.jpg" alt="Hello Friend" position="center" style="border-radius: 8px;" >}}
10. dan berikut hasilnya 
{{< image src="/sync_contact/3.jpg" alt="Hello Friend" position="center" style="border-radius: 8px;" >}}
maka berhasilah sudah memunculkan kontak kita kembali,dengan microG. bagaimana ? mudah bukan ?? karena sesuatu yang ingin kita capai itu tidak lah mudah (hahai) jika inigin ada yang ditanyakan silakan tanyakan 

(A : bang, kalo gitu berarti kita sama saja download opengapss juga dong ? 

Q : yaealah kan tinggal minta kekawan apa yang di perluin asalkan versi android nya sama lo yaa..

A: ane nolep bang

Q: se nolep nolepnya lo pasti lo punya kawan di medsos lo. wkwk banyak banyak bergaullah sekarang karena kalo udah lulus nanti lo gak bisa nolep teros), dan jangan lupa tinggal kan pertanyaan kalian di kolom komentar dibawah. sekian terimakasih kawan :D