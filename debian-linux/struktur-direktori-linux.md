# Memahami Struktur Direktori Sistem Berkas Linux (FHS)

> **Kategori:** Sistem & Administrasi Linux  
> **Status:** Terbit | **Pembaruan Terakhir:** November 2026  
> **Penulis:** Satrijo Oeiboeo (`@oeiboeo`)

---

## Ringkasan
Berbeda dengan sistem operasi Windows yang membagi penyimpanan berdasarkan huruf partisi (`C:\`, `D:\`), sistem operasi **Debian GNU/Linux** menyatukan seluruh berkas dan perangkat keras dalam satu pohon direktori tunggal yang berawal dari **root (`/`)**. Susunan ini mengikuti standar **FHS (*Filesystem Hierarchy Standard*)** agar lokasi file konfigurasi, aplikasi, dan data pengguna selalu konsisten di berbagai distribusi Linux.

---

## 1. Peta Hierarki Direktori Utama

| Direktori | Nama & Kepanjangan | Fungsi Utama dalam Sistem |
| :--- | :--- | :--- |
| **`/`** | *Root Directory* | Puncak tertinggi dari seluruh struktur sistem berkas Linux. |
| **`/bin` & `/usr/bin`** | *User Binaries* | Menyimpan program dan perintah dasar pengguna seperti `ls`, `cp`, `cat`, dan `nano`. |
| **`/sbin` & `/usr/sbin`** | *System Binaries* | Menyimpan perintah administrasi sistem yang umumnya dijalankan dengan hak akses `sudo` (contoh: `ufw`, `reboot`). |
| **`/etc`** | *Editable Text Configuration* | Pusat penyimpanan seluruh file konfigurasi sistem dan aplikasi (contoh: `/etc/fstab`, `/etc/ssh/`). |
| **`/home`** | *Home Directories* | Ruang pribadi tiap pengguna untuk menyimpan dokumen, unduhan, dan pengaturan lokal (*dotfiles*). |
| **`/root`** | *Root User Home* | Direktori pribadi khusus untuk akun administrator tertinggi (`root`), terpisah dari `/home`. |
| **`/var`** | *Variable Files* | Menyimpan data yang ukurannya terus berubah saat sistem berjalan, seperti catatan aktivitas sistem (`/var/log`) dan *cache* paket. |
| **`/tmp`** | *Temporary Files* | Tempat penyimpanan berkas sementara yang otomatis dibersihkan saat sistem dimatikan atau dinyalakan ulang. |
| **`/opt`** | *Optional Software* | Lokasi pemasangan perangkat lunak tambahan dari pihak ketiga yang tidak berasal dari repositori bawaan. |
| **`/dev`** | *Device Files* | Berkas khusus yang merepresentasikan perangkat keras yang terhubung (seperti hard disk `/dev/sda` atau USB). |
| **`/mnt` & `/media`** | *Mount Points* | Titik kait sementara untuk mengakses partisi tambahan, diska lepas (*flashdisk*), atau drive eksternal. |

---

## 2. Perintah Navigasi & Pemeriksaan Direktori
Untuk menjelajahi struktur direktori di atas melalui terminal Debian, gunakan beberapa perintah dasar berikut:

```bash
# Menampilkan lokasi direktori kerja saat ini
pwd

# Melihat isi direktori beserta ukuran berkas yang mudah dibaca manusia
ls -lh /etc

# Memeriksa penggunaan ruang penyimpanan pada tiap partisi yang terpasang
df -h

# Mengukur total ukuran sebuah direktori (contoh: direktori /var/log)
sudo du -sh /var/log
```

---

## 3. Kebiasaan Baik Mengelola Berkas
* **Hindari menyunting file di `/usr` secara manual:** Perubahan manual di dalam `/usr` dapat tertimpa saat sistem melakukan pembaruan paket (`apt upgrade`). Gunakan direktori `/etc` untuk konfigurasi sistem atau `/usr/local/bin` untuk skrip buatan sendiri.
* **Cadangkan dua direktori paling vital:** Jika berencana memasang ulang sistem operasi, cukup amankan isi direktori **`/home`** (data & konfigurasi pengguna) serta file konfigurasi khusus di **`/etc`**.
* Dokumentasi ini merupakan bagian dari arsip pribadi di [*Jejak Pikiran & Catatan Digital*](https://github.com/oeiboeo).
