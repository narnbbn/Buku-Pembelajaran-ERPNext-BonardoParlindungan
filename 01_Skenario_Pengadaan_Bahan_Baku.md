# Skenario 1: Pengadaan Bahan Baku (Procurement / Purchasing)

## Tujuan Praktik
Mahasiswa mampu memahami dan mempraktikkan siklus pengadaan barang (P2P - *Procure to Pay*) pada modul **Buying** dan **Stock** di ERPNext untuk kebutuhan manufaktur:
`Material Request` -> `Purchase Order (PO)` -> `Purchase Receipt` -> `Purchase Invoice` -> `Payment Entry`.

---

## Latar Belakang Kasus
Departemen PPIC (*Production Planning and Inventory Control*) PT Dodoo Manufaktur Kreatif menjadwalkan produksi awal untuk **50 unit Kursi Belajar Dodoo** dan **20 unit Meja Belajar Dodoo**.
Gudang Bahan Baku saat ini masih kosong, sehingga perusahaan harus menerbitkan pesanan pembelian (Purchase Order) kepada para pemasok rekanan.

---

## Rincian Kebutuhan Pembelian (Purchase Orders)

### Pesanan 1: Kepada Pemasok Kayu (PT Kayu Lestari Abadi)
- **Supplier**: `PT Kayu Lestari Abadi`
- **Target Gudang Penerimaan**: `Gudang Bahan Baku - PDM`
- **Daftar Barang**:
  | Kode Item | Nama Item | Jumlah (Qty) | Satuan | Harga Satuan (IDR) | Total Harga (IDR) |
  |---|---|---|---|---|---|
  | `RM-KY-001` | Balok Kayu Mahoni 5x7x100 | 250 | Nos | Rp 20.000 | Rp 5.000.000 |
  | `RM-KY-002` | Papan Kayu Olahan 60x120 | 25 | Nos | Rp 75.000 | Rp 1.875.000 |
  | **Subtotal** | | | | | **Rp 6.875.000** |

---

### Pesanan 2: Kepada Pemasok Logam & Baut (CV Baja Presisi Logam)
- **Supplier**: `CV Baja Presisi Logam`
- **Target Gudang Penerimaan**: `Gudang Bahan Baku - PDM`
- **Daftar Barang**:
  | Kode Item | Nama Item | Jumlah (Qty) | Satuan | Harga Satuan (IDR) | Total Harga (IDR) |
  |---|---|---|---|---|---|
  | `RM-BS-001` | Rangka Penyangga Besi | 150 | Nos | Rp 30.000 | Rp 4.500.000 |
  | `RM-BT-001` | Baut & Mur Hex M6 | 700 | Nos | Rp 1.000 | Rp 700.000 |
  | **Subtotal** | | | | | **Rp 5.200.000** |

---

### Pesanan 3: Kepada Pemasok Kimia & Perlengkapan (Toko Sentosa Kimia)
- **Supplier**: `Toko Sentosa Kimia`
- **Target Gudang Penerimaan**: `Gudang Bahan Baku - PDM`
- **Daftar Barang**:
  | Kode Item | Nama Item | Jumlah (Qty) | Satuan | Harga Satuan (IDR) | Total Harga (IDR) |
  |---|---|---|---|---|---|
  | `RM-CT-001` | Cat Vernis Pelitur Kayu | 25 | Liter | Rp 45.000 | Rp 1.125.000 |
  | `RM-BS-002` | Bantalan Dudukan Busa | 60 | Nos | Rp 15.000 | Rp 900.000 |
  | **Subtotal** | | | | | **Rp 2.025.000** |

---

## Langkah-Langkah Eksekusi di ERPNext

1. **Buat Purchase Order (PO)**:
   - Masuk ke menu **Buying** > **Purchase Order** > Klik **Add Purchase Order**.
   - Pilih Supplier, tentukan tanggal transaksi, masukkan item dan kuantitas sesuai tabel di atas.
   - Klik **Save** lalu **Submit**.
2. **Terima Barang Fisik (Purchase Receipt)**:
   - Dari dokumen PO yang sudah disubmit, klik tombol **Create** di kanan atas > pilih **Receipt**.
   - Pastikan *Accepted Warehouse* mengarah ke `Gudang Bahan Baku - PDM`.
   - Klik **Save** lalu **Submit**.
   - *Verifikasi*: Cek menu **Stock** > **Stock Balance**, pastikan kuantitas bahan baku telah bertambah.
3. **Catat Tagihan Pemasok (Purchase Invoice)**:
   - Dari Purchase Receipt atau Purchase Order, klik **Create** > **Invoice**.
   - Verifikasi total tagihan, klik **Save** lalu **Submit**.
4. **Pembayaran ke Pemasok (Payment Entry - Opsional)**:
   - Dari Purchase Invoice, klik **Create** > **Payment**.
   - Masukkan Mode of Payment (misal: *Bank* atau *Cash*), simpan dan submit.
