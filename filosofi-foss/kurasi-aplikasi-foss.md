# Daftar Perangkat Lunak Bebas (FOSS) Pengganti Aplikasi Harian

> **Kategori:** Filosofi & Kurasi FOSS  
> **Status:** Terbit | **Pembaruan Terakhir:** November 2026  
> **Penulis:** Satrijo Oeiboeo (`@oeiboeo`)

---

## Ringkasan
Menggunakan perangkat lunak bebas dan sumber terbuka (*Free and Open-Source Software* / FOSS) memberikan kendali penuh atas privasi, keamanan, serta kebebasan dari ketergantungan pada satu vendor tertentu. Catatan ini memuat daftar kurasi aplikasi FOSS ringan dan andal untuk menggantikan perangkat lunak berpemilik (*proprietary*) dalam aktivitas komputasi harian di lingkungan **Debian GNU/Linux**.

---

## 1. Perbandingan & Alternatif Aplikasi Harian

| Kategori Tugas | Aplikasi Berpemilik Umum | Alternatif FOSS Rekomendasi | Lisensi Utama |
| :--- | :--- | :--- | :--- |
| **Peramban Web** | Google Chrome / Edge | **LibreWolf** atau **Mozilla Firefox** | MPL 2.0 |
| **Perkantoran** | Microsoft Office | **LibreOffice** | MPL 2.0 |
| **Catatan & Markdown** | Notion / Obsidian | **Logseq** atau **Joplin** | AGPL / MIT |
| **Penyunting Gambar** | Adobe Photoshop | **GIMP** atau **Krita** | GPLv3 |
| **Pemutar Media** | Windows Media Player | **MPV** atau **VLC Media Player** | GPLv2+ |
| **Pengelola Kata Sandi** | 1Password / LastPass | **KeePassXC** atau **Bitwarden** | GPLv3 / AGPL |

---

## 2. Perangkat Lunak Berbasis Terminal (CLI)
Untuk alur kerja yang lebih cepat dan hemat sumber daya di terminal Linux, beberapa utilitas modern berbasis teks berikut sangat layak dipasang.

* **btop / htop:** Pemantau penggunaan prosesor, memori, dan proses sistem secara interaktif.
* **ripgrep (`rg`):** Pencari teks di dalam file dengan kecepatan jauh lebih tinggi dibanding `grep` standar.
* **fzf:** Pencari berkas dan riwayat perintah terminal secara instan (*fuzzy finder*).
* **tmux:** Pengelola sesi terminal ganda dalam satu jendela kerja.

---

## 3. Prinsip Dasar Memilih Perangkat Lunak Bebas
Sebelum memasang sebuah aplikasi baru, ada tiga kriteria utama yang selalu dijadikan acuan:

1. **Transparansi Kode Sumber:** Kode dapat diaudit secara terbuka oleh komunitas untuk memastikan tidak ada pelacakan tersembunyi.
2. **Format Berkas Terbuka:** Data disimpan dalam format standar (seperti `.md`, `.txt`, `.odt`, atau `.json`) sehingga tetap mudah dibaca puluhan tahun mendatang.
3. **Dukungan Komunitas Aktif:** Memiliki dokumentasi yang jelas dan pembaruan keamanan yang terawat.

---

## Catatan Penutup
* Seluruh aplikasi di atas dapat dipasang langsung melalui repositori resmi Debian (`apt`) maupun melalui **Flathub** untuk versi terbaru.
* Dokumentasi ini merupakan bagian dari arsip pribadi di [*Jejak Pikiran & Catatan Digital*](https://github.com/oeiboeo).
