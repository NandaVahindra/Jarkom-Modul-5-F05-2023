# Jarkom-Modul-5-F05-2023
Apta Rasendriya Wijaya - 5025211139  
Made Nanda Wija Vahindra - 5025211160  


## Topologi
Berikut topologi yang digunakan pada praktikum modul 5:
![image](https://github.com/NandaVahindra/Jarkom-Modul-5-F05-2023/assets/116022017/fa3144e2-145d-4515-a28c-46310bc6b2a3)

## VLSM
Berikut pembagian rute untuk topologi diatas:

![image](https://github.com/NandaVahindra/Jarkom-Modul-5-F05-2023/assets/116022017/b1b8a1c0-8406-41f6-a10c-6882e3307994)

![image](https://github.com/NandaVahindra/Jarkom-Modul-5-F05-2023/assets/116022017/6d14ce05-00bf-4c98-bf02-c6ebdc84ea15)

Berikut tree pembagian IP:

![image](https://github.com/NandaVahindra/Jarkom-Modul-5-F05-2023/assets/116022017/bc1eb940-f4fc-4275-8dae-cf51b98fc078)

## Konfigurasi
Berikut konfigurasi pada masing-masing router, client, dan server untuk melakukan subnetting:

- Revolte
```
#Revolte
auto eth0
iface eth0 inet static
    address 10.54.0.1
    netmask 255.255.255.252
    gateway 10.54.0.2
```
- Richter
```
#Richter
auto eth0
iface eth0 inet static
    address 10.54.0.5
    netmask 255.255.255.252
    gateway 10.54.0.6
```
- Fern
```
#Fern
#a1
auto eth0
iface eth0 inet static
    address 10.54.0.6
    netmask 255.255.255.252
#a2
auto eth1
iface eth1 inet static
    address 10.54.0.2
    netmask 255.255.255.252
#a3
auto eth2
iface eth2 inet static
    address 10.54.0.129
    netmask 255.255.255.128
    gateway 10.54.0.130
```
- SchewerMountain
```
#SchewerMountain
auto eth0
iface eth0 inet dhcp
```
- Himmel
```
#Himmel
#a3
auto eth2
iface eth2 inet static
    address 10.54.0.130
    netmask 255.255.255.128
#a4
auto eth0
iface eth0 inet static
    address 10.54.2.1
    netmask 255.255.254.0
#a5
auto eth1
iface eth1 inet static
    address 10.54.0.9
    netmask 255.255.255.252
    gateway 10.54.0.10

up route add -net 10.54.0.0 netmask 255.255.255.252 gw 10.54.0.129
up route add -net 10.54.0.4 netmask 255.255.255.252 gw 10.54.0.129
```
- Frieren
```
#Frieren
#a5
auto eth1
iface eth1 inet static
    address 10.54.0.10
    netmask 255.255.255.252
#a6
auto eth0
iface eth0 inet static
    address 10.54.0.14
    netmask 255.255.255.252
#a7
auto eth2
iface eth2 inet static
    address 10.54.0.17
    netmask 255.255.255.252
    gateway 10.54.0.18

up route add -net 10.54.0.0 netmask 255.255.255.252 gw 10.54.0.9
up route add -net 10.54.0.4 netmask 255.255.255.252 gw 10.54.0.9
up route add -net 10.54.0.128 netmask 255.255.255.128 gw 10.54.0.9
up route add -net 10.54.2.0 netmask 255.255.254.0 gw 10.54.0.9
```
- Stark
```
#Stark
auto eth0
iface eth0 inet static
    address 10.54.0.13
    netmask 255.255.255.252
    gateway 10.54.0.14
```
- Aura
```
#Aura
auto eth0
iface eth0 inet dhcp
#a5
auto eth1
iface eth1 inet static
    address 10.54.0.21
    netmask 255.255.255.252
#a7
auto eth2
iface eth2 inet static
    address 10.54.0.18
    netmask 255.255.255.252

up route add -net 10.54.0.0 netmask 255.255.255.252 gw 10.54.0.17
up route add -net 10.54.0.4 netmask 255.255.255.252 gw 10.54.0.17
up route add -net 10.54.0.128 netmask 255.255.255.128 gw 10.54.0.17
up route add -net 10.54.2.0 netmask 255.255.254.0 gw 10.54.0.17
up route add -net 10.54.0.8 netmask 255.255.255.252 gw 10.54.0.17
up route add -net 10.54.0.12 netmask 255.255.255.252 gw 10.54.0.17

up route add -net 10.54.8.0 netmask 255.255.248.0 gw 10.54.0.22
up route add -net 10.54.4.0 netmask 255.255.252.0 gw 10.54.0.22
```
- TurkRegion
```
#TurkRegion
auto eth0
iface eth0 inet dhcp
```
- Heiter
```
#Heiter
#a8
auto eth1
iface eth1 inet static
    address 10.54.0.22
    netmask 255.255.255.252
    gateway 10.54.0.21
#a9
auto eth0
iface eth0 inet static
    address 10.54.8.1
    netmask 255.255.248.0
#a10
auto eth2
iface eth2 inet static
    address 10.54.4.1
    netmask 255.255.252.0
```
- Sein
```
#Sein
#a5
auto eth0
iface eth0 inet static
    address 10.54.4.2
    netmask 255.255.252.0
    gateway 10.54.4.1
```
- GrobeForest
```
#GrobeForest
auto eth1
iface eth1 inet dhcp
```

## Setup DHCP

- **Revolte (DHCP Server)**

```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt update
apt install isc-dhcp-server -y
echo "INTERFACESv4=\"eth0\"
INTERFACESv6=\"\"" > /etc/default/isc-dhcp-server

# 1 2
echo "
subnet 10.54.0.0 netmask 255.255.255.252 {

}

subnet 10.54.0.4 netmask 255.255.255.252 {

}

subnet 10.54.0.128 netmask 255.255.255.128 {
    range 10.54.0.131 10.54.0.254;
    option routers 10.54.0.130;
    option broadcast-address 10.54.0.255;
    option domain-name-servers 10.54.0.5;
}

subnet 10.54.2.0 netmask 255.255.254.0 {
    range 10.54.2.2 10.54.3.254;
    option routers 10.54.2.1;
    option broadcast-address 10.54.3.255;
    option domain-name-servers 10.54.0.5;
}

subnet 10.54.0.8 netmask 255.255.255.252 {

}

subnet 10.54.0.12 netmask 255.255.255.252 {

}

subnet 10.54.0.16 netmask 255.255.255.252 {

}

subnet 10.54.0.20 netmask 255.255.255.252 {

}

subnet 10.54.8.0 netmask 255.255.248.0 {
    range 10.54.8.2 10.54.15.254;
    option routers 10.54.8.1;
    option broadcast-address 10.54.15.255;
    option domain-name-servers 10.54.0.5;
}

subnet 10.54.4.0 netmask 255.255.252.0 {
    range 10.54.4.3 10.54.7.254;
    option routers 10.54.4.1;
    option broadcast-address 10.54.7.255;
    option domain-name-servers 10.54.0.5;
}" > /etc/dhcp/dhcpd.conf

service isc-dhcp-server stop
service isc-dhcp-server start
service isc-dhcp-server status
```

- **Heiter dan Himmel (DHCP Relay)**

```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt update
apt install isc-dhcp-relay -y
echo "
SERVERS=\"10.54.0.1\" # IP Dhcp server
INTERFACES=\"eth0 eth1 eth2\"
OPTIONS=\"\"
" >  /etc/default/isc-dhcp-relay
echo "net.ipv4.ip_forward=1" >  /etc/sysctl.conf
service isc-dhcp-relay start
service isc-dhcp-relay restart
```

- **Richer (DNS Server)**

```
apt-get update
apt-get install bind9 -y

echo "options {
        directory \"/var/cache/bind\";
        forwarders {
            192.168.122.1;
        };
        allow-query{any;};

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};" > /etc/bind/named.conf.options
```

- **Stark dan Sein (Web Server)**

```
echo 'nameserver 192.168.122.1 ' > /etc/resolv.conf
apt update
apt install apache2 -y
apt-get install netcat -y
service apache2 start
echo "$HOSTNAME" > /var/www/html/index.html
```

## Soal 1
> Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Aura menggunakan iptables, tetapi tidak ingin menggunakan MASQUERADE.

Berikut rule yang harus dimasukkan pada Aura supaya topologi dapat mengakses keluar:
```
iptables -t nat -A POSTROUTING -s 10.54.0.0/20 -o eth0 -j SNAT --to-source $(hostname -I | awk '{print $1}')
```
Karena tugas NAT melibatkan akses ke jaringan luar, penggunaan tabel yang relevan adalah tabel nat dengan penggunaan sintaks `-t nat`. NAT beroperasi dengan mentranslasikan IP pada topologi ke satu IP yang sama. Oleh karena itu, chain yang diterapkan adalah POSTROUTING, dengan target SNAT dan sumbernya adalah NID Topologi, yaitu `10.54.0.0/20`. Interface Aura yang terkait dengan NAT adalah `eth0`, sehingga menggunakan sintaks -o eth0 dan IP yang digunakan adalah IP yang pertama. IP interface yang digunakan oleh Aura dapat diakses melalui perintah `hostname -I` karena NAT terhubung dengan eth0 itu menggunakan dhcp yang mana IP yang digunakan berubah-ubah, sehingga menggunakan sintaks `--to-source $(hostname -I | awk '{print $1}')`.

Berikut hasil config dengan test diluar dari host Aura:
![image](https://github.com/NandaVahindra/Jarkom-Modul-5-F05-2023/assets/116022017/e4f359d5-5acf-44e6-9bff-34d158b07c9d)

## Soal 7
> Karena terdapat 2 WebServer, kalian diminta agar setiap client yang mengakses Sein dengan Port 80 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan dan request dari client yang mengakses Stark dengan port 443 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan.

kita dapat menambahakan config di router Heiter untuk config port 80 dan 443:
```
iptables -A PREROUTING -t nat -p tcp --dport 80 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 10.54.4.2:80
iptables -A PREROUTING -t nat -p tcp --dport 80 -j DNAT --to-destination 10.54.0.13:80
iptables -A PREROUTING -t nat -p tcp --dport 443 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 10.54.0.13:80
iptables -A PREROUTING -t nat -p tcp --dport 443 -j DNAT --to-destination 10.54.4.2:80
```

Penjelasannya:

- `iptables -A PREROUTING`: Menambahkan sebuah aturan ke dalam rantai `PREROUTING` dari tabel `nat`. Rantai `PREROUTING` digunakan untuk mengatur alamat tujuan paket sebelum routing, yaitu sebelum keputusan mengenai ke mana paket akan dikirim diambil.

- `-t nat`: Menunjukkan bahwa aturan yang ditambahkan berada di dalam tabel `nat`, yang biasanya digunakan untuk NAT (Network Address Translation).

- `-p tcp`: Menentukan bahwa aturan ini hanya berlaku untuk protokol TCP, yang merupakan protokol tingkat transport yang umum digunakan.

- `--dport 80` dan `--dport 443`: Ini menentukan bahwa aturan hanya berlaku untuk paket data yang ditujukan ke port 80 dan port 443.

- `-m statistic`: Ini memanggil modul `statistic` yang digunakan untuk mencocokkan paket berdasarkan statistik tertentu.

- `--mode nth --every 2 --packet 0`: Ini adalah pengaturan dari modul `statistic`. Mode `nth` digunakan untuk mencocokkan setiap paket ke-N. Dalam hal ini, `--every 2` yang berarti setiap paket kedua akan dicocokkan, mulai dari `--packet 0` (paket pertama).

- `-j DNAT`: Menentukan tindakan `DNAT` (Destination Network Address Translation), yang mengubah alamat tujuan paket.

- `--to-destination 10.54.4.2:80` dan `--to-destination 10.54.0.13:80`: Menentukan alamat tujuan baru untuk paket yang cocok, dimana paket akan diarahkan ulang ke `10.54.4.2` dan `10.54.0.13`.

berikut hasil config:
![image](https://github.com/NandaVahindra/Jarkom-Modul-5-F05-2023/assets/116022017/58cd349e-2e42-4581-a2d1-6dcd95c40238)


## Soal 8
> Karena berbeda koalisi politik, maka subnet dengan masyarakat yang berada pada Revolte dilarang keras mengakses WebServer hingga masa pencoblosan pemilu kepala suku 2024 berakhir. Masa pemilu (hingga pemungutan dan penghitungan suara selesai) kepala suku bersamaan dengan masa pemilu Presiden dan Wakil Presiden Indonesia 2024.

config di webserver:

```
iptables -A INPUT -s 10.54.0.0/30 -m time --datestart 2024-02-14T00:00:00 --datestop 2024-06-26T00:00:00 -j DROP
```

 Berikut penjelasannya:

- `iptables -A INPUT`: Menambahkan aturan ke rantai `INPUT`. Rantai `INPUT` digunakan untuk memutuskan nasib paket yang masuk ke sistem.
  
- `-s 10.54.0.0/30`: Menentukan sumber (source) paket yang akan masuk yaitu  `10.54.0.0/30` yang merupakan subnet dari revolte.

- `-m time`: Ini memanggil modul `time` yang digunakan untuk membatasi aturan berdasarkan waktu.

- `--datestart 2024-02-14T00:00:00 --datestop 2024-06-26T00:00:00`: Mendefinisikan rentang waktu di mana aturan ini aktif yaitu tanggal 14 Februari 2024 pukul 00:00 hingga tanggal 26 Juni 2024 pukul 00:00.

- `-j DROP`: Yang berarti paket akan dibuang.

berikut hasil config:
![image](https://github.com/NandaVahindra/Jarkom-Modul-5-F05-2023/assets/116022017/9892c943-0fc2-4735-8cad-b9bc5005b436)

## Soal 9
> Sadar akan adanya potensial saling serang antar kubu politik, maka WebServer harus dapat secara otomatis memblokir  alamat IP yang melakukan scanning port dalam jumlah banyak (maksimal 20 scan port) di dalam selang waktu 10 menit. 

config di webserver:

```
iptables -N scanning_tab
iptables -A INPUT -m recent --name scanning_tab --update --seconds 600 --hitcount 20 -j DROP
iptables -A INPUT -m recent --name scanning_tab --set -j ACCEPT
```

 Berikut penjelasannya:

- `iptables`: Ini adalah perintah untuk mengonfigurasi `iptables`, sebuah tool untuk mengatur aturan firewall di Linux.

- `-N scanning_tab`: Opsi `-N` digunakan untuk membuat rantai baru. `scanning_tab` di sini adalah nama yang diberikan untuk rantai baru ini.

 Berikut penjelasannya:

- `iptables -A INPUT`: Ini menambahkan aturan ke rantai `INPUT`, yang mengatur paket data yang masuk ke sistem.

- `-m recent`: Modul `recent` digunakan untuk melacak paket yang diterima dari alamat IP tertentu. Modul ini memungkinkan Anda membuat keputusan berdasarkan jumlah paket yang diterima dari alamat IP tersebut dalam jangka waktu tertentu.

- `--name scanning_tab`: Ini menentukan nama daftar yang digunakan oleh modul `recent` untuk melacak. Dalam kasus ini, "scanning_tab" adalah nama yang diberikan. Ini harus sesuai dengan nama rantai atau daftar yang telah Anda definisikan sebelumnya.

- `--update`: Opsi ini memperbarui waktu terakhir sebuah paket diterima dari alamat IP tertentu.

- `--seconds 600`: Ini menentukan periode waktu untuk melacak. Dalam hal ini, aturan akan mempertimbangkan paket yang diterima dalam 600 detik (10 menit) terakhir.

- `--hitcount 20`: Ini menetapkan jumlah paket yang diperlukan untuk memicu aturan. Dalam hal ini, jika lebih dari 20 paket diterima dari alamat IP yang sama dalam 600 detik, aturan ini akan aktif.

- `-j DROP`: Yang berarti paket akan dibuang.

berikut hasil config:
![image](https://github.com/NandaVahindra/Jarkom-Modul-5-F05-2023/assets/116022017/f675cc91-0db4-46f9-933a-aa6c253e3863)


## Soal 10
> Karena kepala suku ingin tau paket apa saja yang di-drop, maka di setiap node server dan router ditambahkan logging paket yang di-drop dengan standard syslog level. 


## Kendala Pengerjaan
- `syslog` pada `/var/log/syslog` tidak mau update meskipun paket sudah masuk dalam ip host sehingga tidak bisa mengerjakan nomer 10
