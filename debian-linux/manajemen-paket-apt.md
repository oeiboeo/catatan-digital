# Manajemen Paket & Optimasi Dasar Debian GNU/Linux

> **Kategori:** Sistem & Administrasi Linux  
> **Status:** Terbit | **Pembaruan Terakhir:** November 2026  
> **Penulis:** Satrijo Oeiboeo (`@oeiboeo`)

---

## Ringkasan
Catatan ini merangkum perintah dasar pengelolaan paket perangkat lunak menggunakan `apt` pada sistem operasi **Debian GNU/Linux**, serta langkah pembersihan rutin untuk menjaga ruang penyimpanan tetap ringan.

---

## 1. Pembaruan & Peningkatan Sistem
Sebelum memasang perangkat lunak baru, pastikan daftar repositori lokal telah diperbarui agar mendapatkan versi paket paling mutakhir.

```bash
# Memperbarui indeks daftar paket dari repositori
sudo apt update

# Meningkatkan versi paket yang sudah terpasang
sudo apt upgrade -y
```

---

## 2. Manajemen Pemasangan & Penghapusan Paket
Berikut adalah perintah harian yang paling sering digunakan di terminal:

| Perintah | Fungsi Utama |
| :--- | :--- |
| `sudo apt install <nama-paket>` | Memasang aplikasi atau pustaka baru. |
| `sudo apt remove <nama-paket>` | Menghapus aplikasi tanpa menghapus file konfigurasinya. |
| `sudo apt purge <nama-paket>` | Menghapus aplikasi beserta seluruh file konfigurasinya secara bersih. |
| `apt search <kata-kunci>` | Mencari nama paket yang tersedia di dalam repositori. |

---

## 3. Pembersihan Sistem Rutin
Setelah menghapus atau memperbarui banyak paket, sisa dependensi dan tembolok (*cache*) sering kali menumpuk di penyimpanan.

```bash
# Menghapus paket dependensi yang sudah tidak diperlukan lagi
sudo apt autoremove -y

# Membersihkan arsip paket (.deb) yang tersimpan di cache lokal
sudo apt clean
```

---

## Catatan Tambahan
* Selalu periksa daftar paket yang akan dihapus sebelum menekan tombol **Y** saat menjalankan perintah `autoremove`.
* Dokumentasi ini merupakan bagian dari arsip pribadi di [*Jejak Pikiran & Catatan Digital*](https://github.com/oeiboeo).
