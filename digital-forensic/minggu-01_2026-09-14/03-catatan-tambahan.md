# Catatan Tambahan — Minggu 01

## Pengumuman
- Kuliah Digital Forensic diselenggarakan oleh Fakultas Informatika Telkom University (kode mata kuliah terkait keamanan sistem dan forensik digital).
- Perkuliahan semester ini akan mencakup teori hukum pembuktian, akuisisi bukti fisik/logis, analisis artefak memori dan sistem berkas, hingga penyusunan laporan persidangan forensik.
- Mahasiswa diminta mempersiapkan lingkungan lab virtual (Linux CAINE / Kali Linux / SANS SIFT Workstation) untuk sesi praktikum mendatang.

## Tugas / Deadline
- **Tugas Mandiri 1**: Membaca ringkasan standar ISO/IEC 27037:2012 dan membandingkan peran serta tanggung jawab seorang *Digital Evidence First Responder* (DEFR) dengan *Digital Evidence Specialist* (DES).
- Format: Makalah ringkas 2 halaman, dikumpulkan pada pertemuan berikutnya.

## Catatan Dosen Penting
- **Integritas Bukti di Atas Segalanya**: Jangan pernah menghubungkan media bukti ke sistem analisis tanpa menggunakan *Hardware Write-Blocker* (atau software write-blocker teruji). Satu bit data yang berubah dapat menggugurkan kekuatan pembuktian di pengadilan (*admissibility*).
- **Enkripsi Disk Modern**: Pendekatan tradisional "langsung cabut kabel daya (*pull the plug*)" sudah usang untuk sistem modern yang dilindungi BitLocker, LUKS, atau FileVault. Penarikan RAM secara *live* menjadi prioritas jika sistem sedang menyala.
