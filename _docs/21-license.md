---
title: "Cara Install XAMPP di Windows dan Menjalankan Localhost"
permalink: /docs/license/
excerpt: "Cara Install XAMPP di Windows dan Menjalankan Localhost."
last_modified_at: 2018-01-10T11:22:01-05:00
header:
  teaser: "assets/pict/cara-install-xampp-di-windows-dan-menjalankan-localhost_website-apache-friends.png"
toc: true
toc_label: "Getting Started"
---

Salah satu aplikasi server localhost serta yang paling banyak digunakan dan cukup familiar di kalangan web developer saat ini adalah XAMPP.

Aplikasi XAMPP ini dibuat oleh Apache Friends dan installer-nya bisa langsung diunduh dari situs mereka. Isi aplikasinya juga sudah sangat komplit, antara lain:

Apache
MySQL
PHP
phpMyAdmin
FileZilla FTP Server
Tomcat
XAMPP Control Panel

Selain itu XAMPP juga sudah cross-platform, jadi bisa berjalan di MAC dan Linux, namun pada kesempatan kali ini kita hanya akan membahas XAMPP di Windows saja.

## Menginstall XAMPP di Windows
Pertama Anda harus kunjungi website [`Apache Friend`](https://www.apachefriends.org/) dan download XAMPP disana.

<figure class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/pict/cara-install-xampp-di-windows-dan-menjalankan-localhost_website-apache-friends.png" alt="Website Apache Friends">
</figure> 

Setelah selesai di download, selanjutnya tinggal jalankan file tersebut dengan melakukan klik dua kali pada file tersebut.

Selama proses instalasi, Anda mungkin akan mendapatkan beberapa peringatan seperti Windows menanyakan apakah Anda yakin ingin menginstall, dan lain sebagainya. Klik saja “Yes” untuk melanjutkan.

XAMPP Setup Wizard akan memandu Anda melalui proses instalasi. Klik Next

<figure class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/pict/cara-install-xampp-di-windows-dan-menjalankan-localhost_XAMPP-setup-wizard.png" alt="XAMPP setup wizard">
</figure>

Pada jendela berikutnya Anda akan diminta untuk memilih komponen apa saja yang ingin Anda install. Apache dan PHP secara otomatis akan terinstall maka keduanya tanda ceklis tidak bisa dihilangkan, sedangkan untuk yang lainnya masih bisa disesuaikan dengan kebutuhan Anda, namun untuk contoh kali ini pastikan Anda menceklis MySQL dan PHPMyAdmin karena ini akan sangat berguna untuk Anda nantinya.

<figure class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/pict/cara-install-xampp-di-windows-dan-menjalankan-localhost_XAMPP-pilihan-instalasi.png" alt="Pilihan instalasi di XAMPP">
</figure>

Next, pilih folder lokasi yang Anda inginkan untuk menginstall XAMPP pada komputer Anda, pada contoh ini kita coba untuk membuatnya di folder C:\Program Files\XAMPP.

<figure class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/pict/cara-install-xampp-di-windows-dan-menjalankan-localhost_memilih-folder-lokasi-XAMPP.png" alt="Memilih folder lokasi XAMPP">
</figure>

Selanjutnya, Anda akan ditanya apakah Anda ingin menginstall Bitnami for XAMPP, ini merupakan tool gratis untuk memudahkan Anda menginstall WordPress, Drupal dan Joomla.

Pada contoh kali ini kita tidak menginstall Bitnami karena nantinya kita ingin menginstall WordPress secara manual saja

<figure class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/pict/cara-install-xampp-di-windows-dan-menjalankan-localhost_bitnami-for-XAMPP.png" alt="Bitnami for XAMPP">
</figure>

Setelah semua pengaturan dipilih, XAMPP kini siap untuk di install ke komputer Anda. Klik Next untuk melanjutkan.

<figure class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/pict/cara-install-xampp-di-windows-dan-menjalankan-localhost_XAMPP-finish-install.png" alt="XAMPP selesai di install">
</figure>

Setelah XAMPP terinstall, Anda akan ditanya apakah Anda ingin memulai XAMPP Control Panel, yang menyediakan sebuah antarmuka untuk menjalankan lingkungan localhost Anda. Anda bisa ceklis pada pilihan ini lalu klik Finish.

<figure class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/pict/cara-install-xampp-di-windows-dan-menjalankan-localhost_XAMPP-finish-install2.png" alt="XAMPP selesai di install 2">
</figure>

Control Panel secara otomatis akan terbuka, namun apabila tadi Anda tidak menceklis pilihan, Anda bisa membukanya melalui folder XAMPP di komputer Anda, dan buka XAMPP Control Panel sebagai gantinya.

Maka tampilan XAMPP Control Panel akan terbuka seperti berikut ini.

<figure class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/pict/cara-install-xampp-di-windows-dan-menjalankan-localhost_XAMPP-control-panel.png" alt="XAMPP Control Panel">
</figure>

## Cara Menjalankan Aplikasi XAMPP
Biasanya jika saya menggunakan XAMPP, yang saya start hanyalah aplikasi Apache dan MySQL, karena saya tidak memerlukan aplikasi seperti Filezilla, dan lain-lain.

<figure class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/pict/cara-install-xampp-di-windows-dan-menjalankan-localhost_XAMPP-menjalankan-PHP-MySQL.png" alt="XAMPP menjalankan PHP MySQL">
</figure>

Kini proses instalasi berjalan dengan baik dan semuanya selesai dengan lancar, Anda bisa mencoba menjalankan http://localhost/ atau http://127.0.0.1 pada web browser Anda untuk memastikan apakah XAMPP sudah terinstall. Jika berhasil maka akan terlihat tampilan utama seperti gambar berikut ini.

<figure class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/pict/cara-install-xampp-di-windows-dan-menjalankan-localhost_tampilan-localhost.png" alt="Tampilan Localhost">
</figure>

