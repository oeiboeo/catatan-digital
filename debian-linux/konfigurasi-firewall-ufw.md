# Konfigurasi Dasar Firewall Menggunakan UFW di Debian

> **Kategori:** Sistem & Administrasi Linux  
> **Status:** Terbit | **Pembaruan Terakhir:** November 2026  
> **Penulis:** Satrijo Oeiboeo (`@oeiboeo`)

---

## Ringkasan
**UFW (*Uncomplicated Firewall*)** adalah antarmuka baris perintah yang dirancang untuk mempermudah pengelolaan aturan *firewall* `iptables`/`nftables` pada sistem operasi **Debian GNU/Linux**. Catatan ini merangkum langkah pemasangan, penerapan aturan dasar pemblokiran koneksi masuk, serta cara membuka akses layanan tertentu secara aman.

---

## 1. Pemasangan UFW
Pada instalasi standar Debian, paket `ufw` terkadang belum terpasang secara bawaan. Pasang terlebih dahulu melalui repositori resmi.

```bash
# Memperbarui daftar paket dan memasang UFW
sudo apt update
sudo apt install ufw -y
```

---

## 2. Mengatur Kebijakan Dasar (*Default Policies*)
Prinsip keamanan jaringan yang disarankan adalah menolak seluruh koneksi masuk dari luar secara otomatis, namun mengizinkan seluruh koneksi keluar dari komputer lokal.

```bash
# Menolak semua koneksi masuk secara bawaan
sudo ufw default deny incoming

# Mengizinkan semua koneksi keluar secara bawaan
sudo ufw default allow outgoing
```

---

## 3. Membuka Akses Layanan Penting (Sebelum Mengaktifkan UFW)
Jika Anda mengelola sistem dari jarak jauh menggunakan **SSH**, wajib membuka akses port SSH terlebih dahulu sebelum mengaktifkan *firewall* agar koneksi tidak terputus.

```bash
# Mengizinkan koneksi SSH (port 22)
sudo ufw allow ssh

# Contoh membuka port layanan web (opsional jika menjalankan web server)
sudo ufw allow http
sudo ufw allow https
```

---

## 4. Mengaktifkan & Memeriksa Status Firewall
Setelah aturan dasar dan pengecualian layanan diterapkan, aktifkan UFW dan periksa daftar aturan yang berjalan.

```bash
# Mengaktifkan firewall UFW (akan berjalan otomatis saat sistem menyala)
sudo ufw enable

# Memeriksa status dan daftar aturan aktif beserta nomor urutnya
sudo ufw status verbose
```

---

## 5. Menghapus Aturan yang Tidak Diperlukan
Jika ingin mencabut izin suatu layanan atau port tertentu, gunakan nomor aturan yang tampil pada status UFW.

```bash
# Menampilkan daftar aturan dengan nomor indeks
sudo ufw status numbered

# Menghapus aturan berdasarkan nomor urut (contoh nomor 2)
sudo ufw delete 2
```

---

## Catatan Keamanan
* **Selalu izinkan SSH sebelum menjalankan `sudo ufw enable`** apabila Anda bekerja di atas server jarak jauh (*VPS*).
* Hindari membuka port layanan ke publik jika aplikasi hanya diakses secara lokal di dalam jaringan rumah atau komputer pribadi.
* Dokumentasi ini merupakan bagian dari arsip pribadi di [*Jejak Pikiran & Catatan Digital*](https://github.com/oeiboeo).
