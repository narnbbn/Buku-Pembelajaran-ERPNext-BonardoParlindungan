# Skenario 3: Penjualan & Distribusi Produk Jadi (Order to Cash)

## Tujuan Praktik
Mahasiswa mampu memahami siklus penjualan (*Order to Cash* - O2C) pada modul **Selling**, **Stock**, dan **Accounts** di ERPNext:
`Quotation (Penawaran)` -> `Sales Order (SO)` -> `Delivery Note (Surat Jalan)` -> `Sales Invoice (Faktur Penjualan)` -> `Payment Entry`.

---

## Latar Belakang Kasus
Yayasan Sekolah Bintang Cerdas memesan perlengkapan kelas baru berupa **20 unit Kursi Belajar Kayu Dodoo (`FG-KD-001`)** yang baru saja selesai diproduksi.
Tim Sales PT Dodoo membuat kesepakatan penjualan dengan harga katalog standar Rp 250.000 / unit.

---

## Rincian Transaksi Penjualan

- **Customer**: `Yayasan Sekolah Bintang Cerdas`
- **Gudang Pengeluaran**: `Gudang Barang Jadi - PDM`
- **Daftar Pesanan**:
  | Kode Item | Nama Item | Jumlah (Qty) | Harga Satuan (IDR) | Total Harga (IDR) | HPP Satuan Estimasi | Estimasi Margin Kotor |
  |---|---|---|---|---|---|---|
  | `FG-KD-001` | Kursi Belajar Kayu Dodoo | 20 Nos | Rp 250.000 | **Rp 5.000.000** | ± Rp 194.900 | ± Rp 1.102.000 (22%) |

---

## Tahapan Eksekusi di ERPNext

### Langkah 1: Membuat Sales Order (SO)
1. Buka menu **Selling** > **Sales Order** > Klik **Add Sales Order**.
2. Masukkan rincian:
   - **Customer**: `Yayasan Sekolah Bintang Cerdas`
   - **Delivery Date**: Tentukan tanggal pengiriman (misal: 3 hari dari tanggal transaksi)
   - **Item Table**:
     - Item: `FG-KD-001`
     - Qty: `20`
     - Rate: `250.000`
3. Klik **Save** lalu **Submit**.
   *(Status Sales Order: "To Deliver and Bill")*.

---

### Langkah 2: Pengiriman Barang Fisik (Delivery Note)
1. Dari dokumen Sales Order yang telah disubmit, klik tombol **Create** di kanan atas > pilih **Delivery**.
2. Periksa bahwa sumber gudang (*Source Warehouse*) adalah `Gudang Barang Jadi - PDM`.
3. Pastikan kuantitas pengiriman adalah **20 unit**.
4. Klik **Save** lalu **Submit**.
5. *Pemeriksaan Stok*:
   - Buka menu **Stock** > **Stock Balance**.
   - Periksa bahwa stok `FG-KD-001` di Gudang Barang Jadi berkurang dari 25 unit menjadi **5 unit**.
   - Sistem secara otomatis mencatat jurnal akuntansi: Pendebetan *Cost of Goods Sold (COGS)* dan Pengkreditan *Stock In Hand*.

---

### Langkah 3: Menerbitkan Faktur Penjualan (Sales Invoice)
1. Kembali ke dokumen Sales Order (atau Delivery Note), klik **Create** > pilih **Invoice**.
2. Periksa rincian nilai total Rp 5.000.000.
3. Klik **Save** lalu **Submit**.
   *(Status Sales Order berubah menjadi "To Bill" jika sebagian, atau "Completed" jika lunas)*.

---

### Langkah 4: Penerimaan Pembayaran (Payment Entry)
1. Dari dokumen Sales Invoice, klik tombol **Create** > pilih **Payment**.
2. Tentukan metode pembayaran (*Mode of Payment*: Bank / Cash).
3. Pastikan nilai pembayaran lunas Rp 5.000.000.
4. Klik **Save** lalu **Submit**.
   *(Status Sales Invoice berubah menjadi "Paid")*.

---

## Analisis Pasca Transaksi (Laporan Keuangan & Manufaktur)

Mahasiswa diharapkan memeriksa 3 laporan penting di ERPNext:
1. **Gross Profit Report**:
   - Menu: **Accounts** > **Gross Profit**.
   - Verifikasi penjualan 20 unit Kursi menghasilkan laba kotor positif sesuai selisih Harga Jual dan HPP produksi.
2. **Stock Ledger**:
   - Menu: **Stock** > **Stock Ledger**.
   - Amati riwayat pergerakan barang mulai dari *Purchase Receipt* (penerimaan bahan baku), *Material Transfer for Manufacture*, *Manufacture* (masuknya barang jadi), hingga *Delivery Note* (keluarnya barang ke pelanggan).
3. **General Ledger / Profit and Loss Statement**:
   - Menu: **Accounts** > **Profit and Loss Statement**.
   - Amati pencatatan *Sales Revenue*, *Cost of Goods Sold (COGS)*, dan *Operating Expenses*.
