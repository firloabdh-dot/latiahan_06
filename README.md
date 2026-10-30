# Catatan Praktikum - Aplikasi Profil Flutter

**Nama:** Firlo Abdul Fatur  
**Role:** Mahasiswa Global Institute  

---

## Hari 1: Kerangka Dasar & Refactoring Awal

### Hari 1: Sesi Pagi (Kerangka Dasar)
Di sesi pagi Hari 1 ini, saya fokus bikin kerangka dasar halaman profil dan benerin beberapa *error code* yang ada di materi awal:

1. **Jarak foto profil ke nama terlalu mepet**
   - **Masalah:** Di kode awal pakenya `SizedBox(width: 16)`. Karena posisinya di dalam `Column` (susunannya ke bawah), `width` itu gak ada efeknya sama sekali, jadi fotonya nempel sama teks nama.
   - **Solusi:** Diganti jadi `SizedBox(height: 16)` biar ada jarak ke bawah.
   - **Data Profil:** Nama dan *role* saya ubah pake nama sendiri (`Firlo Abdul Fatur` - `Mahasiswa Global Institute`).

2. **Error kurung penutup dobel di paling bawah**
   - **Masalah:** Di barisan paling akhir kode awal ada kelebihan tanda tutup kurung dan titik koma `); );` yang bikin kodenya merah/*error* pas mau dijalankan.
   - **Solusi:** Dihapus penutup yang lebihnya biar kodenya normal lagi.

3. **Kodenya masih numpuk di satu tempat**
   - **Masalah:** Awalnya semua kodenya digabungin di `main.dart`.
   - **Solusi:** Dipisah jadi 2 file sesuai arahan tugas:
     - `main.dart` buat jalanin aplikasinya.
     - `profile_page.dart` buat isi tampilan profilnya.

### Hari 1: Sesi Siang (Extract Widget Bagian 1)
Di sesi siang ini kodenya di-*refactor* / dipecah biar lebih modular dan rapi:
1. **Bikin widget `ProfileAvatar`:** Buat nampung komponen foto profil (`CircleAvatar`).
2. **Bikin widget `ProfileInfo`:** Buat nampung teks nama sama *role*, lengkap pake parameter *data passing* (`userName` dan `role`).

---

## Hari 2: Menambahkan Komponen Statistik Profil

### Hari 2: Sesi Pagi (Membangun Baris Statistik)
Di sesi pagi Hari 2 ini, saya nambahin baris statistik profil (`Row` yang isinya 3 `Column` buat Proyek, Followers, dan Following) sekalian benerin 2 *bug* dari kode awal:

1. **Jarak antar item statistik mepet (Proyek ke Followers)**
   - **Masalah:** Di kode awal tertulis `SizedBox(height: 24)` di antara Proyek dan Followers. Karena posisinya di dalam `Row` (susunan menyamping), `height` gak ngasih jarak ke samping.
   - **Solusi:** Diganti jadi `SizedBox(width: 24)` biar jarak kiri-kanannya rapi.

2. **Error tipe data di angka Following**
   - **Masalah:** Angka pada `Following` ditulis `42` (tipe `int` tanpa kutip), padahal parameter `count` dan widget `Text` butuh tipe data `String`.
   - **Solusi:** Ditambahin tanda kutip jadi `'42'`.

### Hari 2: Sesi Siang (Extract Widget Bagian 2)
Di sesi siang ini, bagian baris statistik di-*refactor* jadi 2 *custom widget* mandiri:
1. **Bikin widget `ProfileStats`:** Buat nampung `Container` biru muda dan `Row` deretan statistiknya.
2. **Bikin widget `StatItem`:** Buat nampung susunan `Column` angka (`count`) dan keterangannya (`label`) pake parameter *required*.

---

## Hari 3: Menambahkan Daftar Pengalaman (ListView)

### Hari 3: Sesi Siang (Implementasi ListView & Expanded)
Di sesi pagi Hari 3 ini, saya nambahin daftar pengalaman kerja yang bisa di-*scroll* pake `ListView.builder` dan benerin 2 *error* di kode awal:

1. **Kurang tanda koma di `List<String> experiences`**
   - **Masalah:** Di urutan ke-3 (`'Lead Developer - Aplikasi Sekurindo'`), lupa dikasih tanda koma (`,`) di ujungnya, jadinya teks ke-3 dan ke-4 malah nyatu jadi satu baris.
   - **Solusi:** Ditambahin tanda koma di ujung string ke-3 biar kebaca 4 item terpisah.

2. **Error layar merah (*Unbounded Height*) pas pasang `ListView.builder`**
   - **Masalah:** Di kode awal, `ListView.builder` langsung ditaruh mentah-mentah di dalam `Column`, jadinya *error* karena `ListView` bingung batas tinggi layarnya seberapa.
   - **Solusi:** `ListView.builder`-nya dibungkus pake widget `Expanded` biar otomatis ngambil sisa ruang layar di bawahnya.

### Hari 3: Sesi Malam (Merapikan Tampilan Item List dengan Card)
Di sesi siang ini, tampilan tiap baris di `ListView.builder` di-*refactor* dan dirapiin:
1. **Bikin widget `ExperienceCard`:** Memecah `ListTile` keluar jadi *custom widget* sendiri dengan parameter `experience`.
2. **Styling pake `Card` dan Ikon:** Bungkus `ListTile` pake widget `Card` (`elevation: 2` dan `margin` vertikal 6) terus ditambahin ikon koper (`Icons.work` warna biru) di sebelah kirinya (`leading`).