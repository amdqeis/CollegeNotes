# Contoh & Demonstrasi — Minggu 02

## Contoh 1: Lembar Kontrol Rantai Penjagaan Bukti (*Chain of Custody Form*)

Dokumentasi Chain of Custody menjamin integritas hukum agar bukti tidak dapat disanggah (*admissible*) di pengadilan:

| Parameter | Catatan Lapangan |
| :--- | :--- |
| **Nomor Kasus / LP** | LP/B/104/IX/2026/DITTIPIDSIBER |
| **Deskripsi Barang Bukti** | Laptop ASUS ZenBook 14, S/N: `J3N0CV02K91823`, Warna Abu-abu, dengan stiker hitam di cover. |
| **Lokasi Penyitaan** | Meja kerja tersangka di PT ABC Finansial, Lantai 5, Ruang IT, Jakarta. |
| **Tanggal & Waktu Sita** | 2026-09-23 09:30 WIB |
| **Status Saat Ditemukan** | Menyala (*Powered ON*), layar terkunci PIN Windows. |
| **Tindakan Pengamanan** | Pengambilan live RAM dump (Prinsip ACPO 2) $\to$ Shutdown teratur $\to$ Penyegelan label anti-tamper. |

### Riwayat Perpindahan Bukti (*Custody Log*):

| Tanggal & Waktu | Dari (Pihak 1) | Kepada (Pihak 2) | Tujuan Pemindahan | Tanda Tangan |
| :--- | :--- | :--- | :--- | :--- |
| 2026-09-23 11:00 | Bripka A. Pratama (DEFR) | Iptu B. Santoso (Penyidik) | Transportasi dari TKP ke Lab Forensik | *(Ttd Terlampir)* |
| 2026-09-23 13:45 | Iptu B. Santoso (Penyidik) | Dr. Hendra, CHFI (DES Lab) | Penyerahan fisik media untuk akuisisi bit-stream | *(Ttd Terlampir)* |
| 2026-09-23 17:00 | Dr. Hendra, CHFI (DES Lab) | Locker Bukti Lab No. B-12 | Penyimpanan media asli pasca-akuisisi | *(Ttd Terlampir)* |

---

## Contoh 2: Perbandingan Praktis Akuisisi Fisik vs Akuisisi Logis

### Demonstrasi Kebutuhan Akuisisi Fisik untuk File Recovery:
Tersangka menghapus berkas dokumen konspirasi `rencana_fraud.docx` dari tempat sampah (*Recycle Bin*) sesaat sebelum digeledah.

```bash
# 1. Jika dilakukan Akuisisi Logis (hanya file yang terdaftar di sistem berkas aktif):
# Tool: cp / tar / robocopy
# Hasil: Berkas yang telah dihapus TIDAK AKAN terbawa karena penunjuk metadatanya telah dilepas.

# 2. Jika dilakukan Akuisisi Fisik (Bit-Stream Image):
# Tool: ddrescue / dc3dd melalui Write-Blocker
$ dc3dd if=/dev/nvme0n1 of=/evidence/suspect_drive.raw hash=sha256 log=/evidence/dc3dd.log

# Hasil: Seluruh sektor disk tersalin, termasuk Unallocated Space.
# Menggunakan teknik File Carving (Scalpel / Foremost / PhotoRec):
$ foremost -t docx -i /evidence/suspect_drive.raw -o /evidence/carved_output/

# Luaran Analisis:
# Berkas rencana_fraud.docx berhasil dipulihkan dari Unallocated Cluster 419200-419245
# Bukti fisik ini hanya bisa didapatkan melalui Physical Acquisition!
```

---

## Contoh 3: Struktur Evaluasi Bukti Memberatkan (*Inculpatory*) dan Meringankan (*Exculpatory*)

Dalam laporan forensik resmi (Tahap 5 Pelaporan), ahli wajib bersikap netral sesuai etika sains forensik:

> ### Petikan Laporan Pemeriksaan Forensik Digital (LHP-FD/2026/042)
> 
> **A. Temuan yang Memberatkan (Inculpatory Findings)**:
> 1. Berkas arsip basis data `nasabah_prioritas.sql` ditemukan di dalam direktori `Downloads` pada Secondary Copy citra disk tersangka.
> 2. Kunci registri Windows `UserAssist` membuktikan aplikasi klien FTP *FileZilla* dijalankan pada tanggal 2026-09-22 pukul 23:14 WIB, bertepatan dengan lonjakan trafik keluar sebesar 4.2 GB ke alamat IP luar negeri `198.51.100.45`.
> 
> **B. Temuan yang Meringankan (Exculpatory Findings)**:
> 1. Log antarmuka jaringan (*Event ID 1149*) menunjukkan adanya sesi *Remote Desktop Protocol* (RDP) yang aktif dari alamat IP anonim internal kantor pada rentang jam tersebut.
> 2. Ditemukan infeksi trojan backdoor (*njRAT*) yang terpasang pada komputer tersangka 3 hari sebelum insiden, yang memiliki kapabilitas kontrol kendali jarak jauh penuh (*remote desktop and file transfer*). Hal ini membuka kemungkinan teknis bahwa aksi eksfiltrasi dilakukan oleh peretas pihak ketiga yang membajak komputer tersangka tanpa sepengetahuannya.
