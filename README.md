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
Server pengembangan lokal dapat dikustomisasi dengan tiga opsi baris perintah:
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
1. Menetapkan aturan perutean
Mari kita siapkan aturan perutean. Buka file rute yang terletak di app/Config/Routes.php .
```shell
<?php

use CodeIgniter\Router\RouteCollection;

/**
 * @var RouteCollection $routes
 */
$routes->get('/', 'Home::index');
```
Tambahkan baris berikut, setelah arahan rute untuk '/'.
```shell
use App\Controllers\Pages;

$routes->get('pages', [Pages::class, 'index']);
$routes->get('(:segment)', [Pages::class, 'view']);
```
2. Buat controller pages
Buat file di app/Controllers/Pages.php dengan kode berikut.
```shell
<?php

namespace App\Controllers;

class Pages extends BaseController
{
    public function index()
    {
        return view('welcome_message');
    }

    public function view($page = 'home')
    {
        // ...
    }
}
```
3. Buat tampilan
Buat header di app/Views/templates/header.php dan tambahkan kode berikut:
```shell
<!doctype html>
<html>
<head>
    <title>CodeIgniter Tutorial</title>
</head>
<body>

    <h1><?= esc($title) ?></h1>
```
4. Sekarang, buat footer di app/Views/templates/footer.php yang menyertakan kode berikut:
```shell
<em>&copy; 2022</em>
</body>
</html>
```
5. Menambahkan logika ke controller
Badan halaman statis akan ditempatkan di direktori app/Views/pages .
Di direktori itu, buat dua file bernama home.php dan about.php . Di dalam file tersebut, ketikkan beberapa teks - apa pun yang Anda suka - dan simpan. Jika Anda ingin tampil tidak orisinal, cobalah “Hello World!”.
```shell
<?php

namespace App\Controllers;

use CodeIgniter\Exceptions\PageNotFoundException; // Add this line

class Pages extends BaseController
{
    // ...

    public function view($page = 'home')
    {
        if (! is_file(APPPATH . 'Views/pages/' . $page . '.php')) {
            // Whoops, we don't have a page for that!
            throw new PageNotFoundException($page);
        }

        $data['title'] = ucfirst($page); // Capitalize the first letter

        return view('templates/header', $data)
            . view('pages/' . $page)
            . view('templates/footer');
    }
}
```
6. Coba untuk menjalankan aplikasi
Sekarang kunjungi (localhost:8080/home) .
### News Section
1. Membuat database bernama news. Lalu ketikkan perintah ini untuk membuat tabel bernama news:
```shell
CREATE TABLE news (
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    title VARCHAR(128) NOT NULL,
    slug VARCHAR(128) NOT NULL,
    body TEXT NOT NULL,
    PRIMARY KEY (id),
    UNIQUE slug (slug)
);
```
2. Masukkan data ke dalam tabel tersebut dengan mengetikkan perintah ini :
```shell
INSERT INTO news VALUES
(1,'Elvis sighted','elvis-sighted','Elvis was sighted at the Podunk internet cafe. It looked like he was writing a CodeIgniter app.'),
(2,'Say it isn\'t so!','say-it-isnt-so','Scientists conclude that some programmers have a sense of humor.'),
(3,'Caffeination, Yes!','caffeination-yes','World\'s largest coffee shop open onsite nested coffee shop for staff only.');
```
3. Mengubungkan ke basis data di pc
Cek di dalam file bawaan codeigniter yang bernama .env
Apakah baris kode ini ada di dalam file .env mu:
```shell
atabase.default.hostname = localhost
database.default.database = ci4tutorial
database.default.username = root
database.default.password = root
database.default.DBDriver = MySQLi
```
4. Membuat model news
Buka direktori app/Models dan buat file baru bernama NewsModel.php dan tambahkan kode berikut.
```shell
<?php

namespace App\Models;

use CodeIgniter\Model;

class NewsModel extends Model
{
    protected $table = 'news';
}
```
Tambahkan Metode NewsModel::getNews()
```shell
public function getNews($slug = false)
    {
        if ($slug === false) {
            return $this->findAll();
        }

        return $this->where(['slug' => $slug])->first();
    }
```
5. Menampilkan news
Ubah file app/Config/Routes.php Anda , sehingga terlihat seperti berikut:
```shell
<?php

// ...

use App\Controllers\News; // Add this line
use App\Controllers\Pages;

$routes->get('news', [News::class, 'index']);           // Add this line
$routes->get('news/(:segment)', [News::class, 'show']); // Add this line

$routes->get('pages', [Pages::class, 'index']);
$routes->get('(:segment)', [Pages::class, 'view']);
```
6. Buat pengontrol baru di app/Controllers/News.php .
```shell
<?php

namespace App\Controllers;

use App\Models\NewsModel;

class News extends BaseController
{
    public function index()
    {
        $model = model(NewsModel::class);

        $data['news'] = $model->getNews();
    }

    public function show($slug = null)
    {
        $model = model(NewsModel::class);

        $data['news'] = $model->getNews($slug);
    }
}
```
membuat news lengkap
```shell
<?php

namespace App\Controllers;

use App\Models\NewsModel;

class News extends BaseController
{
    public function index()
    {
        $model = model(NewsModel::class);

        $data = [
            'news'  => $model->getNews(),
            'title' => 'News archive',
        ];

        return view('templates/header', $data)
            . view('news/index')
            . view('templates/footer');
    }

    // ...
}
```
6. Buat app/Views/news/index.php dan tambahkan potongan kode berikutnya.
```shell
<h2><?= esc($title) ?></h2>

<?php if (! empty($news) && is_array($news)): ?>

    <?php foreach ($news as $news_item): ?>

        <h3><?= esc($news_item['title']) ?></h3>

        <div class="main">
            <?= esc($news_item['body']) ?>
        </div>
        <p><a href="/news/<?= esc($news_item['slug'], 'url') ?>">View article</a></p>

    <?php endforeach ?>

<?php else: ?>

    <h3>No News</h3>

    <p>Unable to find any news for you.</p>

<?php endif ?>
```
Membuat news lengkap
```shell
<?php

namespace App\Controllers;

use App\Models\NewsModel;
use CodeIgniter\Exceptions\PageNotFoundException;

class News extends BaseController
{
    // ...

    public function show($slug = null)
    {
        $model = model(NewsModel::class);

        $data['news'] = $model->getNews($slug);

        if (empty($data['news'])) {
            throw new PageNotFoundException('Cannot find the news item: ' . $slug);
        }

        $data['title'] = $data['news']['title'];

        return view('templates/header', $data)
            . view('news/view')
            . view('templates/footer');
    }
}
```
7. Satu-satunya hal yang perlu dilakukan adalah membuat tampilan terkait di app/Views/news/view.php . Letakkan kode berikut di file ini.
```shell
<h2><?= esc($news['title']) ?></h2>
<p><?= esc($news['body']) ?></p>
```
8. Arahkan browser Anda ke halaman “berita”, yaitu (localhost:8080/news) , Anda akan melihat daftar item berita, yang masing-masing memiliki link untuk menampilkan satu artikel saja.
## CI4 Overview
### Models, View, Controller
MVC adalah Merupakan pola arsitektur perangkat lunak yang umum digunakan dalam merancang antarmuka pengguna dan mengorganisir kode dalam aplikasi.
1. Views - biasanya berbentuk HTML dengan jumlah PHP yang sangat kecil. Tampilan umumnya disimpan di app/Views
2. Models - memelihara satu tipe data untuk aplikasi. Ini mungkin pengguna, postingan blog, transaksi, dll. Model biasanya disimpan di app/Models.
3. Controller -  tempat Anda memastikan bahwa orang diizinkan berada di sana, dan mereka mendapatkan data mereka butuhkan dalam format yang dapat mereka gunakan. Pengontrol biasanya disimpan di app/Controllers

## General topics
### Helper Functions
Helper adalah istilah yang sering digunakan untuk merujuk kepada fungsi, program, atau alat yang membantu dalam menyelesaikan tugas atau masalah tertentu.Jadi, helper bisa merujuk kepada berbagai hal, mulai dari fungsi atau modul dalam pengembangan perangkat lunak hingga orang atau sumber daya yang memberikan bantuan dalam menyelesaikan tugas atau masalah tertentu.
1. Mengunduh helper
Memuat file pembantu cukup sederhana menggunakan metode berikut:
```shell
<?php

helper('name');
```
Misalnya, untuk memuat file Cookie Helper , yang diberi nama cookie_helper.php , Anda akan melakukan ini:
```shell
<?php

helper('cookie');
```
2. Cara agar helper banyak termuat
```shell
<?php

helper(['cookie', 'date']);
```
3. Cara untuk memuat di namespace tertentu
Untuk contoh ini, asumsikan kita telah mengelompokkan semua kode yang berhubungan dengan Blog ke dalam namespace-nya sendiri, Example\Blog. File-file tersebut ada di server kami di Modules/Blog/ . Jadi, kami akan meletakkan file Helper kami untuk modul blog di Modules/Blog/Helpers/ . File blog_helper akan berada di Modules/Blog/Helpers/blog_helper.php . Di dalam pengontrol kita, kita dapat menggunakan perintah berikut untuk memuat helper untuk kita:
```shell
<?php

helper('Example\Blog\blog');
```
Adapun cara lain:
```shell
<?php

helper('Example\Blog\Helpers\blog');
```
4. Adapun helper yang termuat otomatis
Jika Anda memerlukan helper tertentu secara global di seluruh aplikasi Anda, Anda dapat memberitahu CodeIgniter untuk memuatnya secara otomatis selama inisialisasi sistem. Hal ini dilakukan dengan membuka file app/Config/Autoload.php dan menambahkan helper ke $helpersproperti.
5. Cara memakai helper
Misalnya, untuk membuat tautan menggunakan anchor()fungsi di salah satu file tampilan, Anda akan melakukan ini:
```shell
<div>
<?= anchor('blog/comments', 'Click Here') ?>
</div>
```
6. Membuat helper khusus
Misalnya, untuk membuat info helper, Anda akan membuat file bernama app/Helpers/info_helper.php , dan menambahkan fungsi ke file:
```shell
<?php

// app/Helpers/info_helper.php
use CodeIgniter\CodeIgniter;

/**
 * Returns CodeIgniter's version.
 */
function ci_version(): string
{
    return CodeIgniter::CI_VERSION;
}
```
7. Memperluas helper
Misalnya, untuk memperluas Array Helper asli Anda akan membuat file bernama app/Helpers/array_helper.php , dan menambahkan atau mengganti fungsi:
```shell
<?php

// any_in_array() is not in the Array Helper, so it defines a new function
function any_in_array($needle, $haystack)
{
    $needle = is_array($needle) ? $needle : [$needle];

    foreach ($needle as $item) {
        if (in_array($item, $haystack, true)) {
            return true;
        }
    }

    return false;
}

// random_element() is included in Array Helper, so it overrides the native function
function random_element($array)
{
    shuffle($array);

    return array_pop($array);
}
```
## Controller and Routing
### Controller
Controller adalah bagian dari pola desain arsitektur perangkat lunak yang disebut Model-View-Controller (MVC). Controller bertanggung jawab untuk menerima input dari pengguna, memprosesnya, dan mengirimkan tanggapan kembali kepada pengguna atau memperbarui model atau tampilan yang sesuai.
1. Contructor
Controller CodeIgniter memiliki konstruktor khusus initController(). Ini akan dipanggil oleh framework setelah __construct()eksekusi konstruktor PHP.
Jika Anda ingin mengganti initController(), jangan lupa menambahkan metode:parent::initController($request, $response, $logger);
```shell
<?php

namespace App\Controllers;

use CodeIgniter\HTTP\RequestInterface;
use CodeIgniter\HTTP\ResponseInterface;
use Psr\Log\LoggerInterface;

class Product extends BaseController
{
    public function initController(
        RequestInterface $request,
        ResponseInterface $response,
        LoggerInterface $logger
    ) {
        parent::initController($request, $response, $logger);

        // Add your code here.
    }

    // ...
}
```
2. Helper
Anda dapat mendefinisikan array file pembantu sebagai properti kelas. Setiap kali pengontrol dimuat, file pembantu ini akan secara otomatis dimuat ke dalam memori sehingga Anda dapat menggunakan metodenya di mana saja di dalam pengontrol:
```shell
<?php

namespace App\Controllers;

class MyController extends BaseController
{
    protected $helpers = ['url', 'form'];
}
```
3. Force https
```shell
<?php

if (! $this->request->isSecure()) {
    $this->forceHTTPS();
}
```
4. Metode perlindungan
Misalnya, jika Anda mendefinisikan metode seperti ini untuk Helloworldpengontrol:
```shell
<?php

namespace App\Controllers;

class Helloworld extends BaseController
{
    protected function utility()
    {
        // some code
    }
}
```
5. Kita coba buat HelloWorld
BaseController menyediakan tempat yang nyaman untuk memuat komponen dan menjalankan fungsi yang diperlukan oleh semua pengontrol Anda. Anda dapat memperluas kelas ini di pengontrol baru mana pun.
```shell
<?php

namespace App\Controllers;

class Helloworld extends BaseController
{
    public function getIndex()
    {
        return 'Hello World!';
    }
}
```
Kemudian simpan file ke direktori aplikasi/Pengontrol Anda .
6. Metode
Membuat metode biasa
```shell
<?php

namespace App\Controllers;

class Helloworld extends BaseController
{
    public function getIndex()
    {
        return 'Hello World!';
    }

    public function getComment()
    {
        return 'I am not flat!';
    }
}
```
7. Mlewati segmen uri ke metode kita
isalnya, Anda memiliki URI seperti ini:
```shell
example.com/index.php/products/shoes/sandals/123
```
```shell
<?php

namespace App\Controllers;

class Products extends BaseController
{
    public function getShoes($sandals, $id)
    {
        return $sandals . $id;
    }
}
```
8. Mendefiniskan controller default
Untuk menentukan pengontrol default, buka file app/Config/Routing.php Anda dan atur properti ini:
```shell
public string $defaultController = 'Helloworld';
```
Dimana Helloworldnama kelas pengontrol yang ingin Anda gunakan.

Dan beri komentar pada baris di app/Config/Routes.php :
```shell
$routes->get('/', 'Home::index');
```
Jika sekarang Anda menjelajahi situs Anda tanpa menentukan segmen URI apa pun, Anda akan melihat pesan “Hello World”.
9. Metode Warisan
Cara lain untuk menampilkan pesan “Hello World” adalah sebagai berikut:
```shell
example.com/index.php/helloworld/index/
```
10. Segmen kedua dari URI menentukan metode mana di pengontrol yang dipanggil.
```shell
<?php

namespace App\Controllers;

class Helloworld extends BaseController
{
    public function index()
    {
        return 'Hello World!';
    }

    public function comment()
    {
        return 'I am not flat!';
    }
}
```
## Building Response
1. Membuat tampilan
Dengan menggunakan editor teks , buat file bernama blog_view.php dan letakkan ini di dalamnya:
```shell
<html>
    <head>
        <title>My Blog</title>
    </head>
    <body>
        <h1>Welcome to my Blog!</h1>
    </body>
</html>
```
Kemudian simpan file di direktori app/Views Anda 
2.  Menampilkan tampilan
```shell
return view('name');
```
Sekarang, buat file bernama Blog.php di direktori app/Controllers , dan letakkan ini di dalamnya:

```shell
<?php

namespace App\Controllers;

class Blog extends BaseController
{
    public function index()
    {
        return view('blog_view');
    }
}
```
Buka file perutean yang terletak di app/Config/Routes.php , dan cari “Definisi Rute”. Tambahkan kode berikut:
```shell
use App\Controllers\Blog;

$routes->get('blog', [Blog::class, 'index']);
```
3. Membuat banyak tampilan
```shell
<?php

namespace App\Controllers;

use CodeIgniter\Controller;

class Page extends Controller
{
    public function index()
    {
        $data = [
            'page_title' => 'Your title',
        ];

        return view('header')
            . view('menu')
            . view('content', $data)
            . view('footer');
    }
}
```
4. Membuat tampilan caching
Kita dapat menyimpan tampilan dalam cache dengan view()fungsi tersebut dengan meneruskan cacheopsi dengan jumlah detik untuk menyimpan tampilan dalam cache, pada parameter ketiga:
```shell
// Cache the view for 60 seconds
return view('file_name', $data, ['cache' => 60]);
```
Secara default, tampilan akan di-cache menggunakan nama yang sama dengan file tampilan itu sendiri. Anda dapat menyesuaikannya dengan meneruskan cache_nameID cache yang ingin Anda gunakan:
```shell
// Cache the view for 60 seconds
return view('file_name', $data, ['cache' => 60, 'cache_name' => 'my_cached_view']);

```
5. Opsi simpan data
```shell
$data = [
    'title'   => 'My title',
    'heading' => 'My Heading',
    'message' => 'My Message',
];

return view('blog_view', $data, ['saveData' => false]);
```
Selain itu, jika Anda ingin fungsionalitas default dari view()fungsi tersebut adalah menghapus data di antara panggilan, Anda dapat mengaturnya $saveDatadi falseapp /Config/Views.php .












