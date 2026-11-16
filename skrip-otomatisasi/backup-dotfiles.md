# Otomatisasi Pencadangan Dotfiles ke GitHub

> **Kategori:** Skrip & Otomatisasi Terminal  
> **Status:** Terbit | **Pembaruan Terakhir:** November 2026  
> **Penulis:** Satrijo Oeiboeo (`@oeiboeo`)

---

## Ringkasan
File konfigurasi tersembunyi (*dotfiles*) seperti `.bashrc`, `.vimrc`, atau konfigurasi terminal menyimpan pengaturan lingkungan kerja Linux yang telah disesuaikan secara pribadi. Catatan ini memuat skrip Bash ringan untuk menyalin dan mencadangkan file-file penting tersebut ke repositori GitHub secara otomatis.

---

## 1. Persiapan Direktori Cadangan
Siapkan sebuah folder khusus di komputer lokal yang sudah terhubung dengan repositori Git Anda.

```bash
# Membuat direktori penyimpanan dotfiles
mkdir -p ~/dotfiles-backup
cd ~/dotfiles-backup

# Inisiasi repositori Git (lewati jika sudah di-clone dari GitHub)
git init
```

---

## 2. Kode Skrip Otomatisasi (`backup-dotfiles.sh`)
Buat file skrip baru dengan perintah `nano ~/backup-dotfiles.sh` lalu masukkan kode berikut.

```bash
#!/usr/bin/env bash

# Direktori tujuan cadangan
BACKUP_DIR="\$HOME/dotfiles-backup"

# Daftar file konfigurasi yang akan dicadangkan
FILES=(".bashrc" ".profile" ".vimrc" ".gitconfig")

echo "Memulai proses pencadangan dotfiles..."

# Menyalin setiap file jika tersedia di direktori Home
for file in "\${FILES[@]}"; do
    if [ -f "HOME/file" ]; then
        cp "\$HOME/file" "BACKUP_DIR/"
        echo "[OK] Berhasil menyalin \$file"
    else
        echo "[LEWATI] File \$file tidak ditemukan"
    fi
done

# Mengirim perubahan ke repositori GitHub
cd "\$BACKUP_DIR" || exit
git add .
git commit -m "Pembaruan otomatis dotfiles: \$(date +'%Y-%m-%d %H:%M')"
git push origin main

echo "Pencadangan selesai!"
```

---

## 3. Cara Menjalankan Skrip
Berikan izin eksekusi pada skrip tersebut agar dapat dijalankan langsung dari terminal Debian.

```bash
# Memberikan hak akses eksekusi
chmod +x ~/backup-dotfiles.sh

# Menjalankan skrip pencadangan
~/backup-dotfiles.sh
```

---

## Catatan Keamanan
* **Jangan pernah mencadangkan kunci privat** seperti isi folder `~/.ssh/` atau file `.env` yang berisi token rahasia ke repositori publik.
* Pastikan repositori tujuan pencadangan diatur menjadi **Private** jika konfigurasi Anda memuat informasi sensitif atau alamat server pribadi.
* Dokumentasi ini merupakan bagian dari arsip pribadi di [*Jejak Pikiran & Catatan Digital*](https://github.com).
