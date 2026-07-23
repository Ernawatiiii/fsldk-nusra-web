# FSLDK Nusa Tenggara — Website Resmi

Website resmi **Forum Silaturahmi Lembaga Dakwah Kampus (FSLDK) Nusa Tenggara**, forum yang menyatukan 16 Lembaga Dakwah Kampus (LDK) se-Nusa Tenggara (Lombok & Sumbawa) dalam satu wadah kolaborasi dakwah.

🔗 **Live demo:** [ernawatiiii.github.io/fsldk-nusra-web](https://ernawatiiii.github.io/fsldk-nusra-web/)

---

## Latar Belakang

Website ini dibangun untuk menggantikan situs lama organisasi (WordPress, sudah lama tidak diperbarui) dengan platform yang:
- Lebih cepat dan ringan (static site, tanpa CMS berat)
- Bisa dikelola konten-nya secara mandiri oleh pengurus **tanpa perlu sentuh kode**
- Gratis untuk dihosting dan dikelola jangka panjang

## Fitur Utama

### Untuk Pengunjung
- **Beranda** — profil singkat forum dengan statistik (jumlah LDK, komisi, badan semi otonom)
- **Berita** — pengumuman & artikel (mendukung tulisan pendek maupun artikel panjang dengan gambar pendukung), lengkap dengan indikator "ada info baru"
- **Tentang Kami** — visi, misi, tujuan, dan struktur organisasi yang interaktif:
  - Setiap **Komisi (A–D)** dan **Badan Semi Otonom** bisa diklik untuk menampilkan daftar anggotanya
  - Daftar **16 LDK anggota** lengkap dengan logo dan tautan langsung ke akun Instagram masing-masing
- **Program Kerja** — enam program unggulan forum
- **Galeri** — dokumentasi kegiatan (dikelola langsung oleh admin)
- **Kontak** — email, Instagram (umum & kemuslimahan), Facebook, dan formulir pesan

### Untuk Admin (Dashboard Tersembunyi)
Diakses lewat tombol mengambang "Mode Admin", dilindungi autentikasi:
- Kelola **Berita** (tambah/hapus, dengan atau tanpa gambar)
- Kelola **Galeri** (upload foto langsung dari perangkat)
- Kelola **Pengurus Harian** (dewan pembina, pengurus inti)
- Kelola **Anggota Komisi & Badan Semi Otonom**

Semua perubahan tersimpan permanen dan langsung tampil di website tanpa proses deploy ulang.

## Tech Stack

| Layer | Teknologi |
|---|---|
| Frontend | HTML, CSS (custom, tanpa framework), Vanilla JavaScript |
| Backend & Database | [Supabase](https://supabase.com) (PostgreSQL, Row Level Security, Auth, Storage) |
| Hosting | GitHub Pages |
| SEO | Meta tags terstruktur, terdaftar & terverifikasi di Google Search Console |

## Arsitektur Singkat

Website ini adalah **single HTML file** yang berkomunikasi langsung dengan Supabase lewat REST API di sisi client (browser), tanpa server backend terpisah:

```
Pengunjung/Admin  →  index.html (GitHub Pages)  →  Supabase (Database + Auth + Storage)
```

- **Keamanan data**: menggunakan Row Level Security (RLS) di PostgreSQL — semua orang bisa membaca data publik, tapi hanya admin yang terautentikasi yang bisa menambah/mengubah/menghapus data.
- **Upload gambar** (galeri & berita) disimpan di Supabase Storage dan diakses lewat public URL.
- **Tanpa build step** — perubahan kode langsung di-deploy begitu file di-push ke branch `main`.

## Struktur Data (Database)

| Tabel | Fungsi |
|---|---|
| `news` | Berita & pengumuman (judul, isi, gambar opsional) |
| `gallery` | Foto dokumentasi kegiatan |
| `pengurus` | Data pengurus harian |
| `komisi_anggota` | Anggota tiap komisi & badan semi otonom |

## Menjalankan Secara Lokal

Karena tidak ada proses build, cukup buka file `index.html` langsung di browser. Untuk fungsi dashboard admin (yang terhubung ke Supabase), pastikan koneksi internet aktif.

## Kontributor

Dikembangkan untuk **FSLDK Nusa Tenggara** sebagai bagian dari digitalisasi informasi organisasi dakwah kampus se-Nusa Tenggara.

---

*"Terwujudnya sinergi antar Lembaga Dakwah Kampus se-Indonesia menuju Indonesia madani."*
