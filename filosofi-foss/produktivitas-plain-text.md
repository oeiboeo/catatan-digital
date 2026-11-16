# Alat Produktivitas Berbasis Teks (Plain Text) untuk Jangka Panjang

> **Kategori:** Filosofi & Kurasi FOSS  
> **Status:** Terbit | **Pembaruan Terakhir:** November 2026  
> **Penulis:** Satrijo Oeiboeo (`@oeiboeo`)

---

## Ringkasan
Aplikasi pencatat modern sering kali menyimpan tulisan pengguna di dalam format tertutup (*proprietary*) atau server awan (*cloud*) yang sewaktu-waktu bisa tutup atau berbayar. Menyimpan catatan, jurnal, dan daftar tugas dalam format **teks biasa (*plain text*)** seperti Markdown (`.md`) atau `.txt` memastikan seluruh arsip pikiran tetap ringan, mudah dicari, dan dapat dibaca lintas generasi perangkat lunak.

---

## 1. Alasan Memilih Format Teks Biasa (*Plain Text*)
* **Tahan Uji Waktu (*Future-Proof*):** Berkas teks yang ditulis tiga puluh tahun lalu masih bisa dibuka dengan sempurna hari ini di sistem operasi apa pun tanpa perlu konversi format.
* **Sangat Ringan & Cepat:** Ribuan catatan dalam format Markdown hanya memakan ruang penyimpanan beberapa megabita saja dan dapat dicari dalam hitungan milidetik menggunakan perintah terminal seperti `grep` atau `ripgrep`.
* **Ramah Sistem Kontrol Versi (Git):** Perubahan setiap baris kalimat dapat dilacak riwayatnya secara presisi menggunakan **Git** dan dicadangkan dengan mudah ke GitHub.

---

## 2. Ekosistem Perangkat Lunak Pendukung
Untuk mengelola arsip teks secara nyaman di lingkungan **Debian GNU/Linux**, beberapa alat berikut saling melengkapi satu sama lain:

| Fungsi Kerja | Perangkat Lunak Rekomendasi | Keterangan Singkat |
| :--- | :--- | :--- |
| **Penyunting Teks Terminal** | **Vim / Neovim** atau **Nano** | Cepat, berjalan langsung di terminal tanpa membebani memori. |
| **Penyunting Markdown Visual** | **Joplin** atau **Zettlr** | Mendukung pratinjau langsung, tautan antarcatatan, dan manajemen tag. |
| **Pengelola Daftar Tugas** | **Todo.txt** | Format daftar tugas berbasis satu file teks sederhana yang didukung banyak aplikasi lintas platform. |
| **Konversi Dokumen** | **Pandoc** | Mengubah file Markdown menjadi PDF, HTML, EPUB, atau dokumen perkantoran dalam satu perintah. |

---

## 3. Prinsip Menata Arsip Catatan Pribadi
1. **Gunakan penamaan berkas yang deskriptif:** Gunakan huruf kecil dan tanda hubung (contoh: `konfigurasi-firewall-ufw.md`) agar mudah dibaca baik oleh manusia maupun skrip terminal.
2. **Hindari struktur folder yang terlalu dalam:** Cukup kelompokkan catatan ke dalam 3 hingga 5 kategori besar agar tidak membingungkan saat mencari berkas.
3. **Tulis dengan bahasa sendiri:** Catatan terbaik bukanlah salinan dokumentasi resmi, melainkan ringkasan pemahaman setelah mempraktikkannya langsung.

---

## Catatan Penutup
* Seluruh isi repositori **Catatan Digital** ini dibangun sepenuhnya di atas prinsip teks biasa dan Markdown.
* Dokumentasi ini merupakan bagian dari arsip pribadi di [*Jejak Pikiran & Catatan Digital*](https://github.com/oeiboeo).
