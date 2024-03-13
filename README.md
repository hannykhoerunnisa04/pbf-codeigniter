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


