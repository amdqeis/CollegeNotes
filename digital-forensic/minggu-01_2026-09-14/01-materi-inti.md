# Materi Inti — Minggu 01

## 1. Definisi dan Hierarki Norma: Prinsip, Standar, Panduan, dan Praktik Terbaik

Dalam investigasi forensik digital, penanganan bukti harus memiliki legitimasi ilmiah dan hukum. Hierarki norma tata kelola bukti digital terbagi menjadi empat tingkatan:

- **Prinsip (*Principle*)**:
  - Kebenaran fundamental (*fundamental truth*) atau proposisi mendasar yang menjadi landasan sistem keyakinan, penalaran (*chain of reasoning*), dan pedoman bertindak atau evaluasi.
  - Sifatnya mutlak, konseptual, dan menjadi payung etika serta metodologi.
- **Standar (*Standards*)**:
  - Rumusan formula teknis yang telah disepakati secara konsensus internasional oleh para pakar (contoh: ISO - International Organization for Standardization).
  - Standar menetapkan *"the best way of doing something"* — mencakup pembuatan produk, pengelolaan proses pengujian laboratorium, hingga penyerahan material bukti.
  - Bersifat preskriptif, terukur, dan menjadi dasar sertifikasi/akreditasi.
- **Panduan (*Guidelines*)**:
  - Rekomendasi prosedural yang memberikan arahan teknis langkah demi langkah tanpa mengikat secara mutlak secara hukum, namun diakui oleh komunitas profesional.
  - Catatan evolutif: Seiring waktu dan matangnya teknologi, banyak pedoman (*guidelines*) berevolusi menjadi standar formal (*standards*).
- **Praktik Terbaik (*Best Practice*)**:
  - Metode, teknik, atau prosedur operasional yang secara umum diakui dan terbukti menghasilkan luaran yang superior dibandingkan alternatif lainnya.

---

## 2. Prinsip-Prinsip Utama Bukti Digital

### A. Prinsip Pertukaran Locard (*Locard's Exchange Principle*)
> *"Every contact leaves a trace."* — Prof. Edmond Locard (1910)

- **Konsep Dasar**:
  - Setiap kali ada kontak fisik atau interaksi antara seseorang (pelaku/korban) dengan lingkungan (tempat kejadian perkara/TKP) atau objek, terjadi perpindahan material timbal-balik (*cross-transfer of materials*).
  - Tujuan penyidikan: Menelusuri jejak (*follow the trails*) guna menghubungkan pelaku dengan korban dan TKP (*linking suspect, victim, and crime scene*).
- **Penerapan dalam Forensik Digital (Cyber Realm)**:
  - Pada intrusi komputer atau kejahatan siber, kontak digital menghasilkan jejak bukti (*digital traces*) di berbagai lapisan:
    - *File system*: Timestamps MACB ($Modified, Accessed, Created, Born/Entry Modified$), file slack, metadata $MFT$.
    - *Operating system*: Registry keys, Shimcache, Amcache, Shellbags, UserAssist, Prefetch.
    - *System & Network logs*: Syslog, Windows Event Logs, firewall traffic, DNS queries, packet captures.
  - **Transfer Dua Arah**: Pelaku meninggalkan artefak/malware di sistem target, sekaligus membawa pulang elemen dari TKP digital, seperti berkas curian, hash kredensial, atau basis data PII (*Personally Identifiable Information*). Jejak ini menjadi bukti pengait kepemilikan data saat penggeledahan fisik pelaku.

### B. Prinsip ACPO (*Association of Chief Police Officers*) untuk Bukti Digital
Pedoman ACPO Good Practice Guide for Digital Evidence menetapkan 4 prinsip baku:

1. **Prinsip 1 (Integritas Data Asli)**:
   - Tidak ada tindakan apa pun yang diambil oleh penegak hukum, personel yang dipekerjakan, atau agen mereka yang boleh **mengubah data** yang nantinya akan dijadikan barang bukti di pengadilan.
2. **Prinsip 2 (Kompetensi Akses Data Asli)**:
   - Apabila dalam kondisi mendesak/khusus seseorang harus mengakses data asli secara langsung, orang tersebut **wajib kompeten** dan mampu memberikan kesaksian serta penjelasan tertulis mengenai relevansi dan implikasi teknis dari tindakan yang diambil.
3. **Prinsip 3 (Audit Trail & Keterulangan)**:
   - Harus dibuat dan dipelihara jejak audit (*audit trail*) atau catatan lengkap dari semua proses yang diterapkan pada bukti digital. Pihak ketiga independen (*independent third party*) harus mampu meneliti catatan tersebut dan **menghasilkan luaran yang sama persis (*same result*)**.
4. **Prinsip 4 (Tanggung Jawab Investigasi)**:
   - Penanggung jawab penyidikan (*officer in charge*) memikul tanggung jawab menyeluruh untuk memastikan kepatuhan terhadap hukum dan semua prinsip forensik ini.

---

## 3. Standar dan Panduan Internasional

### Standar Baku:
- **ISO/IEC 27037:2012**: *Information technology — Security techniques — Guidelines for identification, collection, acquisition, and preservation of digital evidence*.
  - Standar fundamental panduan operasional DEFR dan DES.
- **ISO/IEC 17025**: *General requirements for the competence of testing and calibration laboratories*.
  - Menetapkan kompetensi teknis, kalibrasi peralatan, dan validasi metodologi laboratorium forensik.
- **NIST SP 800-86**: *Guide to Integrating Forensic Techniques into Incident Response*.
  - Panduan praktis integrasi teknis forensik ke dalam siklus penanganan insiden keamanan informasi.

### Panduan Komunitas Forensik (*Guidelines & Bodies*):
- **IOCE (International Organization on Computer Evidence)** (2002): Menetapkan prinsip pertukaran bukti digital internasional dan harmonisasi prosedur pemeriksaan.
- **SWGDE (Scientific Working Group on Digital Evidence)** (2013): Mengidentifikasi tiga jenis kegagalan/error utama pada tool forensik:
  1. *Incompleteness* (ketidaklengkapan data yang diekstraksi).
  2. *Inaccuracy* (ketidakakuratan hasil parsing atau decoding).
  3. *Misinterpretation* (salah interpretasi terhadap struktur data/artefak).
- **ENFSI (European Network of Forensic Science Institutes)** (2015): *Best Practice Manual for the Forensic Examination of Digital Technology*.

---

## 4. Kerangka Kerja Tata Kelola ISO/IEC 27037

### A. Konteks dan Driver Bukti Digital
Dalam operasional pengumpulan bukti digital di lapangan, sering terjadi tarik-menarik antara empat pendorong (*drivers*):
1. **Kualitas Pembuktian (*Evidential Quality*)**: Integritas dan ketelitian bukti di persidangan.
2. **Kecepatan Waktu Analisis (*Timeliness of Analysis*)**: Kebutuhan intelijen cepat tanggap.
3. **Pemulihan Layanan (*Restoration of Service*)**: Kebutuhan operasional bisnis agar sistem segera kembali aktif.
4. **Biaya (*Cost*)**: Efisiensi biaya pengadaan alat, transportasi, dan penyimpanan bukti.
Organisasi wajib memiliki mekanisme prioritisasi terencana (*prioritization process*) untuk menyeimbangkan keempat faktor tersebut.

### B. Tiga Prinsip Fundamental Bukti Digital (ISO/IEC 27037)
Bukti digital tunduk pada tiga pilar fundamental:
1. **Relevansi (*Relevance*)**:
   - Harus dapat dibuktikan secara rasional bahwa data yang diakuisisi memiliki nilai guna bagi penyelidikan insiden terkait (*probative value*).
   - Penilai atau investigator harus mampu mengaudit dan menjustifikasi alasan mengapa suatu data/perangkat spesifik disita.
2. **Keandalan (*Reliability*)**:
   - Seluruh proses penanganan harus dapat diaudit (*auditable*) dan dapat diulang (*repeatable*), serta menghasilkan hasil yang konsisten (*reproducible*).
3. **Kecukupan (*Sufficiency*)**:
   - Bukti yang dikumpulkan harus mencukupi untuk mendukung hipotesis penyidikan yang sah dan tuntas, tidak parsial atau terpotong tanpa dasar ilmiah yang logis.

### C. Pembagian Peran: DEFR vs DES
- **DEFR (*Digital Evidence First Responder*)**:
  - Personel lini pertama di lokasi kejadian (misal: petugas patroli terlatih, analis insiden pertama) yang berwenang mengamankan TKP, memprioritaskan bukti volatil, mendokumentasikan, dan melakukan akuisisi awal jika situasi darurat menuntut.
- **DES (*Digital Evidence Specialist*)**:
  - Ahli/spesialis forensik bersertifikasi yang menguasai teknik investigasi mendalam, ekstraksi hardware tingkat lanjut (chip-off, JTAG), analisis file system biner, dan memberikan kesaksian ahli di pengadilan.

### D. Auditability, Justifiability, Repeatability, dan Reproducibility
- **Keterbukaan Audit (*Auditability*)**: Tindakan harus tercatat sedemikian rinci sehingga pihak luar independen dapat menilai setiap langkah yang diambil.
- **Kemampuan Menjustifikasi (*Justifiability*)**: Investigator harus mampu menjelaskan dasar pertimbangan mengapa suatu metode teknis tertentu dipilih sebagai opsi terbaik.
- **Keterulangan (*Repeatability*)**:
  - Menghasilkan hasil tes yang identik di bawah kondisi:
    - Prosedur dan metode pengukuran yang sama;
    - Instrumen dan perkakas yang sama;
    - Kondisi lingkungan yang sama;
    - Dilakukan kapan saja setelah tes awal.
- **Reproduksibilitas (*Reproducibility*)**:
  - Menghasilkan hasil tes yang identik di bawah kondisi:
    - Metode pengukuran yang sama;
    - Instrumen atau perkakas yang **berbeda** (misalnya memverifikasi hasil *EnCase* menggunakan *FTK Imager* atau *dd*);
    - Kondisi lingkungan yang **berbeda**;
    - Dilakukan kapan saja setelah pengujian awal.

### E. Penanganan Sifat Bukti yang Fragile (*Fragile Nature*)
Bukti digital bersifat rentan terhadap manipulasi yang tidak disengaja (misal: pembaruan otomatis OS, penimpaan cache, pelepasan daya pada RAM). Prinsip penanganan meliputi:
1. **Minimalkan interaksi** dengan media penyimpanan/perangkat fisik asli (*minimize handling*).
2. **Catat setiap perubahan** (*account for any changes*): Jika perubahan status bit tidak dapat dihindari (misal: live acquisition RAM yang mengubah alokasi memori beberapa kilobyte), dampak perubahan harus dapat diukur, dijelaskan secara ilmiah, dan dijustifikasi.
3. **Patuhi aturan hukum pembuktian setempat** (*local rules of evidence*).
4. **Patuhi batas kompetensi**: Jangan melakukan tindakan di luar batas keahlian teknis yang teruji.
