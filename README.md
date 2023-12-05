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

### CIDR Tree
Berikut merupakan tree CIDR yang diperoleh berdasarkan pembagian subnet sebelumnya
<img src="https://i.ibb.co/VLm2qgV/CIDR-IT15.jpg" width="700">
