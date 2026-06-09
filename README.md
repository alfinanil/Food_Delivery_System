# 🍔 Food Delivery Order System

Simulasi sistem pemesanan makanan online berbasis **Java Console Application** sebagai proyek mata kuliah **Struktur Data** — Informatika, Universitas Muhammadiyah Malang.

---

## 📋 Deskripsi

Sistem ini mensimulasikan alur pemesanan makanan secara online dengan fitur antrian reguler dan prioritas VIP, pemrosesan pesanan, pengecekan antrian, serta laporan efisiensi sistem.

---

## 🗂️ Struktur File

```
FoodDeliverySystem/
├── Main.java               # Entry point, loop menu utama
├── Menu.java               # Model data menu makanan
├── Order.java              # Model data pesanan pelanggan
├── FoodDeliverySystem.java # Logika utama semua fitur
└── README.md
```

---

## 🧱 Struktur Data yang Digunakan

| Struktur Data | Nama Variabel | Fungsi |
|---|---|---|
| `Queue<Order>` (LinkedList) | `antrianOrder` | Menyimpan pesanan pelanggan reguler — FIFO |
| `PriorityQueue<Order>` | `vipQueue` | Menyimpan pesanan VIP — diproses lebih dulu |
| `ArrayList<Menu>` | `daftarMenu` | Menyimpan daftar menu yang tersedia |
| `ArrayList<Order>` | `timeline` | Menyimpan riwayat pesanan yang sudah selesai |

---

## ✨ Fitur

### 1. Tambah Pesanan
- Input nama pelanggan
- Pilih menu dari daftar yang tersedia
- Cek status VIP
    - **VIP** → masuk ke `vipQueue` (PriorityQueue)
    - **Reguler** → masuk ke `antrianOrder` (Queue)
- Status awal pesanan: `PENDING`

### 2. Proses Pesanan
- Mengambil pesanan dari antrian — **VIP Queue diutamakan**
- Status berubah menjadi `COOKING`
- Opsi **cancel** pesanan → status `CANCELLED`
- Cek apakah ada **delay**
    - Ada delay → input menit tambahan, estimasi diperbarui
    - Tidak ada delay → estimasi sesuai standar menu
- Status akhir: `DONE`
- Pesanan disimpan ke `timeline`

### 3. Lihat Antrian
- Menampilkan isi **VIP Queue** (PriorityQueue)
- Menampilkan isi **Antrian Order** reguler (Queue)
- Jika kedua antrian kosong → tampilkan pesan tidak ada pesanan

### 4. Laporan Efisiensi
- Menampilkan statistik:
    - Total pesanan masuk
    - Pesanan selesai (DONE)
    - Total waktu proses (menit)
    - Total delay (menit)
    - Rata-rata waktu pengiriman
- **Timeline Order** — daftar semua pesanan yang telah selesai
- **Efficiency Report** — persentase penyelesaian dan catatan performa

### 5. Keluar
- Menampilkan pesan penutup dan mengakhiri program

