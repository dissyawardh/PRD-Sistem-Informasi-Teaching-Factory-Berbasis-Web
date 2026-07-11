**PRODUCT REQUIREMENTS DOCUMENT (PRD)**

**Sistem Informasi Teaching Factory Jurusan Komputer dan Bisnis Berbasis Website Menggunakan Framework Laravel**

*Disusun berdasarkan Proposal Tugas Akhir*

Dissya Putri Wardhany — 240102040

Program Studi Teknik Informatika — Politeknik Negeri Cilacap

# Informasi Dokumen

| **Atribut**             | **Keterangan**                                                                                                             |
|-------------------------|----------------------------------------------------------------------------------------------------------------------------|
| Nama Produk             | Sistem Informasi Teaching Factory (TeFa) JKB                                                                               |
| Versi Dokumen           | 1.0                                                                                                                        |
| Status                  | Draft untuk Tugas Akhir                                                                                                    |
| Framework               | Laravel (PHP), MySQL, Bootstrap/Blade                                                                                      |
| Metodologi Pengembangan | Waterfall                                                                                                                  |
| Referensi               | Proposal Tugas Akhir – Rancang Bangun Sistem Informasi Teaching Factory JKB Berbasis Website Menggunakan Framework Laravel |
| Target Pengguna         | Mahasiswa, Koordinator Divisi, dan Admin Teaching Factory Jurusan Komputer dan Bisnis                                      |

# Daftar Isi

# 1. Pendahuluan

## 1.1 Latar Belakang

Teaching Factory (TeFa) Jurusan Komputer dan Bisnis (JKB) merupakan wadah bagi mahasiswa untuk mengembangkan keterampilan melalui kegiatan berorientasi dunia kerja, yang terdiri dari tiga divisi: TeFa Desain Grafis, TeFa Multimedia, dan TeFa Web. Saat ini informasi profil organisasi, struktur kepengurusan, dokumentasi proyek, dan agenda kegiatan masih tersebar di berbagai media dan belum terdokumentasi secara terpusat, sehingga menyulitkan mahasiswa memperoleh informasi lengkap serta menyulitkan pengurus dalam pengelolaan data dan publikasi hasil kerja.

Produk ini dikembangkan untuk menjawab kebutuhan tersebut: sebuah sistem informasi berbasis website yang berfungsi sebagai media pengenalan organisasi, dokumentasi proyek dan kegiatan, serta pengelolaan agenda/timeline kegiatan secara terstruktur dan terpusat.

## 1.2 Tujuan Produk

- Menyediakan media informasi terpusat mengenai profil, struktur, dan divisi Teaching Factory JKB bagi mahasiswa.

- Menyediakan sarana dokumentasi proyek dan kegiatan yang dapat diakses sebagai portofolio organisasi.

- Menyediakan fitur pengelolaan timeline kegiatan dan pengumuman agar informasi tersampaikan secara efektif ke seluruh anggota.

- Menyediakan pengelolaan data organisasi (divisi, anggota, akun pengguna) dengan hak akses yang sesuai peran masing-masing pengguna.

## 1.3 Ruang Lingkup Produk

### 1.3.1 Termasuk dalam Ruang Lingkup (In-Scope)

- Landing page publik berisi profil, visi-misi, struktur organisasi, divisi, dan arsip proyek.

- Autentikasi berbasis role: Administrator, Koordinator Divisi, dan Anggota Divisi.

- Modul CRUD untuk data proyek, kegiatan, pengumuman, divisi, dan anggota.

- Modul timeline kegiatan yang dapat dilihat oleh seluruh anggota sesuai hak akses.

- Dashboard ringkasan data (jumlah proyek, kegiatan, pengumuman) sesuai peran pengguna.

### 1.3.2 Tidak Termasuk dalam Ruang Lingkup (Out-of-Scope)

- Manajemen tugas atau monitoring progres pengerjaan proyek secara detail (hanya dokumentasi hasil akhir).

- Modul keuangan/anggaran organisasi.

- Fitur komunikasi langsung seperti chat atau forum diskusi.

- Integrasi dengan sistem akademik kampus atau sistem eksternal lainnya.

# 2. Pengguna dan Peran (User Roles)

Sistem memiliki tiga jenis peran pengguna dengan hak akses berbeda berdasarkan konsep Role-Based Access Control (RBAC), sebagaimana dirangkum pada tabel berikut.

| **Modul / Hak Akses**                   | **Administrator** | **Koordinator Divisi**    | **Anggota Divisi** |
|-----------------------------------------|-------------------|---------------------------|--------------------|
| Melihat Landing Page & informasi publik | ✓                 | ✓                         | ✓                  |
| Login ke dashboard                      | ✓                 | ✓                         | ✓                  |
| Kelola akun pengguna & hak akses        | ✓                 | ✗                         | ✗                  |
| Kelola struktur organisasi & divisi     | ✓                 | ✗                         | ✗                  |
| Kelola data anggota (seluruh divisi)    | ✓                 | ✗ (hanya lihat divisinya) | ✗                  |
| Kelola data proyek (tambah/ubah/hapus)  | ✓ (semua)         | ✓ (divisinya)             | ✗ (hanya lihat)    |
| Kelola data kegiatan/timeline           | ✓ (semua)         | ✓ (divisinya)             | ✗ (hanya lihat)    |
| Kelola pengumuman                       | ✓ (semua)         | ✓ (divisinya)             | ✗ (hanya lihat)    |

# 3. Kebutuhan Fungsional (Functional Requirements)

Kebutuhan fungsional disusun dalam format user story beserta kriteria penerimaan (acceptance criteria) untuk setiap modul sistem.

## 3.1 Modul Landing Page

**User Story:** Sebagai pengunjung (tanpa login), saya ingin melihat profil, visi-misi, struktur organisasi, dan divisi Teaching Factory agar saya mengenal organisasi tersebut.

- Halaman dapat diakses tanpa autentikasi.

- Menampilkan profil, visi-misi, struktur organisasi, dan daftar divisi (Desain Grafis, Multimedia, Web).

- Menampilkan daftar proyek yang telah dipublikasikan sebagai portofolio.

## 3.2 Modul Autentikasi & RBAC

**User Story:** Sebagai pengguna terdaftar, saya ingin login menggunakan email dan password agar dapat mengakses dashboard sesuai peran saya.

- Login memvalidasi kombinasi email dan password terhadap data pada basis data.

- Password disimpan dalam bentuk hash (bcrypt) menggunakan fitur bawaan Laravel.

- Setelah login berhasil, pengguna diarahkan ke dashboard sesuai role: Administrator, Koordinator Divisi, atau Anggota Divisi.

- Pengguna yang belum login tidak dapat mengakses halaman dashboard maupun halaman kelola data (redirect ke halaman login).

- Tersedia fitur logout yang mengakhiri sesi pengguna.

## 3.3 Modul Dashboard

**User Story:** Sebagai pengguna yang telah login, saya ingin melihat ringkasan data (jumlah proyek, kegiatan, pengumuman) agar saya cepat memahami kondisi organisasi terkini.

- Dashboard menampilkan jumlah total proyek, kegiatan, dan pengumuman sesuai hak akses role.

- Tampilan dashboard berbeda antara Administrator (data seluruh organisasi) dan Koordinator/Anggota Divisi (data divisinya).

## 3.4 Modul Manajemen Organisasi (Divisi & Anggota)

**User Story:** Sebagai Administrator, saya ingin mengelola data divisi, anggota, dan struktur organisasi agar informasi organisasi selalu akurat dan terbaru.

- Administrator dapat menambah, mengubah, dan menghapus data divisi.

- Administrator dapat menambah, mengubah, dan menghapus data anggota beserta divisinya.

- Data yang disimpan otomatis tampil pada Landing Page.

- Koordinator Divisi hanya dapat melihat data anggota pada divisinya sendiri.

## 3.5 Modul Manajemen Proyek

**User Story:** Sebagai Koordinator Divisi, saya ingin menambahkan dokumentasi proyek yang telah diselesaikan oleh divisi saya agar dapat menjadi arsip portofolio organisasi.

- Form input proyek terdiri dari judul, deskripsi, divisi pelaksana, instansi mitra, tanggal pelaksanaan, dan file/gambar dokumentasi.

- Koordinator Divisi hanya dapat mengelola (ubah/hapus) proyek milik divisinya sendiri.

- Administrator dapat melihat, mengubah, dan menghapus seluruh data proyek dari semua divisi.

- Proyek yang berstatus 'dipublikasikan' tampil otomatis pada Landing Page dan halaman arsip proyek.

- Anggota Divisi hanya dapat melihat daftar dan detail proyek tanpa hak ubah/hapus.

## 3.6 Modul Manajemen Kegiatan (Timeline)

**User Story:** Sebagai Koordinator Divisi, saya ingin menambahkan agenda kegiatan divisi saya agar seluruh anggota mengetahui jadwal kegiatan yang akan datang.

- Form input kegiatan terdiri dari nama kegiatan, deskripsi, tanggal/waktu pelaksanaan, dan divisi penyelenggara.

- Kegiatan ditampilkan dalam bentuk timeline terurut berdasarkan tanggal.

- Anggota Divisi hanya dapat melihat kegiatan yang sudah dipublikasikan, tanpa hak ubah/hapus.

## 3.7 Modul Pengumuman

**User Story:** Sebagai Koordinator Divisi, saya ingin membuat pengumuman terkait divisi saya agar informasi penting tersampaikan ke seluruh anggota.

- Form input pengumuman terdiri dari judul, isi pengumuman, dan tanggal publikasi.

- Pengumuman ditampilkan terurut dari yang terbaru.

- Administrator dapat memantau seluruh pengumuman dari semua divisi.

## 3.8 Modul Manajemen Akun Pengguna

**User Story:** Sebagai Administrator, saya ingin membuat dan mengatur akun pengguna beserta peran (role)-nya agar hak akses setiap pengguna sesuai dengan tanggung jawabnya.

- Administrator dapat menambah, mengubah, menonaktifkan, dan menghapus akun pengguna.

- Setiap akun wajib memiliki salah satu role: Administrator, Koordinator Divisi, atau Anggota Divisi.

- Perubahan role langsung memengaruhi hak akses pengguna pada sesi berikutnya.

# 4. Kebutuhan Non-Fungsional

| **Kategori**    | **Deskripsi Kebutuhan**                                                                                                                          |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| Keamanan        | Password pengguna dienkripsi (bcrypt); autentikasi dan otorisasi menggunakan session & middleware role Laravel; proteksi CSRF pada seluruh form. |
| Usability       | Antarmuka sederhana, informatif, dan responsif; menggunakan skema warna navy, emas (gold), dan putih dengan font Poppins.                        |
| Performa        | Waktu muat halaman utama disarankan di bawah 3 detik pada koneksi standar kampus.                                                                |
| Kompatibilitas  | Dapat diakses melalui browser umum (Chrome, Firefox, Edge) pada perangkat desktop maupun mobile (responsive design).                             |
| Portabilitas    | Berjalan pada web server berbasis PHP (Apache/Nginx) dengan basis data MySQL, dapat dijalankan secara lokal (XAMPP) maupun hosting.              |
| Maintainability | Kode mengikuti struktur MVC bawaan Laravel agar mudah dipelihara dan dikembangkan oleh mahasiswa/pemula.                                         |

# 5. Arsitektur Sistem & Teknologi

Sistem dibangun dengan arsitektur berbasis web menggunakan pola Model-View-Controller (MVC) bawaan Laravel, yang memisahkan logika data (Model), tampilan (View/Blade), dan logika pengendali (Controller).

## 5.1 Alur Kerja Umum

1.  Pengguna mengakses website melalui browser (Landing Page dapat diakses tanpa login).

2.  Pengguna dengan akun (anggota TeFa) login menggunakan email dan password.

3.  Middleware autentikasi & role memeriksa hak akses, lalu mengarahkan ke dashboard sesuai peran.

4.  Controller menerima permintaan pengguna, memanggil Model untuk mengambil/menyimpan data ke MySQL, lalu meneruskan data ke View (Blade) untuk ditampilkan.

5.  Data yang bersifat publik (proyek terpublikasi, profil organisasi) otomatis tersinkronisasi ke Landing Page.

## 5.2 Teknologi yang Digunakan

| **Komponen**       | **Teknologi**                                       |
|--------------------|-----------------------------------------------------|
| Bahasa Pemrograman | PHP                                                 |
| Framework Backend  | Laravel (versi 10/11 LTS)                           |
| Basis Data         | MySQL                                               |
| Templating / View  | Blade (Laravel)                                     |
| Front-end Styling  | Bootstrap 5 / Tailwind CSS (opsional), font Poppins |
| Web Server Lokal   | XAMPP / Laragon                                     |
| Version Control    | Git & GitHub                                        |
| Tools Desain UI    | Figma                                               |
| Testing            | Black Box Testing (manual)                          |

# 6. Desain Basis Data

Struktur basis data dirancang sederhana agar mudah diimplementasikan oleh pemula, dengan tabel-tabel inti berikut.

### users

Menyimpan akun pengguna beserta perannya.

| **Kolom**               | **Tipe Data** | **Keterangan**                                   |
|-------------------------|---------------|--------------------------------------------------|
| id                      | bigint (PK)   | ID unik pengguna                                 |
| name                    | varchar(100)  | Nama lengkap                                     |
| email                   | varchar(100)  | Email, unik, digunakan untuk login               |
| password                | varchar(255)  | Password terenkripsi (hash)                      |
| role                    | enum          | 'admin', 'koordinator', 'anggota'                |
| division_id             | bigint (FK)   | Relasi ke tabel divisions (nullable untuk admin) |
| created_at / updated_at | timestamp     | Waktu pembuatan/pembaruan data                   |

### divisions

Menyimpan data divisi Teaching Factory.

| **Kolom**   | **Tipe Data** | **Keterangan**                               |
|-------------|---------------|----------------------------------------------|
| id          | bigint (PK)   | ID unik divisi                               |
| name        | varchar(100)  | Nama divisi (Desain Grafis, Multimedia, Web) |
| description | text          | Deskripsi singkat divisi                     |

### members

Menyimpan data anggota aktif Teaching Factory.

| **Kolom**   | **Tipe Data** | **Keterangan**                 |
|-------------|---------------|--------------------------------|
| id          | bigint (PK)   | ID unik anggota                |
| name        | varchar(100)  | Nama anggota                   |
| division_id | bigint (FK)   | Relasi ke tabel divisions      |
| position    | varchar(100)  | Jabatan/peran dalam organisasi |
| photo       | varchar(255)  | Path foto anggota (opsional)   |

### projects

Menyimpan dokumentasi proyek yang telah dikerjakan.

| **Kolom**           | **Tipe Data** | **Keterangan**                 |
|---------------------|---------------|--------------------------------|
| id                  | bigint (PK)   | ID unik proyek                 |
| title               | varchar(150)  | Judul proyek                   |
| description         | text          | Deskripsi proyek               |
| division_id         | bigint (FK)   | Divisi pelaksana               |
| partner_institution | varchar(150)  | Instansi mitra                 |
| project_date        | date          | Tanggal pelaksanaan            |
| image               | varchar(255)  | Path dokumentasi/gambar proyek |
| status              | enum          | 'draft', 'published'           |

### activities

Menyimpan agenda/timeline kegiatan organisasi.

| **Kolom**   | **Tipe Data** | **Keterangan**              |
|-------------|---------------|-----------------------------|
| id          | bigint (PK)   | ID unik kegiatan            |
| title       | varchar(150)  | Nama kegiatan               |
| description | text          | Deskripsi kegiatan          |
| division_id | bigint (FK)   | Divisi penyelenggara        |
| event_date  | datetime      | Tanggal & waktu pelaksanaan |
| status      | enum          | 'draft', 'published'        |

### announcements

Menyimpan pengumuman organisasi.

| **Kolom**    | **Tipe Data** | **Keterangan**                                          |
|--------------|---------------|---------------------------------------------------------|
| id           | bigint (PK)   | ID unik pengumuman                                      |
| title        | varchar(150)  | Judul pengumuman                                        |
| content      | text          | Isi pengumuman                                          |
| division_id  | bigint (FK)   | Divisi terkait (nullable jika untuk seluruh organisasi) |
| published_at | datetime      | Tanggal publikasi                                       |

Relasi antar tabel: satu divisi (divisions) memiliki banyak anggota (members), proyek (projects), kegiatan (activities), dan pengumuman (announcements) — relasi one-to-many. Tabel users terhubung ke divisions untuk menentukan cakupan data yang dapat dikelola oleh Koordinator Divisi.

# 7. Desain Antarmuka (UI/UX)

## 7.1 Prinsip Desain

- Sederhana dan informatif: navigasi utama dikelompokkan jelas antara halaman publik dan dashboard.

- Responsif: tampilan menyesuaikan perangkat desktop maupun mobile.

- Skema warna: Navy (#1B2A4A) sebagai warna utama, Emas/Gold (#C9A227) sebagai aksen, dan Putih (#FFFFFF) sebagai latar.

- Tipografi: menggunakan font Poppins untuk kesan modern dan mudah dibaca.

## 7.2 Halaman Utama yang Dibutuhkan

| **Halaman**          | **Diakses oleh**           | **Fungsi Utama**                                               |
|----------------------|----------------------------|----------------------------------------------------------------|
| Landing Page         | Publik                     | Profil, visi-misi, struktur organisasi, arsip proyek publikasi |
| Login                | Publik                     | Autentikasi pengguna terdaftar                                 |
| Dashboard            | Semua role (setelah login) | Ringkasan data sesuai hak akses                                |
| Kelola Proyek        | Admin, Koordinator Divisi  | CRUD data proyek                                               |
| Kelola Kegiatan      | Admin, Koordinator Divisi  | CRUD data kegiatan/timeline                                    |
| Kelola Pengumuman    | Admin, Koordinator Divisi  | CRUD data pengumuman                                           |
| Kelola Organisasi    | Admin                      | CRUD divisi, anggota, struktur organisasi                      |
| Kelola Akun Pengguna | Admin                      | CRUD akun & role pengguna                                      |

# 8. Alur Pengguna (User Flow) Ringkas

1.  Pengunjung membuka website → Landing Page tampil tanpa perlu login.

2.  Pengunjung ingin login → klik menu Login → memasukkan email & password.

3.  Sistem memvalidasi kredensial → jika berhasil, arahkan ke Dashboard sesuai role.

4.  Admin/Koordinator memilih menu Kelola Proyek/Kegiatan/Pengumuman → melakukan tambah/ubah/hapus data.

5.  Data yang berstatus 'published' otomatis tampil kembali di Landing Page dan halaman publik.

# 9. Implementasi Kode Dasar (Contoh Kode untuk Pemula)

Bagian ini menyediakan contoh kode dasar Laravel yang dapat langsung diadaptasi oleh pemula, dengan tetap mengikuti konsep MVC, RBAC, dan CRUD sesuai rancangan sistem. Contoh berikut menggunakan studi kasus modul Proyek (Projects), yang polanya dapat diterapkan sama untuk modul Kegiatan dan Pengumuman.

## 9.1 Instalasi Proyek Laravel

> composer create-project laravel/laravel tefa-jkb  
> cd tefa-jkb  
> php artisan key:generate

*Perintah dasar membuat proyek Laravel baru bernama tefa-jkb.*

Atur koneksi basis data pada file .env:

> DB_CONNECTION=mysql  
> DB_HOST=127.0.0.1  
> DB_PORT=3306  
> DB_DATABASE=tefa_jkb  
> DB_USERNAME=root  
> DB_PASSWORD=

## 9.2 Migration (Struktur Tabel)

Buat migration menggunakan perintah artisan, lalu definisikan kolom tabel:

> php artisan make:migration create_divisions_table  
> php artisan make:migration create_projects_table
>
> // database/migrations/xxxx_create_divisions_table.php  
> public function up()  
> {  
> Schema::create('divisions', function (Blueprint \$table) {  
> \$table-\>id();  
> \$table-\>string('name', 100);  
> \$table-\>text('description')-\>nullable();  
> \$table-\>timestamps();  
> });  
> }
>
> // database/migrations/xxxx_create_projects_table.php  
> public function up()  
> {  
> Schema::create('projects', function (Blueprint \$table) {  
> \$table-\>id();  
> \$table-\>string('title', 150);  
> \$table-\>text('description')-\>nullable();  
> \$table-\>foreignId('division_id')-\>constrained()-\>onDelete('cascade');  
> \$table-\>string('partner_institution', 150)-\>nullable();  
> \$table-\>date('project_date')-\>nullable();  
> \$table-\>string('image')-\>nullable();  
> \$table-\>enum('status', \['draft', 'published'\])-\>default('draft');  
> \$table-\>timestamps();  
> });  
> }

*Jalankan php artisan migrate untuk membuat tabel pada basis data.*

## 9.3 Model (Relasi Data)

> // app/Models/Project.php  
> namespace App\Models;  
>   
> use Illuminate\Database\Eloquent\Model;  
>   
> class Project extends Model  
> {  
> protected \$fillable = \[  
> 'title', 'description', 'division_id',  
> 'partner_institution', 'project_date', 'image', 'status',  
> \];  
>   
> public function division()  
> {  
> return \$this-\>belongsTo(Division::class);  
> }  
> }
>
> // app/Models/Division.php  
> namespace App\Models;  
>   
> use Illuminate\Database\Eloquent\Model;  
>   
> class Division extends Model  
> {  
> protected \$fillable = \['name', 'description'\];  
>   
> public function projects()  
> {  
> return \$this-\>hasMany(Project::class);  
> }  
> }

## 9.4 Middleware Role (RBAC Sederhana)

Middleware digunakan untuk membatasi akses halaman berdasarkan role pengguna yang login.

> php artisan make:middleware CheckRole
>
> // app/Http/Middleware/CheckRole.php  
> namespace App\Http\Middleware;  
>   
> use Closure;  
> use Illuminate\Http\Request;  
>   
> class CheckRole  
> {  
> public function handle(Request \$request, Closure \$next, ...\$roles)  
> {  
> if (!auth()-\>check() \|\| !in_array(auth()-\>user()-\>role, \$roles)) {  
> abort(403, 'Anda tidak memiliki akses ke halaman ini.');  
> }  
>   
> return \$next(\$request);  
> }  
> }

Daftarkan middleware pada berkas bootstrap/app.php (Laravel 11) atau app/Http/Kernel.php (Laravel 10):

> // bootstrap/app.php (Laravel 11)  
> -\>withMiddleware(function (Middleware \$middleware) {  
> \$middleware-\>alias(\[  
> 'role' =\> \App\Http\Middleware\CheckRole::class,  
> \]);  
> })

## 9.5 Routing dengan Proteksi Role

> // routes/web.php  
> use App\Http\Controllers\ProjectController;  
>   
> Route::get('/', \[ProjectController::class, 'landing'\])-\>name('landing');  
>   
> Route::middleware(\['auth'\])-\>group(function () {  
> Route::get('/dashboard', function () {  
> return view('dashboard');  
> })-\>name('dashboard');  
>   
> Route::middleware(\['role:admin,koordinator'\])-\>group(function () {  
> Route::resource('projects', ProjectController::class)  
> -\>except(\['show'\]);  
> });  
> });

*Route::resource otomatis membuat seluruh route CRUD (index, create, store, edit, update, destroy).*

## 9.6 Controller (Logika CRUD)

> // app/Http/Controllers/ProjectController.php  
> namespace App\Http\Controllers;  
>   
> use App\Models\Project;  
> use App\Models\Division;  
> use Illuminate\Http\Request;  
>   
> class ProjectController extends Controller  
> {  
> // Landing page: tampilkan proyek yang sudah published  
> public function landing()  
> {  
> \$projects = Project::where('status', 'published')  
> -\>latest()  
> -\>get();  
>   
> return view('landing', compact('projects'));  
> }  
>   
> // Daftar proyek pada dashboard (sesuai hak akses role)  
> public function index(Request \$request)  
> {  
> \$user = auth()-\>user();  
>   
> \$query = Project::with('division');  
>   
> // Koordinator hanya melihat proyek pada divisinya sendiri  
> if (\$user-\>role === 'koordinator') {  
> \$query-\>where('division_id', \$user-\>division_id);  
> }  
>   
> \$projects = \$query-\>latest()-\>paginate(10);  
>   
> return view('projects.index', compact('projects'));  
> }  
>   
> public function create()  
> {  
> \$divisions = Division::all();  
> return view('projects.create', compact('divisions'));  
> }  
>   
> public function store(Request \$request)  
> {  
> \$validated = \$request-\>validate(\[  
> 'title' =\> 'required\|string\|max:150',  
> 'description' =\> 'nullable\|string',  
> 'division_id' =\> 'required\|exists:divisions,id',  
> 'partner_institution' =\> 'nullable\|string\|max:150',  
> 'project_date' =\> 'nullable\|date',  
> 'image' =\> 'nullable\|image\|max:2048',  
> 'status' =\> 'required\|in:draft,published',  
> \]);  
>   
> if (\$request-\>hasFile('image')) {  
> \$validated\['image'\] = \$request-\>file('image')-\>store('projects', 'public');  
> }  
>   
> Project::create(\$validated);  
>   
> return redirect()-\>route('projects.index')  
> -\>with('success', 'Proyek berhasil ditambahkan.');  
> }  
>   
> public function edit(Project \$project)  
> {  
> \$divisions = Division::all();  
> return view('projects.edit', compact('project', 'divisions'));  
> }  
>   
> public function update(Request \$request, Project \$project)  
> {  
> \$validated = \$request-\>validate(\[  
> 'title' =\> 'required\|string\|max:150',  
> 'description' =\> 'nullable\|string',  
> 'division_id' =\> 'required\|exists:divisions,id',  
> 'partner_institution' =\> 'nullable\|string\|max:150',  
> 'project_date' =\> 'nullable\|date',  
> 'status' =\> 'required\|in:draft,published',  
> \]);  
>   
> \$project-\>update(\$validated);  
>   
> return redirect()-\>route('projects.index')  
> -\>with('success', 'Proyek berhasil diperbarui.');  
> }  
>   
> public function destroy(Project \$project)  
> {  
> \$project-\>delete();  
>   
> return redirect()-\>route('projects.index')  
> -\>with('success', 'Proyek berhasil dihapus.');  
> }  
> }

## 9.7 View (Blade Template)

> {{-- resources/views/projects/index.blade.php --}}  
> @extends('layouts.app')  
>   
> @section('content')  
> \<h2\>Kelola Proyek\</h2\>  
>   
> @if (session('success'))  
> \<div class="alert alert-success"\>{{ session('success') }}\</div\>  
> @endif  
>   
> \<a href="{{ route('projects.create') }}" class="btn btn-primary mb-3"\>  
> + Tambah Proyek  
> \</a\>  
>   
> \<table class="table"\>  
> \<thead\>  
> \<tr\>  
> \<th\>Judul\</th\>  
> \<th\>Divisi\</th\>  
> \<th\>Status\</th\>  
> \<th\>Aksi\</th\>  
> \</tr\>  
> \</thead\>  
> \<tbody\>  
> @foreach (\$projects as \$project)  
> \<tr\>  
> \<td\>{{ \$project-\>title }}\</td\>  
> \<td\>{{ \$project-\>division-\>name }}\</td\>  
> \<td\>{{ ucfirst(\$project-\>status) }}\</td\>  
> \<td\>  
> \<a href="{{ route('projects.edit', \$project) }}"\>Ubah\</a\>  
> \<form action="{{ route('projects.destroy', \$project) }}"  
> method="POST" style="display:inline"\>  
> @csrf  
> @method('DELETE')  
> \<button type="submit"  
> onclick="return confirm('Hapus proyek ini?')"\>  
> Hapus  
> \</button\>  
> \</form\>  
> \</td\>  
> \</tr\>  
> @endforeach  
> \</tbody\>  
> \</table\>  
>   
> {{ \$projects-\>links() }}  
> @endsection

*Contoh view sederhana untuk daftar proyek; pemula dapat mengganti tampilan tabel dengan komponen Bootstrap/Tailwind sesuai desain Figma.*

## 9.8 Seeder Akun Awal (Role Testing)

> php artisan make:seeder UserSeeder
>
> // database/seeders/UserSeeder.php  
> namespace Database\Seeders;  
>   
> use App\Models\User;  
> use Illuminate\Database\Seeder;  
> use Illuminate\Support\Facades\Hash;  
>   
> class UserSeeder extends Seeder  
> {  
> public function run()  
> {  
> User::create(\[  
> 'name' =\> 'Admin TeFa',  
> 'email' =\> 'admin@tefa.jkb',  
> 'password' =\> Hash::make('password'),  
> 'role' =\> 'admin',  
> \]);  
>   
> User::create(\[  
> 'name' =\> 'Koordinator Web',  
> 'email' =\> 'koordinator.web@tefa.jkb',  
> 'password' =\> Hash::make('password'),  
> 'role' =\> 'koordinator',  
> 'division_id' =\> 1,  
> \]);  
> }  
> }

*Jalankan dengan php artisan db:seed --class=UserSeeder untuk membuat akun uji coba.*

Struktur kode di atas sengaja dibuat sesederhana mungkin (tanpa Repository Pattern, Service Layer, atau API terpisah) agar mudah dipahami dan langsung diimplementasikan oleh mahasiswa pemula, namun tetap konsisten dengan konsep utama proposal: arsitektur MVC, autentikasi berbasis role (RBAC), fungsi CRUD, dan penyimpanan data pada MySQL.

# 10. Rencana Pengujian (Black Box Testing)

Pengujian dilakukan dengan metode Black Box Testing terhadap seluruh fitur utama, berfokus pada kesesuaian input dan output tanpa memperhatikan struktur kode di dalamnya.

| **No** | **Fitur yang Diuji** | **Skenario Pengujian**                                | **Hasil yang Diharapkan**                                            |
|--------|----------------------|-------------------------------------------------------|----------------------------------------------------------------------|
| 1      | Login                | Login dengan email & password benar                   | Berhasil masuk dan diarahkan ke dashboard sesuai role                |
| 2      | Login                | Login dengan password salah                           | Sistem menampilkan pesan gagal login                                 |
| 3      | Kelola Proyek        | Koordinator menambah proyek baru                      | Data proyek tersimpan dan tampil di daftar proyek divisinya          |
| 4      | Kelola Proyek        | Anggota mencoba mengakses form tambah proyek          | Sistem menolak akses (403 Forbidden)                                 |
| 5      | Kelola Kegiatan      | Koordinator menambah kegiatan baru                    | Kegiatan tersimpan dan tampil pada timeline                          |
| 6      | Kelola Pengumuman    | Koordinator membuat pengumuman                        | Pengumuman tampil terurut dari yang terbaru                          |
| 7      | Kelola Organisasi    | Admin menambah divisi baru                            | Divisi baru tersimpan dan tersedia pada pilihan form proyek/kegiatan |
| 8      | Hak Akses            | Koordinator Divisi A mencoba mengubah proyek Divisi B | Sistem menolak akses / data tidak tampil                             |

# 11. Timeline & Milestone Implementasi

Rencana pengerjaan mengikuti metode Waterfall selama enam bulan, selaras dengan jadwal pada proposal tugas akhir.

| **Bulan** | **Milestone Utama**                                                                   |
|-----------|---------------------------------------------------------------------------------------|
| Bulan 1   | Identifikasi masalah dan pengumpulan data (observasi & wawancara)                     |
| Bulan 2   | Analisis kebutuhan sistem dan mulai perancangan arsitektur, aktor, serta modul sistem |
| Bulan 3   | Perancangan basis data dan antarmuka (UI) selesai                                     |
| Bulan 4   | Implementasi sistem: autentikasi, RBAC, modul organisasi, dan modul proyek            |
| Bulan 5   | Implementasi modul kegiatan & pengumuman, pengujian Black Box, dan evaluasi sistem    |
| Bulan 6   | Perbaikan hasil evaluasi dan penyusunan laporan tugas akhir                           |

# 12. Risiko dan Mitigasi

| **Risiko**                                                             | **Dampak**                                       | **Mitigasi**                                                                                                  |
|------------------------------------------------------------------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
| Kebutuhan pengguna berubah di tengah pengembangan                      | Menghambat timeline Waterfall yang bersifat kaku | Melakukan wawancara mendalam di awal dan menetapkan batasan masalah (scope) secara jelas sejak tahap analisis |
| Data proyek/kegiatan antar divisi tercampur karena kesalahan hak akses | Kebocoran data antar divisi                      | Menerapkan pengecekan division_id pada setiap query Controller dan pengujian hak akses secara menyeluruh      |
| Pengembang (mahasiswa) masih pemula terhadap Laravel                   | Waktu pengembangan lebih lama dari estimasi      | Menggunakan pola kode dasar dan sederhana (lihat Bagian 9) serta memanfaatkan dokumentasi resmi Laravel       |
| Kehilangan data karena kesalahan input/hapus                           | Data organisasi hilang                           | Menyediakan konfirmasi sebelum hapus data serta melakukan backup basis data secara berkala                    |

# 13. Kriteria Keberhasilan

- Seluruh fitur pada Bagian 3 (Kebutuhan Fungsional) berhasil lolos pengujian Black Box Testing.

- Mahasiswa Jurusan JKB dapat mengakses informasi profil, divisi, dan portofolio proyek Teaching Factory melalui Landing Page tanpa hambatan.

- Koordinator Divisi dapat mengelola data proyek, kegiatan, dan pengumuman divisinya secara mandiri tanpa keterlibatan Administrator.

- Hak akses tiap role (Admin, Koordinator, Anggota) berfungsi sesuai batasan yang telah ditetapkan (tidak ada akses lintas divisi yang tidak sah).

- Sistem dapat diakses secara stabil melalui browser pada perangkat desktop maupun mobile.

# 14. Lampiran: Glosarium

| **Istilah** | **Keterangan**                                                                                                    |
|-------------|-------------------------------------------------------------------------------------------------------------------|
| MVC         | Model-View-Controller, pola arsitektur yang memisahkan data, tampilan, dan logika program                         |
| RBAC        | Role-Based Access Control, metode pemberian hak akses berdasarkan peran pengguna                                  |
| CRUD        | Create, Read, Update, Delete — empat operasi dasar pengelolaan data                                               |
| Migration   | Berkas Laravel untuk mendefinisikan dan mengubah struktur tabel basis data secara terversi                        |
| Eloquent    | ORM (Object Relational Mapping) bawaan Laravel untuk berinteraksi dengan basis data                               |
| Blade       | Mesin templating bawaan Laravel untuk membangun tampilan (View)                                                   |
| Middleware  | Lapisan program yang memproses permintaan sebelum mencapai Controller, contohnya untuk memeriksa autentikasi/role |
| Seeder      | Berkas Laravel untuk mengisi data awal/contoh ke dalam basis data                                                 |
