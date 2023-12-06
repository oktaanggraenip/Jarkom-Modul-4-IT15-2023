# Jarkom Modul 4 - IT15

|    Anggota Kelompok     |     NRP     |
| ---                     | ---         |
| Oktavia Anggraeni P.    | 5027211001  |
| Brigita Naraduhita P.P. | 5027211055  |

## Daftar Isi
- [VLSM](#VLSM)
- [CIDR](#CIDR)

Berikut tabel pembagian IP
[PembagianIP-IT15](https://docs.google.com/spreadsheets/d/1iyL7mE5pMhhtmgjTeYZ-ELqPOeAZv1WvcwdDAZ8P7GQ/edit?usp=sharing)

## <a name="VLSM"></a> VLSM
### Membuat Topologi VLSM menggunakan CPT
<img src="https://github.com/oktaanggraenip/Jarkom-Modul-4-IT15-2023/assets/102397053/afb43ea3-cd15-481e-94f7-0a359111607a">

Dari hasil pembagian subnet diketahui terdapat sejumlah 21 Subnet

### VLSM Tree
- Major network berada pada /19. 
- Prefix IP kelompok kami ialah 10.71.X.X

Berikut pohon perhitungan VLSM
<img src="https://github.com/oktaanggraenip/Jarkom-Modul-4-IT15-2023/assets/102397053/0a44699a-5e02-4c31-99b3-29bf46e90eea">

### Tabel Perhitungan
<img src="https://github.com/oktaanggraenip/Jarkom-Modul-4-IT15-2023/assets/102397053/bd2d7eea-7c81-43aa-b0e5-ef31a4038e88">

- Perhitungan dilakukan dengan mengurutkan subnet dari jumlah IP tertinggi (Usable IPs)
- Masukkan IP pada setiap node seperti yang ada pada modul, misalnya pada subnet A6
```bash
Subnet A6:
  NID: 10.71.0.0
  Netmask: 255.255.248.0
  IP range: 10.71.0.1 - 10.71.7.254
```
- Klik PC yang ingin diinputkan, lalu pilih desktop -> IP configuration sebagai berikut:

<img src="https://github.com/oktaanggraenip/Jarkom-Modul-4-IT15-2023/assets/102397053/e578026c-753f-4dac-add2-48f917551893">

- Lakukan setting pada bagian IPv4, Subnet Mask, dan Default Gateway

<img src="https://github.com/oktaanggraenip/Jarkom-Modul-4-IT15-2023/assets/102397053/ae935caf-8b85-4a76-976d-32acab3b94e9">

- Setelah subnet A6, selanjutnya mengatur IP pada setiap subnet sampai A21 sesuai hasil perhitungan sebelumnya. (Hasil perhitungan dapat dilihat pada [PembagianIP-IT15](https://docs.google.com/spreadsheets/d/1iyL7mE5pMhhtmgjTeYZ-ELqPOeAZv1WvcwdDAZ8P7GQ/edit?usp=sharing))
- Setelah seluruh node IP telah diatur maka selanjutnya melakukan routing agar semua node dapat terhubung.
- Lakukan ROUTING dengan mengisikan Network (Network Subnet yang ingin disambungkan), Mask(Mask Subnet yang ingin disambungkan), dan Next Hop (IP selanjutnya dari node yang sedang diinputkan)

<img src="https://github.com/oktaanggraenip/Jarkom-Modul-4-IT15-2023/assets/102397053/acfe2166-45fe-4a71-9c37-f7b9677b7db8">

- Selanjutnya memastikan semua node saling terhubung

<img src="https://github.com/oktaanggraenip/Jarkom-Modul-4-IT15-2023/assets/102397053/651e7143-e890-43f3-9a65-ddb13364f1a7">

<br>

## <a name="CIDR"></a> CIDR
### Membuat topologi CIDR menggunakan GNS3
<img src="https://i.ibb.co/n1Xwx6F/jarkom-topogns3.png" width="700">

### Proses penggabungan subnet pada CIDR
- Langkah 0 (A)
<img src="https://i.ibb.co/Y0LQcXF/jarkom-topo-gns.jpg" width="700">

- Langkah 1 (B)
<img src="https://i.ibb.co/YRCj51v/jarkom-1.jpg" width="700">

- Langkah 2 (C)
<img src="https://i.ibb.co/8sNkHKq/jarkom-2.jpg" width="700">

- Langkah 3 (D)
<img src="https://i.ibb.co/4mfjDs9/jarkom-3.jpg" width="700">

- Langkah 4 (E)
<img src="https://i.ibb.co/PccgTTh/jarkom-4.jpg" width="700">

- Langkah 5 (F)
<img src="https://i.ibb.co/wcLKHxm/jarkom-5.jpg" width="700">

- Langkah 6 (G)
<img src="https://i.ibb.co/WfqBmWs/jarkom-6.jpg" width="700">

- Langkah 7 (H)
<img src="https://i.ibb.co/RHbGnVR/jarkom-7.jpg" width="700">

### Pembagian CIDR
Berikut merupakan tabel pembagian subnet pada CIDR yang telah dilakukan sebelumnya
<img src="https://i.ibb.co/JHrKw9M/tabel-ip-cidr.png" width="700">

### CIDR Tree
Berikut merupakan tree CIDR yang diperoleh berdasarkan pembagian subnet sebelumnya
<img src="https://i.ibb.co/VLm2qgV/CIDR-IT15.jpg" width="700">

### Setting pada GNS
- Aura
```
auto eth0
iface eth0 inet dhcp  

auto eth1 # eisen
iface eth1 inet static
   address 10.71.24.132
   netmask 255.255.255.252
   broadcast 10.71.24.135

auto eth2 # denken
iface eth2 inet static
   address 10.71.24.128
   netmask 255.255.255.252
   broadcast 10.71.24.131

auto eth3 # frieren
iface eth3 inet static
   address 10.71.24.124
   netmask 255.255.255.252
   broadcast 10.71.24.127
```

- Eisen
```
auto eth0
iface eth0 inet static
   address 10.71.24.133
   netmask 255.255.255.252
   broadcast 10.71.24.135
   gateway 10.71.24.132

auto eth1
iface eth1 inet static
    address 10.71.24.136
    netmask 255.255.255.252
    broadcast 10.71.24.139
    gateway 10.71.24.132

auto eth2
iface eth2 inet static
    address 10.71.24.104
    netmask 255.255.255.248
    broadcast 10.71.24.111
    gateway 10.71.24.132

auto eth3
iface eth3 inet static
   address 10.71.24.144
   netmask 255.255.255.252
   broadcast 10.71.24.147
   gateway 10.71.24.132

auto eth4
iface eth4 inet static
    address 10.71.24.140
    netmask 255.255.255.252
    broadcast 10.71.24.143
    gateway 10.71.24.132
```

- Stark
```
    address 10.71.24.137
    netmask 255.255.255.252
    gateway 10.71.24.136
```

- Richter
```
    address 10.71.24.105
    netmask 255.255.255.248
    gateway 10.71.24.104
```

- Revolte
```
    address 10.71.24.106
    netmask 255.255.255.248
    gateway 10.71.24.104
```

- Linie
```
auto eth0
iface eth0 inet static
   address 10.71.24.145
   netmask 255.255.255.252
   broadcast 10.71.24.147
   gateway 10.71.24.144

auto eth1 # ke lawine
iface eth1 inet static
    address 10.71.24.148
    netmask 255.255.255.252
    broadcast 10.71.24.151
    gateway 10.71.24.144

auto eth2 
iface eth2 inet static
    address 10.71.20.0
    netmask 255.255.254.0
    broadcast 10.71.21.255
    gateway 10.71.24.144
```

- GranzChannel
```
auto eth0 
iface eth0 inet static
    address 10.71.20.1
    netmask 255.255.254.0
    gateway 10.71.20.0
```

- Lawine
```
auto eth0
iface eth0 inet static
    address 10.71.24.149
    netmask 255.255.255.252
    broadcast 10.71.24.151
    gateway 10.71.24.148

auto eth1 # ke heiter
iface eth1 inet static
    address 10.71.24.1
    netmask 255.255.252.192
    broadcast 10.71.24.63
    gateway 10.71.24.148

auto eth2
iface eth2 inet static
    address 10.71.24.0
    netmask 255.255.255.192
    broadcast 10.71.24.63
    gateway 10.71.24.148
```

- BredtRegion
```
auto eth0
iface eth0 inet static
    address 10.71.24.2
    netmask 255.255.255.192
    gateway 10.71.24.0
```
- Heiter
```
auto eth0
iface eth0 inet static
    address 10.71.24.3
    netmask 255.255.252.192
    broadcast 10.71.24.64
    gateway 10.71.24.1

auto eth1 # sein
iface eth1 inet static
    address 10.71.16.0
    netmask 255.255.252.0
    broadcast 10.71.19.255
    gateway 10.71.24.1

auto eth1 # riegelcanyon
iface eth1 inet static
    address 10.71.16.1
    netmask 255.255.252.0
    broadcast 10.71.19.255
    gateway 10.71.24.1
```

- Sein
```
auto eth0
iface eth0 inet static
    address 10.71.16.2
    netmask 255.255.252.0
    broadcast 10.71.19.255
    gateway 10.71.16.0
```

- RiegelCanyon
```
auto eth0
iface eth0 inet static
    address 10.71.16.3
    netmask 255.255.252.0
    gateway 10.71.16.1
```

- Lugner
```
auto eth0
iface eth0 inet static
   address 10.71.24.141
   netmask 255.255.255.252
   broadcast 10.71.24.143
   gateway 10.71.24.140

auto eth1
iface eth1 inet static
    address 10.71.12.0
    netmask 255.255.252.0
    broadcast 10.71.15.255
    gateway 10.71.24.140

auto eth2
iface eth2 inet static
    address 10.71.22.0
    netmask 255.255.255.0
    broadcast 10.71.22.255
    gateway 10.71.24.140
```

- TurkRegion
```
auto eth0
iface eth0 inet static
    address 10.71.12.1
    netmask 255.255.252.0
    gateway 10.71.12.0
```

- GrobeForest
```
auto eth0
iface eth0 inet static
    address 10.71.22.1
    netmask 255.255.252.0
    gateway 10.71.22.0
```

- Denken
```
auto eth0
iface eth0 inet static
    address 10.71.24.129
    netmask 255.255.255.252
    broadcast 10.71.24.131
    gateway 10.71.24.128

auto eth1 
iface eth1 inet static
    address 10.71.23.0
    netmask 255.255.255.0
    broadcast 10.71.23.255
    gateway 10.71.24.128

auto eth2
iface eth2 inet static
    address 10.71.23.2
    netmask 255.255.255.0
    broadcast 10.71.23.255
    gateway 10.71.24.128
```

- RoyalCapital
```
auto eth0
iface eth0 inet static
    address 10.71.23.1
    netmask 255.255.255.0
    gateway 10.71.23.0
```

- WillieRegion
```
auto eth0
iface eth0 inet static
    address 10.71.23.3
    netmask 255.255.255.0
    gateway 10.71.23.2
```

- Frieren
```
auto eth0
iface eth0 inet static
   address 10.71.24.125
   netmask 255.255.255.252
   broadcast 10.71.24.127
   gateway 10.71.24.124

auto eth1 #lakekorridor
iface eth1 inet static
    address 10.71.24.64
    netmask 255.255.255.224
    broadcast 10.71.24.95
    gateway 10.71.24.124

auto eth2 #flamme
iface eth2 inet static
    address 10.71.24.120
    netmask 255.255.255.252
    broadcast 10.71.24.123
    gateway 10.71.24.124
```

- LakeKorridor
```
auto eth0
iface eth0 inet static
    address 10.71.24.65
    netmask 255.255.255.224
    gateway 10.71.24.64
```

- Flamme
```
auto eth0
iface eth0 inet static
    address 10.71.24.121
    netmask 255.255.255.252
    broadcast 10.71.24.123
    gateway 10.71.24.120

auto eth1 #fern
iface eth1 inet static
    address 10.71.24.112
    netmask 255.255.255.252
    broadcast 10.71.24.115
    gateway 10.71.24.120

auto eth2 #rohrroad
iface eth2 inet static
    address 10.71.8.0
    netmask 255.255.252.0
    broadcast 10.71.11.255
    gateway 10.71.24.120

auto eth3 #himmel
iface eth3 inet static
    address 10.71.24.116
    netmask 255.255.255.252
    broadcast 10.71.24.119
    gateway 10.71.24.120
```

- Fern
```
auto eth0
iface eth0 inet static
    address 10.71.24.113
    netmask 255.255.255.252
    broadcast 10.71.24.115
    gateway 10.71.24.112

auto eth1
iface eth1 inet static
    address 10.71.0.0
    netmask 255.255.248.0
    broadcast 10.71.7.255
    gateway 10.71.24.112
```

- LaubHills
```
auto eth0
iface eth0 inet static
    address 10.71.0.1
    netmask 255.255.248.0
    gateway 10.71.0.0
```

- AppetitRegion
```
auto eth0
iface eth0 inet static
    address 10.71.0.2
    netmask 255.255.248.0
    gateway 10.71.0.0
```

- RohrRoad
```
auto eth0
iface eth0 inet static
    address 10.71.8.1
    netmask 255.255.252.0
    gateway 10.71.8.0
```

- Himmel
```
auto eth0
iface eth0 inet static
    address 10.71.24.117
    netmask 255.255.255.252
    broadcast 10.71.24.119
    gateway 10.71.24.116

auto eth1
iface eth1 inet static
    address 10.71.24.96
    netmask 255.255.255.248
    broadcast 10.71.24.103
    gateway 10.71.24.116
```

- SchwerMountains
```
auto eth0
iface eth0 inet static
    address 10.71.24.97
    netmask 255.255.255.248
    gateway 10.71.24.96
```

### Routing
Selanjutnya dilakukan routing pada sistem GNS dengan cara berikut
```
route add -net <NID subnet> netmask <netmask> gw <IP gateway>
```

- Aura (A3, A4, A6, A8, A9, A11, A14, A17, A18)
```
route add -net <10.71.24.112> netmask <255.255.255.252> gw <10.71.24.120>
route add -net <10.71.24.116> netmask <255.255.255.252> gw <10.71.24.120>
route add -net <10.71.24.120> netmask <255.255.255.252> gw <10.71.24.124>
route add -net <10.71.24.125> netmask <255.255.255.252> gw <10.71.24.124>
route add -net <10.71.24.129> netmask <255.255.255.252> gw <10.71.24.128>
route add -net <10.71.24.133> netmask <255.255.255.252> gw <10.71.24.132>
route add -net <10.71.24.140> netmask <255.255.255.252> gw <10.71.24.132>
route add -net <10.71.24.144> netmask <255.255.255.252> gw <10.71.24.132>
route add -net <10.71.24.148> netmask <255.255.255.252> gw <10.71.24.144>
```

- Eisen (A12, A13, A14, A15, A16)
```
route add -net <10.71.24.104> netmask <255.255.255.248> gw <10.71.24.132>
route add -net <10.71.24.105> netmask <255.255.255.248> gw <10.71.24.132>
route add -net <10.71.24.106> netmask <255.255.255.248> gw <10.71.24.132>
route add -net <10.71.24.136> netmask <255.255.255.252> gw <10.71.24.132>
route add -net <10.71.24.137> netmask <255.255.255.252> gw <10.71.24.136>
route add -net <10.71.24.140> netmask <255.255.255.252> gw <10.71.24.132>
route add -net <10.71.12.0> netmask <255.255.252.0> gw <10.71.24.140>
route add -net <10.71.22.0> netmask <255.255.255.0> gw <10.71.24.140>
```

- Linie (A21)
```
route add -net <10.71.20.0> netmask <255.255.254.0> gw <10.71.24.144>
route add -net <10.71.20.1> netmask <255.255.254.0> gw <10.71.20.0>
```

- Lawine (A19)
```
route add -net <10.71.24.0> netmask <255.255.255.192> gw <10.71.24.148>
route add -net <10.71.24.2> netmask <255.255.255.192> gw <10.71.24.0>
```

- Heiter (A20)
```
route add -net <10.71.16.0> netmask <255.255.252.0> gw <10.71.24.1>
route add -net <10.71.16.1> netmask <255.255.252.0> gw <10.71.24.1>
```

- Denken (A10)
```
route add -net <10.71.23.0> netmask <255.255.255.0> gw <10.71.24.128>
route add -net <10.71.23.2> netmask <255.255.255.0> gw <10.71.24.128>
```

- Frieren (A6, A7)
```
route add -net <10.71.24.120> netmask <255.255.255.252> gw <10.71.24.124>
route add -net <10.71.24.64> netmask <255.255.255.224> gw <10.71.24.124>
```

- Flamme (A2, A3, A4)
```
route add -net <10.71.8.0> netmask <255.255.252.0> gw <10.71.24.120>
route add -net <10.71.24.112> netmask <255.255.255.252> gw <10.71.24.120>
route add -net <10.71.24.116> netmask <255.255.255.252> gw <10.71.24.120>
route add -net <10.71.24.96> netmask <255.255.255.248> gw <10.71.24.116>
```

- Himmel (A5)
```
route add -net <10.71.24.97> netmask <255.255.255.248> gw <10.71.24.96>
```

- Fern (A1)
```
route add -net <10.71.0.0> netmask <255.255.248.0> gw <10.71.24.112>
route add -net <10.71.0.1> netmask <255.255.248.0> gw <10.71.0.0>
route add -net <10.71.0.2> netmask <255.255.248.0> gw <10.71.0.0>
```

- Kemudian jalankan command `iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.71.0.0/15` pada Aura
- Pastikan untuk memasukkan nameserver pada `etc/resolv.conf`
`echo "nameserver 192.168.122.1
nameserver 10.71.0.0" > /etc/resolv.conf`

### Kendala
- Proses routing sulit dan mengalami error

