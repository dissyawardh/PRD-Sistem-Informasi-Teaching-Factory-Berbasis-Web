**PRODUCT REQUIREMENTS DOCUMENT (PRD)**

**Perancangan UI/UX**

**Sistem Informasi Teaching Factory Jurusan Komputer dan Bisnis Berbasis Website**

*Disusun berdasarkan Proposal Tugas Akhir*

Dissya Putri Wardhany — 240102040

Program Studi Teknik Informatika — Politeknik Negeri Cilacap

# Informasi Dokumen

| **Atribut**            | **Keterangan**                                                          |
|------------------------|-------------------------------------------------------------------------|
| Nama Dokumen           | PRD Perancangan UI/UX – Sistem Informasi Teaching Factory JKB           |
| Versi Dokumen          | 1.0                                                                     |
| Status                 | Draft untuk Tugas Akhir                                                 |
| Tools Desain           | Figma                                                                   |
| Dokumen Terkait        | PRD Pengembangan Sistem (Backend/Laravel), Proposal Tugas Akhir         |
| Target Pengguna Desain | Pengunjung/Mahasiswa, Anggota Divisi, Koordinator Divisi, Administrator |

# Daftar Isi

# 1. Pendahuluan

## 1.1 Latar Belakang

Sistem Informasi Teaching Factory (TeFa) JKB akan digunakan oleh dua kelompok pengguna dengan kebutuhan berbeda: pengunjung umum/mahasiswa yang hanya ingin melihat informasi organisasi, dan pengguna internal (Administrator, Koordinator Divisi, Anggota Divisi) yang mengelola atau melihat data melalui dashboard. Perbedaan kebutuhan ini menuntut perancangan antarmuka yang sederhana, informatif, dan konsisten, agar kedua kelompok pengguna dapat memperoleh dan mengelola informasi secara efektif tanpa kebingungan navigasi.

Dokumen ini merupakan turunan dari PRD Pengembangan Sistem dan berfokus khusus pada perancangan User Interface (UI) dan User Experience (UX), meliputi filosofi desain, design system (warna, tipografi, komponen), struktur navigasi, wireframe tiap halaman, alur pengguna, hingga rencana pengujian usability.

## 1.2 Tujuan Perancangan UI/UX

- Menghasilkan antarmuka yang sederhana, informatif, dan mudah dipahami oleh mahasiswa maupun anggota organisasi.

- Membangun identitas visual Teaching Factory JKB yang konsisten melalui skema warna dan tipografi yang telah ditentukan.

- Memastikan navigasi antara halaman publik dan dashboard berbasis role berjalan intuitif.

- Menyediakan pedoman desain (design system) yang dapat digunakan secara konsisten oleh pengembang saat proses implementasi front-end.

- Meningkatkan efisiensi dan kepuasan pengguna dalam menyelesaikan tugasnya (mencari informasi, mengelola data proyek/kegiatan/pengumuman).

## 1.3 Ruang Lingkup Perancangan

- Desain antarmuka untuk halaman publik: Landing Page, Profil Organisasi, Arsip Proyek, Login.

- Desain antarmuka dashboard untuk tiga role: Administrator, Koordinator Divisi, Anggota Divisi.

- Desain komponen UI (design system): tombol, form, tabel, kartu, badge, navigasi, timeline, modal konfirmasi.

- Pedoman responsif untuk tampilan desktop, tablet, dan mobile.

- Rencana pengujian usability sederhana terhadap prototipe desain.

# 2. Prinsip dan Filosofi Desain

Perancangan UI/UX mengacu pada prinsip dasar User Interface dan User Experience: antarmuka tidak hanya berfokus pada tampilan visual, tetapi juga pada kemudahan penggunaan, efisiensi, dan kepuasan pengguna dalam mencapai tujuannya. Berikut prinsip utama yang menjadi acuan perancangan.

| **Prinsip**                             | **Penerapan pada Sistem**                                                                                  |
|-----------------------------------------|------------------------------------------------------------------------------------------------------------|
| Kesederhanaan (Simplicity)              | Navigasi dikelompokkan jelas, form hanya menampilkan input yang relevan, tanpa elemen dekoratif berlebihan |
| Konsistensi (Consistency)               | Warna, tipografi, ukuran tombol, dan pola layout sama di seluruh halaman                                   |
| Umpan Balik (Feedback)                  | Setiap aksi (simpan, ubah, hapus) menampilkan notifikasi/alert yang jelas                                  |
| Pencegahan Kesalahan (Error Prevention) | Validasi form, konfirmasi sebelum hapus data, serta pembatasan akses sesuai role                           |
| Efisiensi Penggunaan                    | Fitur pencarian dan filter pada tabel/tampilan data yang panjang (proyek, kegiatan, anggota)               |
| Aksesibilitas                           | Kontras warna memadai, ukuran font terbaca, serta struktur heading yang jelas                              |
| Responsivitas                           | Tata letak menyesuaikan lebar layar (desktop, tablet, mobile) tanpa kehilangan fungsi                      |

# 3. Persona Pengguna

## 3.1 Pengunjung / Mahasiswa Umum

Mahasiswa Jurusan JKB yang belum tergabung dalam Teaching Factory dan ingin mengetahui profil, divisi, serta hasil kerja organisasi.

**Tujuan Pengguna:**

- Mengenal profil dan struktur Teaching Factory dengan cepat.

- Melihat contoh proyek/portofolio yang pernah dikerjakan.

**Kendala/Kebutuhan Desain:**

- Tidak familiar dengan istilah teknis organisasi — gunakan bahasa sederhana.

- Mengakses dari HP saat waktu senggang — wajib responsif.

## 3.2 Anggota Divisi

Mahasiswa yang telah tergabung dalam salah satu divisi TeFa dan menggunakan sistem untuk melihat informasi internal.

**Tujuan Pengguna:**

- Melihat timeline kegiatan agar tidak ketinggalan agenda.

- Melihat pengumuman dan dokumentasi proyek divisinya.

**Kendala/Kebutuhan Desain:**

- Hanya butuh akses baca (read-only) — sembunyikan tombol aksi (tambah/ubah/hapus).

- Perlu tampilan timeline yang mudah dipindai secara kronologis.

## 3.3 Koordinator Divisi

Pengurus yang bertanggung jawab mengelola data proyek, kegiatan, dan pengumuman pada divisinya.

**Tujuan Pengguna:**

- Menambahkan dokumentasi proyek/kegiatan/pengumuman dengan cepat.

- Memantau data yang sudah maupun belum dipublikasikan.

**Kendala/Kebutuhan Desain:**

- Butuh form input yang ringkas dengan validasi jelas.

- Perlu indikator status (draft/published) yang mudah dikenali.

## 3.4 Administrator

Pengelola tertinggi sistem yang mengatur seluruh data organisasi, divisi, anggota, dan akun pengguna.

**Tujuan Pengguna:**

- Memantau seluruh aktivitas dan data dari semua divisi.

- Mengelola akun dan hak akses pengguna dengan mudah.

**Kendala/Kebutuhan Desain:**

- Butuh dashboard ringkasan (jumlah proyek/kegiatan/pengumuman per divisi).

- Perlu tabel data dengan fitur pencarian/filter karena volume data lebih besar.

# 4. Design System

## 4.1 Palet Warna

Skema warna utama terdiri dari Navy, Emas (Gold), dan Putih, sesuai dengan identitas visual yang ditetapkan pada proposal, dilengkapi warna status untuk kebutuhan feedback antarmuka.

|     |                                                               |
|-----|---------------------------------------------------------------|
|     | Navy – \#1B2A4A (warna utama: header, sidebar, tombol primer) |

|     |                                           |
|-----|-------------------------------------------|
|     | Navy Dark – \#10192E (hover/active state) |

|     |                                                       |
|-----|-------------------------------------------------------|
|     | Gold – \#C9A227 (aksen: ikon aktif, badge, highlight) |

|     |                                                           |
|-----|-----------------------------------------------------------|
|     | Light Gold – \#FBF3DA (latar highlight/notifikasi ringan) |

|     |                                             |
|-----|---------------------------------------------|
|     | Putih – \#FFFFFF (latar utama/kartu konten) |

|     |                                                           |
|-----|-----------------------------------------------------------|
|     | Light Navy – \#EEF1F6 (latar section/tabel selang-seling) |

|     |                                               |
|-----|-----------------------------------------------|
|     | Abu-abu – \#666666 (teks sekunder/keterangan) |

| **Warna Status** | **Kode** | **Penggunaan**                       |
|------------------|----------|--------------------------------------|
| Sukses           | \#2E7D32 | Notifikasi berhasil simpan/ubah data |
| Peringatan       | \#ED8936 | Status draft, data belum lengkap     |
| Bahaya/Error     | \#C0392B | Notifikasi gagal, tombol hapus       |
| Informasi        | \#2B6CB0 | Tooltip atau catatan bantuan         |

## 4.2 Tipografi

| **Elemen**              | **Font** | **Ukuran (Desktop)** | **Bobot**       |
|-------------------------|----------|----------------------|-----------------|
| Judul Halaman (H1)      | Poppins  | 28–32 px             | SemiBold/Bold   |
| Sub-judul (H2)          | Poppins  | 22–24 px             | SemiBold        |
| Sub-judul (H3)          | Poppins  | 18–20 px             | Medium          |
| Isi/Body Text           | Poppins  | 14–16 px             | Regular         |
| Label Form & Keterangan | Poppins  | 12–13 px             | Regular/Medium  |
| Tombol (Button)         | Poppins  | 14 px                | Medium/SemiBold |

Poppins dipilih karena bentuk huruf geometris yang modern, mudah dibaca pada berbagai ukuran layar, serta memberi kesan profesional yang sesuai dengan identitas Teaching Factory.

## 4.3 Tata Letak & Grid

- Lebar konten maksimum (max-width) 1200px pada tampilan desktop agar teks dan kartu tidak melebar berlebihan.

- Grid 12 kolom digunakan untuk mengatur kartu proyek, kegiatan, dan statistik dashboard.

- Jarak antar elemen (spacing) mengikuti kelipatan 8px (8, 16, 24, 32px) untuk menjaga konsistensi visual.

- Sudut elemen (border-radius) menggunakan nilai 8px pada kartu dan tombol untuk kesan modern namun tetap formal.

## 4.4 Komponen UI Utama

| **Komponen**                 | **Spesifikasi Desain**                                                                                           |
|------------------------------|------------------------------------------------------------------------------------------------------------------|
| Tombol Primer                | Latar Navy, teks putih, hover menjadi Navy Dark; digunakan untuk aksi utama (Simpan, Login, Tambah Data)         |
| Tombol Sekunder              | Latar putih dengan border Navy, teks Navy; digunakan untuk aksi netral (Batal, Kembali)                          |
| Tombol Bahaya                | Latar merah (#C0392B), teks putih; digunakan khusus untuk aksi Hapus, selalu disertai dialog konfirmasi          |
| Input Form                   | Border abu-abu tipis, radius 8px, label di atas input, pesan error berwarna merah di bawah input                 |
| Kartu (Card)                 | Latar putih, bayangan (shadow) tipis, radius 8px; digunakan pada kartu proyek, kegiatan, dan statistik dashboard |
| Badge Status                 | Bentuk pil (rounded-full) kecil: kuning untuk 'Draft', hijau untuk 'Published'                                   |
| Tabel Data                   | Header berlatar Navy dengan teks putih, baris data selang-seling (zebra) warna Light Navy untuk keterbacaan      |
| Navigasi Sidebar (Dashboard) | Latar Navy penuh, ikon dan teks putih, menu aktif ditandai aksen Gold di sisi kiri                               |
| Navigasi Atas (Landing Page) | Latar putih/transparan dengan logo dan menu utama, tombol 'Login' beraksen Gold                                  |
| Timeline Kegiatan            | Garis vertikal Navy dengan titik penanda Gold di tiap kegiatan, disusun kronologis                               |
| Modal Konfirmasi             | Muncul di tengah layar dengan overlay gelap transparan; digunakan sebelum aksi hapus data                        |

# 5. Arsitektur Informasi (Sitemap & Navigasi)

## 5.1 Sitemap

Struktur navigasi dibagi menjadi dua area besar: area publik (dapat diakses tanpa login) dan area dashboard (memerlukan login, konten menyesuaikan role).

| **Area**                        | **Halaman**                                                                 |
|---------------------------------|-----------------------------------------------------------------------------|
| Publik                          | Landing Page → Profil Organisasi → Struktur & Divisi → Arsip Proyek → Login |
| Dashboard (semua role)          | Dashboard (ringkasan) → Profil Akun → Logout                                |
| Dashboard (Koordinator & Admin) | Kelola Proyek → Kelola Kegiatan → Kelola Pengumuman                         |
| Dashboard (khusus Admin)        | Kelola Organisasi (Divisi & Anggota) → Kelola Akun Pengguna                 |

## 5.2 Pola Navigasi

- Halaman publik menggunakan navigasi atas (top navbar) horizontal dengan menu: Beranda, Profil, Divisi, Proyek, Login.

- Halaman dashboard menggunakan navigasi samping (sidebar) vertikal berisi menu sesuai hak akses role yang sedang login.

- Menu yang tidak dapat diakses oleh suatu role disembunyikan sepenuhnya dari tampilan (bukan hanya dinonaktifkan), agar antarmuka tetap sederhana.

- Breadcrumb ditampilkan pada halaman dashboard untuk membantu pengguna mengetahui posisinya, contoh: Dashboard \> Kelola Proyek \> Tambah Proyek.

# 6. Wireframe Halaman (Deskripsi Tata Letak)

Wireframe berikut menggambarkan struktur tata letak (bukan tampilan visual final) untuk memandu proses desain di Figma maupun implementasi Blade template.

## 6.1 Landing Page

|                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|
| **LANDING PAGE**                                                                                            |
| ▢ Navbar atas: Logo TeFa JKB \| Beranda \| Profil \| Divisi \| Proyek \| \[Tombol Login\]                   |
| ▢ Hero section: Judul “Teaching Factory Jurusan Komputer dan Bisnis” + deskripsi singkat + gambar/ilustrasi |
| ▢ Section Profil: Visi & Misi organisasi (2 kolom teks)                                                     |
| ▢ Section Divisi: 3 kartu (Desain Grafis, Multimedia, Web) dengan ikon dan deskripsi singkat                |
| ▢ Section Struktur Organisasi: bagan/daftar pengurus utama                                                  |
| ▢ Section Arsip Proyek: grid kartu proyek terpublikasi (gambar, judul, divisi, tanggal)                     |
| ▢ Footer: kontak, alamat, tautan sosial media Teaching Factory                                              |

## 6.2 Halaman Login

|                                                                                     |
|-------------------------------------------------------------------------------------|
| **LOGIN**                                                                           |
| ▢ Logo/nama sistem di bagian atas form                                              |
| ▢ Input Email                                                                       |
| ▢ Input Password (dengan ikon show/hide password)                                   |
| ▢ \[Tombol Login\] — latar Navy penuh lebar                                         |
| ▢ Teks kecil: “Hubungi Admin jika lupa password”                                    |
| ▢ Latar belakang halaman menggunakan warna Navy dengan aksen Gold di sisi ilustrasi |

## 6.3 Dashboard (Umum, Menyesuaikan Role)

|                                                                                                  |
|--------------------------------------------------------------------------------------------------|
| **DASHBOARD**                                                                                    |
| ▢ Sidebar kiri: Logo, menu navigasi sesuai role, tombol Logout di bagian bawah                   |
| ▢ Header atas: nama pengguna yang login + badge role (Admin/Koordinator/Anggota)                 |
| ▢ Baris kartu statistik: Total Proyek \| Total Kegiatan \| Total Pengumuman (angka besar + ikon) |
| ▢ Section 'Kegiatan Mendatang': daftar 3–5 kegiatan terdekat dalam bentuk mini-timeline          |
| ▢ Section 'Pengumuman Terbaru': daftar 3–5 pengumuman terbaru                                    |

## 6.4 Kelola Proyek / Kegiatan / Pengumuman (Admin & Koordinator)

|                                                                                                                                                         |
|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| **KELOLA PROYEK**                                                                                                                                       |
| ▢ Judul halaman + breadcrumb (Dashboard \> Kelola Proyek)                                                                                               |
| ▢ Baris aksi: kolom pencarian (search) di kiri, \[+ Tambah Proyek\] di kanan                                                                            |
| ▢ Tabel data: Judul \| Divisi \| Tanggal \| Status (badge) \| Aksi (Ubah/Hapus)                                                                         |
| ▢ Paginasi di bagian bawah tabel                                                                                                                        |
| ▢ Form Tambah/Ubah (halaman atau modal terpisah): Judul, Deskripsi, Divisi (dropdown), Instansi Mitra, Tanggal, Upload Gambar, Status (draft/published) |

Pola wireframe yang sama diterapkan untuk halaman Kelola Kegiatan (tambahan input Tanggal & Waktu) dan Kelola Pengumuman (tambahan input Isi Pengumuman berupa rich text/textarea).

## 6.5 Kelola Organisasi & Kelola Akun (Khusus Admin)

|                                                                              |
|------------------------------------------------------------------------------|
| **KELOLA ORGANISASI**                                                        |
| ▢ Tab navigasi: Divisi \| Anggota \| Struktur Organisasi                     |
| ▢ Tab Divisi: tabel nama divisi + deskripsi + \[+ Tambah Divisi\]            |
| ▢ Tab Anggota: tabel nama, divisi, jabatan, foto + filter berdasarkan divisi |
| ▢ Tab Struktur Organisasi: form/urutan jabatan pengurus inti                 |

|                                                                                                                                        |
|----------------------------------------------------------------------------------------------------------------------------------------|
| **KELOLA AKUN PENGGUNA**                                                                                                               |
| ▢ Tabel akun: Nama \| Email \| Role \| Divisi (jika ada) \| Status Aktif \| Aksi                                                       |
| ▢ \[+ Tambah Akun\] membuka form: Nama, Email, Password, Role (dropdown: admin/koordinator/anggota), Divisi (muncul jika role ≠ admin) |
| ▢ Toggle aktif/nonaktif akun tanpa perlu menghapus data                                                                                |

# 7. Alur Pengguna (User Flow)

## 7.1 Alur Pengunjung Melihat Informasi

1.  Buka Landing Page

2.  Klik menu Divisi/Proyek untuk melihat detail

3.  Membaca informasi tanpa perlu login

4.  (Opsional) Klik Login jika merupakan anggota TeFa

## 7.2 Alur Koordinator Menambahkan Dokumentasi Proyek

1.  Login menggunakan akun Koordinator Divisi

2.  Diarahkan ke Dashboard

3.  Klik menu Kelola Proyek pada sidebar

4.  Klik tombol + Tambah Proyek

5.  Mengisi form (judul, deskripsi, tanggal, gambar, status)

6.  Klik Simpan → sistem menampilkan notifikasi sukses

7.  Proyek dengan status 'published' otomatis muncul di Landing Page

## 7.3 Alur Administrator Mengatur Akun Pengguna Baru

1.  Login sebagai Administrator

2.  Buka menu Kelola Akun Pengguna

3.  Klik + Tambah Akun

4.  Isi nama, email, password, pilih role dan divisi (jika perlu)

5.  Klik Simpan → akun baru aktif dan dapat langsung digunakan untuk login

# 8. Pedoman Desain Responsif

| **Breakpoint** | **Lebar Layar** | **Penyesuaian Tata Letak**                                                                                                                             |
|----------------|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Desktop        | ≥ 1024px        | Sidebar dashboard tampil penuh; grid kartu 3–4 kolom; tabel tampil lengkap                                                                             |
| Tablet         | 768–1023px      | Sidebar dapat disembunyikan (collapsible); grid kartu 2 kolom                                                                                          |
| Mobile         | \< 768px        | Sidebar berubah menjadi menu hamburger; grid kartu 1 kolom; tabel data ditampilkan sebagai daftar kartu (card list) agar tidak perlu scroll horizontal |

# 9. Aksesibilitas & Usability

- Kontras warna teks terhadap latar minimal memenuhi rasio 4.5:1 (misalnya teks putih di atas latar Navy) agar mudah dibaca.

- Seluruh gambar (dokumentasi proyek, foto anggota) menyertakan teks alternatif (alt text) yang deskriptif.

- Ukuran target sentuh (tombol/link) pada tampilan mobile minimal 44x44px agar mudah ditekan.

- Label form selalu ditampilkan (tidak hanya placeholder) agar pengguna tetap mengetahui jenis input meski sudah mulai mengetik.

- Pesan error ditampilkan berdekatan dengan input yang salah, disertai penjelasan singkat cara memperbaikinya.

# 10. Rencana Pengujian Usability

Pengujian dilakukan terhadap prototipe desain (Figma) sebelum masuk tahap implementasi, dengan melibatkan beberapa mahasiswa/anggota TeFa sebagai responden.

| **Skenario Tugas**                                       | **Tujuan Pengujian**                       | **Indikator Keberhasilan**                                      |
|----------------------------------------------------------|--------------------------------------------|-----------------------------------------------------------------|
| Mencari informasi profil & divisi TeFa dari Landing Page | Menilai kejelasan navigasi publik          | Responden menemukan informasi dalam \< 3 klik                   |
| Login dan menemukan menu Kelola Proyek                   | Menilai kejelasan navigasi dashboard       | Responden menemukan menu tanpa bantuan                          |
| Menambahkan data proyek baru melalui form                | Menilai kejelasan form & validasi          | Responden berhasil menyimpan data tanpa kesalahan berulang      |
| Membedakan status draft dan published pada tabel         | Menilai kejelasan indikator visual (badge) | Responden dapat membedakan status dengan benar                  |
| Mengakses sistem melalui perangkat mobile                | Menilai kenyamanan tampilan responsif      | Responden dapat menyelesaikan tugas tanpa kesulitan scroll/zoom |

Hasil pengujian usability digunakan sebagai bahan perbaikan desain sebelum prototipe diimplementasikan ke dalam kode program (Blade template) pada tahap pengembangan sistem.

# 11. Deliverable & Rencana Kerja Desain

| **Deliverable**      | **Deskripsi**                                                        | **Format**      |
|----------------------|----------------------------------------------------------------------|-----------------|
| Style Guide          | Dokumentasi warna, tipografi, dan komponen UI (Bagian 4 dokumen ini) | Figma / PDF     |
| Wireframe            | Rancangan tata letak low-fidelity seluruh halaman (Bagian 6)         | Figma           |
| Mockup High-Fidelity | Desain visual lengkap dengan warna, ikon, dan gambar                 | Figma           |
| Prototype Interaktif | Simulasi alur klik antar halaman untuk pengujian usability           | Figma Prototype |
| Aset Desain          | Ikon, logo, dan gambar pendukung siap pakai untuk implementasi       | SVG/PNG         |

## 11.1 Tahapan Kerja Desain

| **Tahap**                           | **Aktivitas**                                                                          |
|-------------------------------------|----------------------------------------------------------------------------------------|
| 1\. Riset & Persona                 | Wawancara singkat dengan pengurus TeFa, menyusun persona pengguna                      |
| 2\. Information Architecture        | Menyusun sitemap dan alur navigasi                                                     |
| 3\. Wireframing                     | Membuat rancangan tata letak low-fidelity seluruh halaman                              |
| 4\. Design System                   | Menetapkan warna, tipografi, dan komponen UI reusable                                  |
| 5\. High-Fidelity Mockup            | Menerapkan design system ke seluruh wireframe                                          |
| 6\. Prototyping & Usability Testing | Menghubungkan antar halaman di Figma dan menguji ke responden                          |
| 7\. Handoff ke Implementasi         | Menyerahkan spesifikasi desain (warna, ukuran, aset) kepada tahap coding Laravel/Blade |

# 12. Lampiran: Glosarium Desain

| **Istilah**              | **Keterangan**                                                                                       |
|--------------------------|------------------------------------------------------------------------------------------------------|
| Wireframe                | Rancangan tata letak halaman tanpa detail visual (warna, gambar final), fokus pada struktur & fungsi |
| Mockup                   | Rancangan visual halaman yang sudah menerapkan warna, tipografi, dan gambar mendekati tampilan akhir |
| Prototype                | Simulasi interaktif antar halaman untuk menguji alur penggunaan sebelum coding                       |
| Design System            | Kumpulan pedoman desain (warna, tipografi, komponen) yang digunakan secara konsisten                 |
| Information Architecture | Struktur pengelompokan dan navigasi konten dalam sebuah sistem/website                               |
| Usability Testing        | Pengujian terhadap desain dengan melibatkan pengguna nyata untuk menilai kemudahan penggunaan        |
| Breakpoint               | Titik lebar layar tertentu yang menjadi acuan perubahan tata letak responsif                         |
