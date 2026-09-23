# Contoh & Demonstrasi — Minggu 01

## Contoh 1: Manifestasi Locard's Exchange Principle pada Insiden Eksfiltrasi Data

### Skenario Kasus:
Seorang oknum pegawai internal (insider threat) mencuri basis data pelanggan rahasia perusahaan menggunakan media USB Flash Drive sebelum mengundurkan diri.

### Jejak yang Ditinggalkan di TKP Digital (Target Machine):
1. **Registry Windows**:
   - `HKLM\SYSTEM\CurrentControlSet\Enum\USBSTOR`: Menyimpan *Vendor ID*, *Product ID*, dan *Serial Number* unik dari USB Flash Drive yang dicolokkan.
   - `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\MountPoints2`: Mencatat GUID volume perangkat saat dikaitkan ke pengguna spesifik.
2. **File System ($MFT & USN Journal)**:
   - Entri $MFT mencatat pembuatan berkas arsip `pelanggan_2026.zip` beserta *timestamp* pembuatan dan akses.
3. **Windows Event Logs**:
   - *Event ID 20001 / 20003* pada `Microsoft-Windows-DriverFrameworks-UserMode`: Bukti proses inisialisasi dan koneksi perangkat penyimpanan USB.
4. **Shellbags & Recent Files**:
   - Menunjukkan navigasi folder target yang dibuka oleh pengguna sesaat sebelum penyalinan data.

### Jejak yang Terbawa oleh Pelaku (Suspect's Artifacts):
- Flash disk yang disita di rumah pelaku memiliki nomor seri yang identik dengan catatan di registry korban.
- Metadata berkas pada flash disk memuat *timestamp* yang beririsan dengan sesi login akun pelaku di komputer kantor.
- Hash kriptografis berkas arsip di flash disk cocok dengan salinan file master di server perusahaan.

---

## Contoh 2: Penerapan 4 Prinsip ACPO pada Penanganan Laptop yang Menyala (*Live Triage*)

### Skenario:
DEFR menemukan laptop tersangka dalam keadaan aktif, tidak terkunci (*unlocked*), dengan enkripsi disk BitLocker aktif dan sesi aplikasi perpesanan terenkripsi (Signal Desktop) sedang terbuka.

### Tindakan DEFR Mengikuti Pedoman ACPO:
1. **Penerapan Prinsip 1 & 2 (Intervensi Terkendali oleh Ahli Kompeten)**:
   - Jika laptop langsung dimatikan (tarik daya), kunci dekripsi BitLocker yang tersimpan di RAM akan hilang seketika, dan seluruh bukti pada storage tidak akan dapat didekripsi.
   - DEFR yang kompeten memutuskan melakukan *Live Memory Acquisition* terlebih dahulu menggunakan alat yang tervalidasi (misalnya: *Belkasoft RAM Capturer* atau *DumpIt* dari USB drive portabel).
   - Tindakan ini disadari akan mengubah sebagian kecil alokasi RAM (beberapa megabyte), namun DEFR memiliki justifikasi tertulis bahwa tindakan tersebut esensial untuk menyelamatkan kunci enkripsi volume.
2. **Penerapan Prinsip 3 (Audit Trail & Keterulangan)**:
   - DEFR mencatat dalam lembar kerja:
     - Waktu tepat intervensi: `2026-09-16 10:14:22 WIB`.
     - Tool yang digunakan: `DumpIt.exe v3.2.0`, dieksekusi dari drive `E:\`.
     - Nilai hash SHA-256 berkas memory dump: `a7f5b8...`.
     - Foto layar laptop sebelum dan sesudah proses ekstraksi.
3. **Penerapan Prinsip 4 (Tanggung Jawab Investigasi)**:
   - Seluruh lembar kendali, log riwayat, dan fisik perangkat diserahkan kepada penyidik penanggung jawab kasus (*Investigating Officer*) dengan tanda tangan *Chain of Custody*.

---

## Contoh 3: Demonstrasi Verifikasi Repeatability vs Reproducibility

### Kasus Uji: Verifikasi Bit-Stream Image Bukti Penyimpanan Flash Drive 8GB

```bash
# Skenario Pengujian Keterulangan (Repeatability):
# Alat: dc3dd pada workstation forensik A
# Kondisi: Sama persis, dilakukan 2 kali berturut-turut
$ dc3dd if=/dev/sdb of=/evidence/image_run1.dd hash=sha256
$ dc3dd if=/dev/sdb of=/evidence/image_run2.dd hash=sha256
# Hasil SHA-256 Run 1: e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
# Hasil SHA-256 Run 2: e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
# Kesimpulan: REPEATABLE (alat sama, hasil identik)

# Skenario Pengujian Reproduksibilitas (Reproducibility):
# Penguji independen kedua menggunakan alat berbeda (FTK Imager CLI / Guymager) di lab lain:
$ guymager --source /dev/sdb --output /lab2/verification.dd --hash-sha256
# Hasil SHA-256 Penguji Kedua: e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
# Kesimpulan: REPRODUCIBLE (alat beda, analis beda, hasil identik)
```
