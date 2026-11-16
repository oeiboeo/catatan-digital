# Pembersihan Sistem & Pembaruan Paket Otomatis Satu Perintah

> **Kategori:** Skrip & Otomatisasi Terminal  
> **Status:** Terbit | **Pembaruan Terakhir:** November 2026  
> **Penulis:** Satrijo Oeiboeo (`@oeiboeo`)

---

## Ringkasan
Merawat sistem operasi **Debian GNU/Linux** secara rutin biasanya memerlukan empat perintah terpisah: memperbarui daftar paket, meningkatkan versi paket, menghapus dependensi usang, dan membersihkan arsip tembolok (*cache*). Catatan ini menyatukan keempat proses tersebut ke dalam satu skrip Bash sederhana agar perawatan sistem cukup dilakukan dengan satu perintah singkat.

---

## 1. Kode Skrip Perawatan (`rawat-sistem.sh`)
Buat file skrip baru di direktori lokal (misalnya melalui perintah `nano ~/rawat-sistem.sh`) lalu salin kode berikut.

```bash
#!/usr/bin/env bash

# Menghentikan skrip jika terjadi kesalahan
set -e

echo "=========================================="
echo "  Memulai Perawatan Sistem Debian Linux"
echo "=========================================="

echo "[1/4] Memperbarui indeks repositori..."
sudo apt update

echo "[2/4] Meningkatkan versi paket terpasang..."
sudo apt upgrade -y

echo "[3/4] Menghapus paket dependensi yang tidak terpakai..."
sudo apt autoremove -y

echo "[4/4] Membersihkan sisa cache arsip paket..."
sudo apt clean

echo "=========================================="
echo "  Perawatan sistem selesai dengan bersih!"
echo "=========================================="
```

---

## 2. Cara Pemasangan & Penggunaan Global
Agar skrip ini dapat dipanggil dari direktori mana saja di terminal cukup dengan mengetikkan nama perintahnya (tanpa perlu menulis `./` atau alamat lengkap folder), pindahkan skrip ke dalam direktori `/usr/local/bin/`.

```bash
# Memberikan izin eksekusi pada skrip
chmod +x ~/rawat-sistem.sh

# Memindahkan skrip ke direktori perintah global sistem
sudo mv ~/rawat-sistem.sh /usr/local/bin/rawat-sistem
```

Setelah dipindahkan, Anda cukup membuka terminal kapan saja dan mengetikkan perintah berikut:

```bash
rawat-sistem
```

---

## 3. Alternatif Tanpa File Skrip (Menggunakan Alias)
Jika tidak ingin membuat file terpisah di `/usr/local/bin/`, Anda cukup menambahkan baris `alias` berikut ke bagian paling bawah file `~/.bashrc`.

```bash
alias rawat='sudo apt update && sudo apt upgrade -y && sudo apt autoremove -y && sudo apt clean'
```

Simpan file `~/.bashrc`, muat ulang konfigurasi dengan perintah `source ~/.bashrc`, lalu ketik `rawat` di terminal untuk menjalankannya.

---

## Catatan Keamanan
* Flag `-y` pada perintah `apt upgrade` dan `apt autoremove` akan menyetujui proses pemasangan maupun penghapusan secara otomatis tanpa meminta konfirmasi ulang.
* Disarankan tetap memeriksa informasi pembaruan kernel atau paket kritis secara berkala sebelum menjalankan skrip pada komputer produksi (*server*).
* Dokumentasi ini merupakan bagian dari arsip pribadi di [*Jejak Pikiran & Catatan Digital*](https://github.com/oeiboeo).
