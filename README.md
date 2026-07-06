<div align="center">

# 🏘️ RWKami

**Portal Digital Warga — Laporan, Pengaduan, Saran, dan Kalkulator Pajak & Zakat UMKM**

Dibangun sebagai proyek UAS PPKn — mengangkat tema partisipasi warga negara, gotong royong, dan kesadaran bernegara dalam bentuk aplikasi web yang benar-benar bisa dipakai masyarakat.

[![Status](https://img.shields.io/badge/status-beta-f59e0b?style=flat-square)](#-status-proyek)
[![License](https://img.shields.io/badge/license-MIT-4f46e5?style=flat-square)](#-lisensi)
[![No Backend](https://img.shields.io/badge/backend-tidak%20perlu-059669?style=flat-square)](#-arsitektur)
[![Made with](https://img.shields.io/badge/dibuat%20dengan-HTML%20%7C%20CSS%20%7C%20JavaScript-0f172a?style=flat-square)](#-teknologi)

</div>

---

## 📖 Tentang Proyek

**RWKami** adalah portal digital untuk lingkungan Rukun Warga (RW) yang memudahkan warga menyampaikan **laporan**, **pengaduan**, dan **saran**, sekaligus dilengkapi **Kalkulator Pajak & Zakat UMKM** sebagai alat bantu edukatif bagi warga pelaku usaha kecil.

Proyek ini sengaja dibangun **tanpa server dan tanpa database** — seluruh data disimpan di `localStorage` browser — sehingga bisa langsung dibuka atau dihosting di mana saja tanpa instalasi PHP/MySQL, sambil tetap merepresentasikan alur kerja aplikasi warga yang nyata.

> ⚠️ **Status: Beta / Uji Coba.** Belum digunakan secara resmi oleh RW mana pun. Berminat menggunakan atau mengustomisasi untuk lingkungan Anda? Hubungi **i.2510393@unida.ac.id**.

---

## ✨ Fitur Utama

### 🧾 Portal Warga
- **Laporan** — infrastruktur rusak, fasilitas umum bermasalah, dll.
- **Pengaduan** — ketertiban umum, sampah liar, kebisingan, keamanan.
- **Saran** — usulan membangun untuk lingkungan RW.
- **Login & Registrasi** — role `warga` dan `admin` (pengurus RW).
- **Dashboard** — filter kategori & status, ubah status (admin), edit/hapus laporan milik sendiri (warga).

### 🧮 Kalkulator Pajak & Zakat UMKM
- **PPh Final UMKM (0,5%)** — dengan fasilitas bebas pajak omzet kumulatif Rp500 juta/tahun.
- **Zakat Penghasilan/Profesi** — otomatis membandingkan dengan nisab bulanan.
- **Zakat Maal** — dihitung dari harta bersih setelah dikurangi hutang.
- **Data pasar real-time** — kurs USD & harga emas 24K, dengan tombol "Gunakan harga ini" untuk mengisi otomatis.
- **Dasar hukum kewarganegaraan** — kaitan pajak & zakat dengan Pasal 23A & 29 UUD 1945 serta Pancasila sila ke-3 dan ke-5.
- **Cetak/simpan hasil sebagai PDF** langsung dari browser.

### 🎨 Kustomisasi
- Bisa disesuaikan sepenuhnya (nama, logo, warna tema, kategori laporan, fitur tambahan) untuk kebutuhan RW/RT masing-masing.

---

## 🏗️ Arsitektur

Proyek ini adalah **Single Page Application (SPA)** murni dalam satu file HTML — tanpa framework, tanpa build tool, tanpa backend.

| Aspek | Implementasi |
|---|---|
| Routing | Hash-based router (`#/dashboard`, `#/kalkulator?tab=...`) |
| Penyimpanan data | `localStorage` browser (pengganti database) |
| Autentikasi | Sesi sederhana berbasis `localStorage`, cocok untuk demo/skala kecil |
| Styling | CSS murni dengan custom properties (design tokens), tanpa framework CSS |
| Data eksternal | `open.er-api.com` (kurs) & `api.gold-api.com` (harga emas) — hanya untuk kalkulator |

```
Browser Pengguna
   └── rwkami.html (routing + UI + logic)
         └── localStorage (users, tickets, session)
         └── fetch() → API kurs & harga emas (opsional, hanya di halaman kalkulator)
```

Karena tidak ada server, data **tidak sinkron antar perangkat/browser** — cukup untuk keperluan demo, uji coba, dan skala RW kecil. Untuk penggunaan resmi berskala lebih besar, arsitektur ini dapat dikembangkan ke backend + database sungguhan (lihat [Roadmap](#-roadmap)).

---

## 📁 Struktur Repositori

```
rwkami/
├── index.html          # Aplikasi utama (portal + kalkulator), single-file
├── README.md           # Dokumentasi proyek (file ini)
├── LICENSE             # Lisensi proyek
└── docs/
    └── screenshots/    # Tangkapan layar untuk dokumentasi (opsional)
```

> Saat ini seluruh aplikasi berada dalam satu berkas `index.html` agar mudah dijalankan tanpa proses build. Struktur folder di atas adalah rekomendasi minimal jika proyek diunggah ke GitHub.

---

## 🚀 Cara Menjalankan

Tidak perlu instalasi apa pun.

1. **Unduh/clone** repositori ini.
   ```bash
   git clone https://github.com/SuTYAA234/RWKAMI.git
   cd rwkami
   ```
2. **Buka `index.html`** langsung di browser (double click), **atau** jalankan local server sederhana:
   ```bash
   npx serve .
   # atau
   python3 -m http.server 8000
   ```
3. Selesai — aplikasi langsung berjalan.

### 🔑 Akun Demo

| Peran | Username | Password |
|---|---|---|
| Warga | `warga` | `warga123` |
| Admin (Pengurus RW) | `admin` | `admin123` |

Atau daftar akun baru sendiri melalui halaman registrasi.

---

## 🌐 Deploy ke Hosting Statis

Karena tidak membutuhkan backend, RWKami bisa langsung dihosting gratis di:

- **GitHub Pages** — aktifkan di `Settings → Pages → Deploy from branch`.
- **Netlify** / **Vercel** — drag-and-drop folder atau hubungkan repo.
- **Cloudflare Pages**.

---

## 🛠️ Teknologi

- HTML5, CSS3 (custom properties, tanpa framework)
- JavaScript (Vanilla, ES6+)
- [Boxicons](https://boxicons.com/) — ikon
- Google Fonts: **Outfit**, **Fraunces**, **Inter**, **JetBrains Mono**
- API publik: [open.er-api.com](https://www.exchangerate-api.com/) (kurs), [gold-api.com](https://gold-api.com/) (harga emas)

---

## 🗺️ Roadmap

- [ ] Migrasi penyimpanan dari `localStorage` ke backend + database sungguhan (opsional, untuk penggunaan multi-perangkat/resmi)
- [ ] Upload foto bukti pada laporan/pengaduan
- [ ] Notifikasi email/WhatsApp saat status laporan berubah
- [ ] Modul kas RT/RW
- [ ] Modul agenda & pengumuman warga
- [ ] Multi-RW dalam satu instance (multi-tenant)

---

## 🤝 Kontribusi & Kustomisasi

Proyek ini terbuka untuk pengembangan lebih lanjut. Jika RW/RT Anda tertarik menggunakan atau mengustomisasi RWKami sesuai kebutuhan lingkungan masing-masing (nama, logo, kategori laporan, fitur tambahan, hosting dengan domain sendiri), silakan hubungi:

📧 **i.2510393@unida.ac.id**

Pull request dan masukan juga sangat diterima melalui tab **Issues** dan **Pull Requests** di repositori ini.

---

## 📄 Lisensi

Proyek ini dirilis di bawah [Lisensi MIT](LICENSE) — bebas digunakan, dimodifikasi, dan didistribusikan dengan tetap menyertakan atribusi.

---

## 🎓 Konteks Akademik

Dikembangkan sebagai proyek Ujian Akhir Semester (UAS) mata kuliah **Pendidikan Pancasila dan Kewarganegaraan (PPKn)**, dengan fokus pada perwujudan nilai partisipasi warga negara, gotong royong, dan kesadaran hukum (perpajakan & zakat) melalui teknologi yang aplikatif bagi masyarakat.

<div align="center">

Dibuat dengan 🧡 untuk lingkungan yang lebih tertib, transparan, dan sejahtera.

</div>
