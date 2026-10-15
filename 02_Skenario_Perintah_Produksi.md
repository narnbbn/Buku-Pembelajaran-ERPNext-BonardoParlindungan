# Skenario 2: Perintah & Proses Produksi (Manufacturing / Work Order)

## Tujuan Praktik
Mahasiswa mampu mengoperasikan modul **Manufacturing** di ERPNext:
1. Memahami kaitan antara **BOM (Bill of Materials)** dengan **Work Order**.
2. Melakukan transfer bahan baku dari gudang penyimpanan ke lantai pabrik (*Material Transfer for Manufacture*).
3. Melacak progres pekerjaan di stasiun kerja (*Job Cards & Operations*).
4. Menyelesaikan produksi barang jadi (*Stock Entry - Manufacture*) dan menghitung HPP otomatis.

---

## Latar Belakang Kasus
Setelah bahan baku diterima di `Gudang Bahan Baku - PDM`, manajer pabrik PT Dodoo menerbitkan surat perintah kerja untuk memproduksi **25 unit Kursi Belajar Kayu Dodoo (`FG-KD-001`)**.

---

## Rincian Perhitungan Kebutuhan Bahan (untuk 25 Unit Kursi)

Berdasarkan BOM Kursi Belajar Dodoo (`FG-KD-001`):

| Kode Item | Nama Item | Rasio per Unit | Total Diperlukan (25 Unit) | Satuan |
|---|---|---|---|---|
| `RM-KY-001` | Balok Kayu Mahoni 5x7x100 | 4 | **100** | Nos |
| `RM-BS-001` | Rangka Penyangga Besi | 2 | **50** | Nos |
| `RM-BT-001` | Baut & Mur Hex M6 | 8 | **200** | Nos |
| `RM-CT-001` | Cat Vernis Pelitur Kayu | 0.2 | **5** | Liter |
| `RM-BS-002` | Bantalan Dudukan Busa | 1 | **25** | Nos |

---

## Tahapan Eksekusi di ERPNext

### Langkah 1: Membuat Work Order
1. Buka menu **Manufacturing** > **Work Order** > Klik **Add Work Order**.
2. Masukkan parameter:
   - **Item to Manufacture**: `FG-KD-001` (Kursi Belajar Kayu Dodoo)
   - **Quantity to Manufacture**: `25`
   - **BOM**: Pilih BOM aktif untuk Kursi Belajar Kayu Dodoo
   - **Source Warehouse**: `Gudang Bahan Baku - PDM`
   - **WIP Warehouse**: `Gudang Barang Dalam Proses - PDM`
   - **Target Warehouse**: `Gudang Barang Jadi - PDM`
3. Klik **Save** kemudian klik **Submit**.
   *(Status Work Order akan berubah menjadi "Not Started")*.

---

### Langkah 2: Transfer Bahan ke Lantai Produksi (Material Transfer for Manufacture)
1. Pada dokumen Work Order yang berstatus *Not Started*, klik tombol **Start** di kanan atas.
2. ERPNext akan otomatis membuka formulir **Stock Entry** dengan tipe `Material Transfer for Manufacture`.
3. Periksa tabel baris barang: pastikan kuantitas barang sesuai kebutuhan 25 unit dan sumber gudang dari `Gudang Bahan Baku` menuju `Gudang Barang Dalam Proses`.
4. Klik **Save** lalu **Submit**.
   *(Status Work Order sekarang berubah menjadi "In Process")*.
5. *Pemeriksaan*: Buka menu **Stock Balance**, periksa bahwa stok bahan baku telah berpindah ke Gudang WIP.

---

### Langkah 3: Eksekusi Operasi & Jam Kerja (Job Cards)
*(Jika opsi "Use Multi-Level BOM" atau "Track Operations" diaktifkan)*:
1. Gulir ke bawah pada Work Order ke bagian **Operations / Job Cards**.
2. Klik masing-masing Job Card (Cutting -> Assembly -> Finishing -> Packing).
3. Klik **Start Job** dan **Complete Job** untuk mencatat waktu pengerjaan dan biaya operasional stasiun kerja.

---

### Langkah 4: Penyelesaian Produksi (Manufacture / Finish)
1. Kembali ke dokumen Work Order.
2. Klik tombol **Finish** di pojok kanan atas.
3. Sistem akan membuat dokumen **Stock Entry** dengan tipe `Manufacture`.
4. Periksa komponen:
   - Bahan baku berkurang dari `Gudang Barang Dalam Proses - PDM`.
   - Barang jadi (`FG-KD-001`) bertambah sebanyak **25 unit** di `Gudang Barang Jadi - PDM`.
5. Perhatikan bagian **Additional Operating Cost** yang otomatis terisi dari tarif workstation.
6. Klik **Save** lalu **Submit**.
7. Status Work Order akan berubah menjadi **Completed** (100%).

---

## Kunci Evaluasi & Hasil yang Diharapkan
- Di laporan **Stock Balance**:
  - `FG-KD-001` bertambah **25 unit** di Gudang Barang Jadi.
  - Stok balok kayu berkurang 100 pcs, rangka besi berkurang 50 pcs, baut berkurang 200 pcs, cat berkurang 5 L, busa berkurang 25 pcs.
  - Nilai valuasi barang jadi mencakup harga bahan baku ditambah biaya tenaga kerja/mesin.
