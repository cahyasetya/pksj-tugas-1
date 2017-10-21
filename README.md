# Tugas 1 Uji Penetrasi 1
## Instalasi Virtual Box
1. Install virtual box
![installvirtualbox](intsall-virtual-box.png)  
Jalankan code tersebut pada terminal anda. Namun, sebelumnya run command **sudo apt-get update** terlebih dahulu. lalu jalankan **sudo apt-get install virtualbox**.

## Instalasi Ubuntu Server
1. Memberi Nama Virtual Mesin  
![memberi nama](1.ubuntu-server-memberi-nama.png)

2. Mengalokasikan Memori untuk Virtual Mesin
![mengalokasikan memori](2.ubuntu-server-mengalokasikan-memori.png)

3. Membuat Virtual Hardisk  
![membuat virtual hardisk](3.ubuntu-server-virutal-hdd.png)

4. Memilih Tipe Virtual Hardisk
![memilih virtual hardisk](4.ubuntu-server-virtual-hdd-type.png)

5. Mengalokasikan Storage
![mengalokasikan storage](5.ubuntu-server-alokasi-storage.png)

6. Memilih Mekanisme Alokasi Storage
![mekanisme alokasi storage](6.ubuntu-server-storage-on-physical-hdd.png)

7. Virtual Mesin telah Ditambahkan
![virtual mesin ditambahkan](40.virtual-mesin-created.png)  
klik **Start** untuk memulain instalasi

## Instalasi Ubuntu Desktop
1. Memberi Nama Virtual Mesin  
![memberi nama](langkah-2.png)  

2. Mengalokasikan Memori untuk Virtual Mesin
![mengalokasikan memori](langkah-3.png)

3. Membuat Virtual Hardisk  
![membuat virtual hardisk](langkah-4.png)

4. Memilih Tipe Virtual Hardisk
![memilih virtual hardisk](langkah-5.png)

5. Mengalokasikan Storage  
![mengalokasikan storage](langkah-6.png)  

6. Memilih Mekanisme Alokasi Storage
![mekanisme alokasi storage](langkah-7.png)

7. Virtual Mesin telah Ditambahkan
![virtual mesin ditambahkan](langkah-1.png)

8. Menambahkan disk file ke Virtual Mesin  
![menambahkan disk file](langkah-9.png)  

9. Memulai Instalasi Ubuntu Desktop di Virtual Mesin
![memulai instalasi ubuntu desktop](langkah-11.png)  
Klik **Install Ubuntu** untuk memulai instalasi

10. Persiapan Instalasi
![persiapan instalasi](langkah-12.png)  

11. Memilih jenis instalasi  
![memilih jenis instalasi](langkah-13.png)  

12. Membuat perubahan pada disk yang ingin diinstall  
![buat perubahan pada disk](langkah-14.png)  

13. Memilih Zona Waktu
![pilih zona waktu](langkah-15.png)  

14. Mengidentifikasi keyboard layout
![identifikasi keyboard](langkah-16.png)

15. Mengisikan username dan password
![isi username dan password](langkah-17.png)

16. Proses Instalasi  
![instalasi](langkah-18.png)  
Tunggu hingga proses instalasi selesai.

17. Reboot
![reboot](langkah-19.png)
Setelah proses instalasi selesai, reboot dan ubuntu desktop siap digunakan.

## Uji Penetrasi Ubuntu Desktop
1. Install Open SSH server  
![installopenssh](intsalasi-openssh-server.png)  
Install OpenSSH-server pada ubuntu desktop yang ada di virtual mesin. Namun, jalankan **sudo apt-get update** terlerbih dahulu. Lalu jalankan **sudo apt-get install openssh-server**
 
2. Install Hydra pada komputer 
