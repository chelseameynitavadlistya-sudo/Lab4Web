# Praktikum 4 – Layout Website Sederhana (HTML & CSS)

Proyek praktikum pemrograman web untuk membuat **layout website sederhana** menggunakan HTML5 dan CSS3 (tanpa framework). Layout terdiri dari header, navigasi, hero panel, konten utama, sidebar, dan footer, serta tiga halaman: **Home**, **About**, dan **Kontak**.

- **Nama:** Chelsea Meynita
- **Program Studi:** Teknik Informatika
- **Kampus:** Universitas Pelita Bangsa

---

## Daftar Isi

1. [Tujuan Praktikum](#1-tujuan-praktikum)
2. [Struktur Proyek](#2-struktur-proyek)
3. [Cara Menjalankan](#3-cara-menjalankan)
4. [Struktur Layout](#4-struktur-layout)
5. [Langkah-Langkah Praktikum](#5-langkah-langkah-praktikum)
6. [Penjelasan Kode CSS](#6-penjelasan-kode-css)
7. [Penjelasan Setiap Halaman](#7-penjelasan-setiap-halaman)
8. [Catatan & Pengembangan Lanjutan](#8-catatan--pengembangan-lanjutan)

---

## 1. Tujuan Praktikum

Setelah menyelesaikan praktikum ini, mahasiswa mampu:

- Membuat struktur halaman web dengan elemen semantik HTML5 (`header`, `nav`, `section`, `article`, `aside`, `footer`).
- Menghubungkan file CSS eksternal ke halaman HTML.
- Mengatur layout dua kolom (konten utama + sidebar) menggunakan `float`.
- Membuat navigasi horizontal dengan status menu aktif.
- Membuat komponen: hero panel, tombol, kolom 3 box, artikel dengan gambar kiri/kanan, widget sidebar, dan formulir kontak.
- Menggunakan satu file CSS yang dipakai bersama oleh banyak halaman.

---

## 2. Struktur Proyek

```
lab4_layout/
├── home.html      # Halaman utama (hero, 3 kolom, artikel, sidebar)
├── about.html     # Halaman profil & portofolio
├── kontak.html    # Halaman formulir kontak
├── style.css      # Stylesheet bersama untuk semua halaman
└── photo.jpg      # Foto profil yang dipakai di halaman About
```

| File | Fungsi | Ukuran |
|------|--------|--------|
| `home.html` | Halaman beranda dengan hero panel, 3 box kolom, 2 artikel (gambar kiri & kanan), dan sidebar widget | ± 4,3 KB |
| `about.html` | Profil singkat, foto, daftar portofolio, dan sidebar keahlian | ± 2,8 KB |
| `kontak.html` | Formulir kontak (nama, email, subjek, pesan) dan info kontak | ± 3,0 KB |
| `style.css` | Seluruh aturan tampilan: layout, navigasi, komponen, form | ± 4,6 KB |
| `photo.jpg` | Foto profil (960 × 1053 px) | ± 78 KB |

---

## 3. Cara Menjalankan

1. Ekstrak `lab4_layout.zip` ke satu folder. Pastikan semua file berada dalam **folder yang sama**.
2. Buka file `home.html` dengan browser (Chrome, Firefox, Edge, dll.) — klik dua kali atau klik kanan → *Open with*.
3. Gunakan menu navigasi di bagian atas untuk berpindah antar halaman.

> **Opsional:** Jika memakai VS Code, install ekstensi **Live Server**, lalu klik kanan `home.html` → *Open with Live Server* agar halaman otomatis refresh saat file disimpan.

> **Catatan:** Gambar placeholder di halaman Home dimuat dari `dummyimage.com`, sehingga membutuhkan koneksi internet.

---

## 4. Struktur Layout

Semua halaman memakai kerangka yang sama, dibungkus oleh `<div id="container">` selebar **960px** dan berada di tengah layar.

```
┌──────────────────────────────────────────────┐
│ header        (judul situs)                  │
├──────────────────────────────────────────────┤
│ nav           Home | Artikel | About | Kontak│
├──────────────────────────────────────────────┤
│ #hero         (judul besar + deskripsi)      │
├────────────────────────────┬─────────────────┤
│ #wrapper                   │                 │
│  ┌──────────────────────┐  │  #sidebar       │
│  │ #main   (640px)      │  │  (260px)        │
│  │  - konten / artikel  │  │  - widget-box   │
│  │  - form / portfolio  │  │  - widget-box   │
│  └──────────────────────┘  │                 │
├────────────────────────────┴─────────────────┤
│ footer        © 2021 - Universitas Pelita    │
└──────────────────────────────────────────────┘
```

Perhitungan lebar: `20px padding + 640px (main) + 260px (sidebar) + 20px padding = 940px` ditambah celah di antaranya, sehingga pas di dalam container 960px.

---

## 5. Langkah-Langkah Praktikum

### Langkah 1 – Membuat folder dan file proyek

1. Buat folder bernama `lab4_layout`.
2. Di dalamnya buat file kosong: `home.html`, `about.html`, `kontak.html`, dan `style.css`.
3. Simpan foto profil sebagai `photo.jpg` di folder yang sama.

### Langkah 2 – Membuat kerangka dasar HTML (`home.html`)

Tulis struktur dasar HTML5 dan hubungkan file CSS eksternal melalui tag `<link>` di dalam `<head>`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Layout Sederhana</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div id="container">
        <!-- seluruh konten halaman -->
    </div>
</body>
</html>
```

### Langkah 3 – Menambahkan header dan navigasi

Di dalam `#container`, tambahkan `header` dan `nav`. Link yang sedang dibuka diberi `class="active"`:

```html
<header>
    <h1>Layout Sederhana</h1>
</header>

<nav>
    <a href="home.html" class="active">Home</a>
    <a href="artikel.html">Artikel</a>
    <a href="about.html">About</a>
    <a href="kontak.html">Kontak</a>
</nav>
```

### Langkah 4 – Menambahkan hero panel

Hero panel adalah area besar berisi sambutan dan tombol *call to action*:

```html
<section id="hero">
    <h1>Hello World!</h1>
    <p>Lorem ipsum dolor sit amet, ...</p>
    <a href="home.html" class="btn btn-large">Learn more &raquo;</a>
</section>
```

### Langkah 5 – Membuat wrapper dua kolom (main + sidebar)

Buat `#wrapper` yang membungkus `#main` (konten utama) dan `#sidebar` (kolom samping):

```html
<section id="wrapper">
    <section id="main">
        <!-- konten utama -->
    </section>

    <aside id="sidebar">
        <!-- widget -->
    </aside>
</section>
```

### Langkah 6 – Mengisi konten utama halaman Home

Di dalam `#main` tambahkan:

1. **Tiga kolom box** (`.row` berisi tiga `.box-col`) — masing-masing memuat gambar bulat, judul, deskripsi, dan tombol *View detail*.
2. **Garis pemisah** `<hr class="divider">`.
3. **Artikel pertama** — gambar di **kiri** (`.entry-img`).
4. **Garis pemisah** lagi.
5. **Artikel kedua** — gambar di **kanan** (`.entry-img right-img`).

```html
<article class="entry">
    <h2>First featurette heading.</h2>
    <div class="entry-img right-img">
        <img src="https://dummyimage.com/150/7b8a70/fff.png" alt="">
    </div>
    <p>Lorem ipsum dolor sit amet, ...</p>
</article>
```

### Langkah 7 – Mengisi sidebar

Tambahkan beberapa `widget-box` di dalam `<aside id="sidebar">`: satu berisi daftar link, satu berisi teks.

```html
<div class="widget-box">
    <h3 class="title">Widget Header</h3>
    <ul>
        <li><a href="#">Widget Link</a></li>
        ...
    </ul>
</div>
```

### Langkah 8 – Menambahkan footer

Letakkan `footer` setelah `#wrapper`, masih di dalam `#container`:

```html
<footer>
    <p>&copy; 2021 - Universitas Pelita Bangsa</p>
</footer>
```

### Langkah 9 – Membuat `style.css` secara bertahap

Tulis CSS dalam urutan yang sama dengan struktur HTML agar mudah dilacak:

1. **Body & container** – font, background, lebar 960px, `margin: 0 auto`.
2. **Header** dan **navigasi** (warna biru `#3e73e6`, hover/active `#2b5bc4`).
3. **Hero panel** – background abu-abu `#e4e4e5`, padding 40px.
4. **Tombol** `.btn`, `.btn-large`, `.btn-default`.
5. **Layout** `#wrapper`, `#main` (`float: left`, 640px), `#sidebar` (`float: right`, 260px).
6. **Tiga kolom** `.row` / `.box-col` (masing-masing 33.333%).
7. **Artikel** `.entry`, `.entry-img`, `.entry-img.right-img`.
8. **Widget sidebar** `.widget-box`.
9. **Footer** – background gelap `#222`, `clear: both`.

### Langkah 10 – Membuat halaman About (`about.html`)

1. Salin kerangka `home.html` (header, nav, hero, wrapper, footer).
2. Pindahkan `class="active"` ke link **About**.
3. Ubah hero menjadi *"Tentang Saya"*.
4. Di `#main` isi artikel **Profil Singkat** (foto `photo.jpg` + deskripsi diri) dan artikel **Portfolio** berisi tiga `.portfolio-item`.
5. Di sidebar isi widget **Navigasi Lain** dan **Keahlian**.
6. Tambahkan CSS `.portfolio-item` di `style.css`.

### Langkah 11 – Membuat halaman Kontak (`kontak.html`)

1. Salin kerangka yang sama dan pindahkan `class="active"` ke link **Kontak**.
2. Ubah hero menjadi *"Hubungi Kami"*.
3. Di `#main`, buat formulir dengan field Nama, Email, Subjek, dan Pesan (`textarea`), lalu tombol **Kirim Pesan**.
4. Di sidebar isi widget **Info Kontak** dan **Media Sosial**.
5. Tambahkan CSS `.contact-form`, `.form-group`, dan efek `:focus` di `style.css`.

### Langkah 12 – Pengujian

- Buka ketiga halaman di browser dan pastikan layout konsisten.
- Klik semua menu navigasi dan pastikan menu aktif berubah sesuai halaman.
- Pastikan sidebar berada di kanan dan footer berada di bawah seluruh konten.
- Coba kirim form tanpa mengisi field wajib untuk melihat validasi bawaan browser.

---

## 6. Penjelasan Kode CSS

| Selector | Fungsi |
|----------|--------|
| `#container` | Membatasi lebar halaman 960px, di tengah layar, dengan bayangan tipis |
| `nav a` | Link navigasi bergaya blok horizontal (`inline-block`) |
| `nav a.active`, `nav a:hover` | Menandai menu aktif / saat disorot kursor |
| `#hero` | Panel besar berlatar abu-abu di bawah navigasi |
| `.btn`, `.btn-large`, `.btn-default` | Gaya tombol: biru, sudut membulat, hover lebih gelap |
| `#wrapper` | `overflow: hidden` agar float di dalamnya tidak "keluar" dari pembungkus |
| `#main` / `#sidebar` | Layout dua kolom memakai `float: left` dan `float: right` |
| `.row` + `.box-col` | Tiga kolom sama lebar (33.333%) dengan `box-sizing: border-box` |
| `.image-circle` | `border-radius: 50%` untuk gambar bulat |
| `.divider` | Garis pemisah tipis antar bagian |
| `.entry` | Pembungkus artikel; `overflow: hidden` untuk membersihkan float gambar |
| `.entry-img` / `.right-img` | Gambar mengambang di kiri / kanan teks |
| `.widget-box` | Kotak sidebar bergaris dengan judul berlatar biru |
| `footer` | `clear: both` agar berada di bawah kolom yang mengambang |
| `.contact-form`, `.form-group` | Tata letak dan gaya input formulir |
| `.form-group input:focus` | Border biru dan efek glow saat input dipilih |
| `.portfolio-item` | Gaya daftar proyek di halaman About |

### Konsep penting

- **Float layout** – `#main` dan `#sidebar` ditempatkan berdampingan dengan `float`. Setelah elemen float, parent harus "dibersihkan" (`overflow: hidden` atau `clear: both`) agar tinggi parent ikut menyesuaikan.
- **`box-sizing: border-box`** – padding dan border dihitung ke dalam lebar elemen, sehingga lebar 33.333% tidak melebihi baris.
- **Satu CSS untuk banyak halaman** – ketiga halaman memuat `style.css` yang sama sehingga tampilan seragam dan mudah dirawat.
- **Class `.active`** – ditempatkan manual pada link halaman yang sedang dibuka.

---

## 7. Penjelasan Setiap Halaman

### `home.html` – Beranda

| Bagian | Isi |
|--------|-----|
| Hero | Judul "Hello World!", paragraf, tombol *Learn more* |
| Main | 3 kolom box bergambar bulat, artikel gambar kiri, artikel gambar kanan |
| Sidebar | Widget Header (5 link) dan Widget Text |

### `about.html` – Tentang Saya

| Bagian | Isi |
|--------|-----|
| Hero | "Tentang Saya" dan deskripsi singkat halaman |
| Main | Profil singkat dengan foto `photo.jpg`, serta Portfolio (Project 1–3) |
| Sidebar | Navigasi lain dan daftar keahlian (HTML5, CSS3, dasar pemrograman web, desain layout, Git/GitHub) |

### `kontak.html` – Hubungi Kami

| Bagian | Isi |
|--------|-----|
| Hero | "Hubungi Kami" dan pengantar form |
| Main | Formulir: Nama Lengkap, Alamat Email, Subjek, Pesan/Komentar, tombol *Kirim Pesan* |
| Sidebar | Info kontak kampus dan tautan media sosial |

> Field **Nama**, **Email**, dan **Pesan** memakai atribut `required`, dan field email memakai `type="email"` sehingga divalidasi otomatis oleh browser.

---

## 8. Catatan & Pengembangan Lanjutan

**Catatan saat ini**

- Menu **Artikel** mengarah ke `artikel.html` yang **belum ada** di folder proyek, sehingga link tersebut akan menampilkan halaman tidak ditemukan. Buat file `artikel.html` dengan kerangka yang sama atau arahkan link ke halaman lain.
- Tombol *Learn more* dan beberapa link widget masih berupa placeholder (`#` atau mengarah ke `home.html`).
- Form kontak memakai `action="#"` sehingga belum mengirim data ke server.
- Lebar container tetap (960px), jadi tampilan belum sepenuhnya responsif di layar kecil.
- Gambar di Home bergantung pada layanan eksternal `dummyimage.com`.
- Teks footer masih menampilkan tahun 2021.

**Ide pengembangan**

- Membuat halaman `artikel.html`.
- Mengganti layout `float` dengan **Flexbox** atau **CSS Grid**.
- Menambahkan **media query** agar layout responsif di perangkat mobile.
- Menghubungkan form ke backend (misalnya PHP atau layanan form pihak ketiga).
- Mengganti gambar placeholder dengan gambar lokal.

---

## Lisensi

Proyek ini dibuat untuk keperluan pembelajaran pada praktikum Pemrograman Web, Universitas Pelita Bangsa.
