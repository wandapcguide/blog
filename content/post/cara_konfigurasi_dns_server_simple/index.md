---
title: "[SIMPLE] Cara Konfigurasi DNS server pada debian 8"
date: 2017-11-20T14:24:40+07:00
draft: false
---

hai guys, apa kabar ? semoga sehat ya. kali ini saya akan mengarhcive tugas tugas sekolah saya yaitu tentang konfigurasi debian. pada kali ini saya akan membahas tentang dns atau domain name server. DNS (Domain Name Server) adalah server yang digunakan untuk mengetahui IP Address suatu host lewat host name-nya. jadi kalian jika ingin ke sebuah situs kalian tidak perlu mengetik ip nya tetapi cukup dengan namanya saja, facebook(.)com misalkan. oke inilah cara untuk mengkonfigurasi dns pada debian 5, 6, 7, 8 ikuti langkah dibawah ini.

install packet nya terlebih dahulu yaitu bind9
```
apt-get install bind9
```

lalu jika sudah ketikan ini
```
cd /etc/bind/
```

lalu ketikan ini
```
nano named.conf.local
```

didalam nano tadi ketikan ini dibawah text ini //include "/etc/bind/zones.rfc1918"; 
```
zone "wandaaja.com" {
            type master;
            file "/etc/bind/db.nda";
};
zone "2.168.192.in.addr-arpa" {
            type master;
            file "/etc/bind/db.192";
}; 
```

save lalu exit dari nano, kemudian ketikan ini 
```
cp db.local db.nda (enter)
cp db.127 db.192 (enter)
```

lalu ketikan ini 
```
nano db.nda
```

maka akan muncul seperti ini 
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    localhost. root.localhost. (
                  2             ; Serial
             604800        ; Refresh
              86400         ; Retry
            2419200       ; Expire
             604800 )      ; Negative Cache TTL
;
@    IN    NS         localhost.
@    IN    A           127.0.0.1
@    IN    AAAA    ::1
```

maka ganti hingga seperti ini 
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    wandaaja.com. root.wandaaja.com. (
                  2             ; Serial
             604800        ; Refresh
              86400         ; Retry
            2419200       ; Expire
             604800 )      ; Negative Cache TTL
;
@           IN    NS    wandaaja.com.
@          IN    A    192.168.2.1
www     IN    A    192.168.2.1
ntp       IN    A    192.168.2.1
ftp        IN    A    192.168.2.1
mail      IN    A    192.168.2.1
```

jika sudah save lalu keluar dari nano, kemudian ketikan ini 
```
nano db.192
```

maka akan tampil seperti ini 
```
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@    IN    SOA    localhost. root.localhost. (
                  1             ; Serial
             604800        ; Refresh
              86400         ; Retry
            2419200       ; Expire
             604800 )      ; Negative Cache TTL
;
@           IN    NS      localhost.
1.0.0      IN    PTR    localhost.
```

maka ganti hingga menjadi seperti ini 
```
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@    IN    SOA    wandaaja.com. root.wandaaja.com. (
                  1             ; Serial
             604800        ; Refresh
              86400         ; Retry
            2419200       ; Expire
             604800 )      ; Negative Cache TTL
;
@   IN    NS      wandaaja.com.
1    IN    PTR    wandaaja.com.
```

save lalu keluar dari nano dan ketikan
```
nano /etc/resolv.conf
```

lalu ketikan ini didalam nya
```
search wandaaja.com
nameserver 192.168.2.1
```

save dan keluar dari nano kemudian ketikan ini untuk mersetart packet atau konfigurasi dns nya
```
/etc/init.d/bind9 restart
```

kemudian untuk pengujian anda bisa lakukan ping dan nslookup ke domain yang anda buat contoh
```
ping www.wandaaja.com (enter)
nslookup www.wandaaja.com (enter)
```

note : 

1. jika kalian ada bacaan server can't find : NXDOMAIN berarti itu ada yang salah

2. wandaaja.com bisa diganti dengan nama domain mu lalu sesuaikan.

3. ip juga bebas tergantung gurunya

4. localhost itu diganti dengan nama domain mu misal wandapcguide(.)org

5. jika mau tau log eror nya didebian gunakan cat /var/log/syslog  | grep nama paket misal grep bind

6. jika hanya di bind9 saja bisa gunakan named-checkconf 