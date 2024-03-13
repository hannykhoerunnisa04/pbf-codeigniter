# HANNY KHOERUNNISA SETIADI-220102036

## Selamat Datang Di CI
CI adalah sebuah framework aplikasi berbasis PHP bersifat open source. Framework ini dipakai untuk membuat website cepat dan mudah, juga bersifat dinamis. CodeIgniter memberikan beragam fitur yang mempermudah proses pengembangan aplikasi, seperti sistem manajemen database yang kuat, pembuatan URL yang mudah dibaca, sistem templating, dan banyak lagi.
Singkatnya, CodeIgniter adalah kerangka kerja lunak yang mencoba menyediakan alat yang Anda butuhkan tanpa mengganggu.
## Persyaratan Server
- PHP and Required Extensions
- Optional PHP Extensions
- Supported Databases
### PHP dan Extension Yang diperlukan
- intl
- mbstring
- json

### Optional PHP Extensions
1. Ekstensi PHP berikut harus diaktifkan di server Anda:
- mysqlind. MySQL digunakan untuk menyimpan dan mengelola data dalam sebuah basis data, yang nantinya dapat diakses, dimanipulasi, dan diambil informasinya oleh aplikasi-aplikasi yang terhubung. 
- Crul atau Client URL. Sebuah software yang dipakai untuk mentransfer data dengan menggunakan protokol seperti HTTP ( Hypertext Transfer Protocol), HTTPS ( Hypertext Tranfer Protocol Secure), FTP ( File Transfer Protocol), dll.
- Imagick. Ekstensi dari php yang memungkinkan untuk memanipulasi gambar secara dinamis.
- gd. Sebuah library grafis yang menyediakan fungsi-fungsi untuk membuat dan memanipulasi gambar secara dinamis dalam PHP
- Simplexml. sebuah ekstensi PHP yang menyediakan fungsi-fungsi untuk mempermudah pengolahan dokumen berformat XML.
2. Ekstensi PHP berikut diperlukan saat Anda menggunakan server Cache:
- memcache adalah sebuah sistem caching yang cepat dan efisien yang digunakan untuk meningkatkan kinerja aplikasi web dengan menyimpan data yang sering diakses dalam memori.
- memcached adalah sebuah sistem caching berbasis memori yang terdistribusi dan open source
- Redis adalah ebuah sistem penyimpanan data berkinerja tinggi yang bersifat open-source dan berbasis memori.
### Basis Data Yang Didukung
- Mysql melalui mysql driver https://www.mysql.com/products/connector/
- PostrgreSQL melalui postgre driver https://jdbc.postgresql.org/download/
- SQLite 3 adalah sebuah perpustakaan perangkat lunak yang menyediakan basis data relasional (RDBMS) yang ringan, self-contained, dan bekerja tanpa server. Ini adalah sistem basis data yang berbasis berkas, yang berarti basis data disimpan dalam sebuah berkas tunggal yang dapat diakses dan diolah oleh program-program aplikasi. https://www.sqlite.org/
- Microsoft SQL Server https://www.microsoft.com/en-us/sql-server/sql-server-downloads
- Oracle DB https://www.oracle.com/id/database/
## Instalasi
### Melalui Composer
1. Ketikkan perintah ini di terminal pc masing-masing.
 ```shell
   composer create-project codeigniter4/appstarter project-root
 ```
2. Ketikkan perintah di terminal untuk masuk ke dalam  direktori untuk mengerucut direktori project-root
 ```shell
cd C:\laragon\www\project-root
```
3. Upgrade

```shell
composer update
```
4. Upgrade untuk versi terbaru
```shell
php builds development
```
5. Kembalikan ke rilis stabil
```shell
php builds release
```
### Instalasi Manual
1. Unduh [versi terbaru] (https://github.com/codeigniter4/framework/archive/v4.0.4.zip)
2. Setelah terinstal ekstrak folder zip yang sudah di instal.
### Struktur
app, public, tests, writable, system

### Server Pengembangan Lokal
1. Ketikkan perintah di terminal untuk memakai server pengembangan lokal
```shell
php spark serve
```
2. Ini akan meluncurkan server dan sekarang Anda dapat melihat aplikasi Anda di browser Anda di (http://localhost:8080) .
- Server pengembangan lokal dapat dikustomisasi dengan tiga opsi baris perintah:
Anda dapat menggunakan --hostopsi CLI untuk menentukan host berbeda untuk menjalankan aplikasi di:
```shell
php spark serve --host example.dev
```
Secara default, server berjalan pada port 8080 tetapi Anda mungkin menjalankan lebih dari satu situs, atau sudah memiliki aplikasi lain yang menggunakan port tersebut. Anda dapat menggunakan --portopsi CLI untuk menentukan opsi lain:
```shell
php spark serve --port 8081
```
Anda juga dapat menentukan versi PHP tertentu yang akan digunakan, dengan --phpopsi CLI, dengan nilainya disetel ke jalur eksekusi PHP yang ingin Anda gunakan:
```shell
php spark serve --php /usr/bin/php7.6.5.4
```
## Membuat aplikasi sederhana
### Static Pages






