# Mengenal Jenis-Jenis Lisensi Perangkat Lunak Bebas (GPL, MIT, Apache)

> **Kategori:** Filosofi & Kurasi FOSS  
> **Status:** Terbit | **Pembaruan Terakhir:** November 2026  
> **Penulis:** Satrijo Oeiboeo (`@oeiboeo`)

---

## Ringkasan
Kode sumber yang tersedia secara terbuka di internet belum tentu bebas digunakan secara sembarangan tanpa aturan. **Lisensi perangkat lunak bebas (*open-source license*)** adalah kontrak hukum yang menentukan sejauh mana orang lain boleh menyalin, memodifikasi, dan mendistribusikan ulang sebuah karya. Catatan ini merangkum perbedaan tiga keluarga lisensi paling populer di dunia perangkat lunak bebas.

---

## 1. Perbandingan Tiga Lisensi Utama

| Jenis Lisensi | Sifat Utama | Kewajiban Membuka Kode Turunan | Contoh Proyek Populer |
| :--- | :--- | :--- | :--- |
| **GNU GPL (v2 / v3)** | *Copyleft* Kuat | **Wajib.** Setiap proyek turunan yang didistribusikan ulang harus tetap berlisensi GPL dan terbuka kodenya. | Kernel Linux, GIMP, Bash |
| **MIT License** | Permisif | **Tidak wajib.** Bebas dipakai di proyek terbuka maupun tertutup asal menyertakan catatan hak cipta asli. | jQuery, Ruby on Rails, VS Code (MIT core) |
| **Apache License 2.0** | Permisif + Paten | **Tidak wajib.** Mirip MIT, namun disertai perlindungan paten kontributor dan kewajiban mencatat perubahan file. | Android, Kubernetes, TensorFlow |

---

## 2. Memahami Perbedaan "Permisif" vs "Copyleft"
* **Lisensi Permisif (MIT, BSD, Apache):** Memberikan kebebasan seluas-luasnya bagi pengembang untuk menggabungkan kode terbuka ke dalam perangkat lunak komersial atau tertutup (*proprietary*), selama nama pencipta asli tetap dicantumkan.
* **Lisensi Copyleft (GNU GPL, AGPL):** Bertujuan menjaga agar kebebasan perangkat lunak tetap melekat selamanya. Jika seseorang memodifikasi kode berlisensi GPL dan membagikannya ke publik, hasil modifikasinya juga wajib dibagikan dengan kode sumber yang terbuka.

---

## 3. Panduan Singkat Memilih Lisensi untuk Proyek Pribadi
* Pilih **MIT License** apabila Anda membuat skrip kecil, pustaka kode, atau templat sederhana dan ingin agar siapa saja dapat memakainya tanpa hambatan birokrasi.
* Pilih **GNU GPLv3** apabila Anda membangun aplikasi utuh dan ingin memastikan tidak ada pihak yang menutup kode hasil pengembangan ulang dari karya Anda.
* Pilih **Creative Commons (CC BY-SA 4.0)** apabila repositori Anda berisi tulisan, artikel, atau dokumentasi catatan teknis (non-kode).

---

## Catatan Penutup
* Tanpa file `LICENSE` di dalam repositori publik, secara hukum hak cipta penuh tetap melekat pada penulis sehingga orang lain sebenarnya belum memiliki izin sah untuk menyalin atau memodifikasinya.
* Dokumentasi ini merupakan bagian dari arsip pribadi di [*Jejak Pikiran & Catatan Digital*](https://github.com/oeiboeo).
