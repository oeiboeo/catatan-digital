# Menjadwalkan Tugas Rutin di Linux dengan Cron & Systemd Timers

> **Kategori:** Skrip & Otomatisasi Terminal  
> **Status:** Terbit | **Pembaruan Terakhir:** November 2026  
> **Penulis:** Satrijo Oeiboeo (`@oeiboeo`)

---

## Ringkasan
Menjalankan skrip pencadangan (*backup*) atau pembersihan sistem secara manual setiap hari sering kali mudah terlupakan. Pada sistem operasi **Debian GNU/Linux**, tugas-tugas berulang tersebut dapat diotomatiskan menggunakan utilitas klasik **Cron** maupun fitur modern **Systemd Timers** agar berjalan tepat waktu di latar belakang.

---

## 1. Memahami Format Penjadwalan Cron (`crontab`)
Setiap baris jadwal pada *crontab* terdiri dari lima kolom waktu yang diikuti oleh perintah atau lokasi skrip yang akan dijalankan.

```text
┌───────────── menit (0 - 59)
│ ┌───────────── jam (0 - 23)
│ │ ┌───────────── tanggal dalam bulan (1 - 31)
│ │ │ ┌───────────── bulan (1 - 12)
│ │ │ │ ┌───────────── hari dalam minggu (0 - 6, Minggu = 0 atau 7)
│ │ │ │ │
* * * * * /jalur/lengkap/ke/skrip.sh
```

---

## 2. Contoh Penerapan Jadwal Harian & Mingguan
Untuk mulai mengatur jadwal milik pengguna saat ini, buka editor jadwal melalui terminal.

```bash
# Membuka konfigurasi crontab pengguna aktif
crontab -e
```

Tambahkan salah satu contoh baris jadwal di bawah ini ke bagian paling bawah file:

```bash
# Menjalankan pencadangan dotfiles setiap hari pada pukul 20.00 (8 malam)
0 20 * * * /home/oeiboeo/backup-dotfiles.sh

# Menjalankan pembersihan dan pembaruan sistem setiap hari Minggu pukul 03.00 pagi
0 3 * * 0 /usr/local/bin/rawat-sistem >> /home/oeiboeo/rawat.log 2>&1
```

Untuk memeriksa daftar jadwal yang sudah aktif, jalankan perintah:

```bash
crontab -l
```

---

## 3. Alternatif Modern: Systemd Timers
Pada distribusi Debian modern, **Systemd Timers** menawarkan pencatatan log yang lebih rapi melalui `journalctl` dan tetap menjalankan tugas yang terlewat jika komputer sedang mati saat jadwal tiba (`Persistent=true`).

### Langkah A: Buat File Service (`/etc/systemd/system/backup-dotfiles.service`)
```ini
[Unit]
Description=Layanan Pencadangan Dotfiles Otomatis

[Service]
Type=oneshot
User=oeiboeo
ExecStart=/home/oeiboeo/backup-dotfiles.sh
```

### Langkah B: Buat File Timer (`/etc/systemd/system/backup-dotfiles.timer`)
```ini
[Unit]
Description=Jadwal Harian Pencadangan Dotfiles

[Timer]
OnCalendar=daily
Persistent=true

[Install]
WantedBy=timers.target
```

### Langkah C: Aktifkan Timer
```bash
# Memuat ulang konfigurasi systemd dan mengaktifkan timer
sudo systemctl daemon-reload
sudo systemctl enable --now backup-dotfiles.timer

# Memeriksa daftar timer yang aktif beserta waktu eksekusi berikutnya
systemctl list-timers --all
```

---

## Catatan Praktis
* **Selalu gunakan jalur lengkap (*absolute path*):** Cron berjalan dengan variabel lingkungan yang terbatas, sehingga perintah atau lokasi skrip wajib ditulis lengkap (contoh: `/home/namauser/skrip.sh`, bukan `~/skrip.sh`).
* **Catat keluaran ke file log:** Menambahkan `>> /jalur/file.log 2>&1` di akhir perintah Cron sangat membantu untuk melacak penyebab kegagalan apabila skrip tidak berjalan sesuai harapan.
* Dokumentasi ini merupakan bagian dari arsip pribadi di [*Jejak Pikiran & Catatan Digital*](https://github.com/oeiboeo).
