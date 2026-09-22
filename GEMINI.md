# College Note-Taking System

Rules ini **berdampingan** dengan rules global. Rules global tetap berlaku untuk `Projects/`
di Obsidian. GEMINI.md ini mengatur workflow khusus pencatatan kuliah.

---

## 0. Konteks Workspace

Workspace ini (`/home/key/Documents/college`) adalah pusat pencatatan materi kuliah.
Sistem pencatatan terbagi **dua tier**:

| Tier | Lokasi | Fungsi |
|------|--------|--------|
| **Tier 1 — Catatan Mingguan** | Workspace ini (`/home/key/Documents/college/<matkul>/`) | Catatan mentah per minggu, di-breakdown ke beberapa file dalam folder per minggu |
| **Tier 2 — Knowledge Base** | Obsidian vault `Kuliah/<Nama Matkul>/` | Rangkuman terstruktur, jurnal akademik, SUMMARY komprehensif, soal berbobot, evaluasi |

---

## 1. Daftar Mata Kuliah & Slug

Gunakan slug berikut secara konsisten di kedua tier:

| Mata Kuliah | Slug (Tier 1 — folder lokal) | Nama Folder (Tier 2 — Obsidian) |
|---|---|---|
| Digital Forensic | `digital-forensic` | `Digital Forensic` |
| Cyber Security | `cyber-security` | `Cyber Security` |
| Komputasi Awan | `komputasi-awan` | `Komputasi Awan` |
| Kecerdasan Artificial | `kecerdasan-artificial` | `Kecerdasan Artificial` |
| Tata Tulis Ilmiah | `tata-tulis-ilmiah` | `Tata Tulis Ilmiah` |
| Sosio Informatics | `sosio-informatics` | `Sosio Informatics` |
| Manajemen Projek TIK | `manajemen-projek-tik` | `Manajemen Projek TIK` |
| Kewarganegaraan | `kewarganegaraan` | `Kewarganegaraan` |

Kalau user menyebut nama mata kuliah dengan variasi penulisan (misal "digfor", "AI",
"cloud computing", "awan", "matkul TIK"), cocokkan ke slug yang benar — jangan buat
folder/entry baru.

---

## 2. Tier 1 — Catatan Mingguan (Workspace Lokal)

### 2a. Struktur Folder — Folder Per Minggu

Setiap minggu mendapat **folder sendiri**, bukan satu file tunggal. Di dalam folder minggu,
materi di-breakdown menjadi beberapa file terpisah agar mudah dinavigasi dan di-review.

```
/home/key/Documents/college/
├── digital-forensic/
│   ├── minggu-01_2026-09-15/
│   │   ├── 00-overview.md          ← Ringkasan topik minggu ini + metadata
│   │   ├── 01-materi-inti.md       ← Poin-poin utama yang diajarkan
│   │   ├── 02-contoh-demo.md       ← Contoh, demonstrasi, studi kasus
│   │   ├── 03-catatan-tambahan.md  ← Pengumuman, tugas, hal penting lain
│   │   └── 04-pertanyaan.md        ← Hal yang belum dipahami
│   ├── minggu-02_2026-09-22/
│   │   ├── 00-overview.md
│   │   ├── 01-materi-inti.md
│   │   ├── 02-contoh-demo.md
│   │   ├── 03-catatan-tambahan.md
│   │   └── 04-pertanyaan.md
│   └── ...
├── cyber-security/
│   ├── minggu-01_2026-09-15/
│   │   └── ... (struktur sama)
│   └── ...
├── komputasi-awan/
├── kecerdasan-artificial/
├── tata-tulis-ilmiah/
├── sosio-informatics/
├── manajemen-projek-tik/
└── kewarganegaraan/
```

### 2b. Penamaan Folder Minggu

Format: `minggu-<NN>_<tanggal-Senin-minggu-itu>/`

- `<NN>` = nomor minggu, dua digit, dimulai dari `01`.
- `<tanggal-Senin>` = tanggal hari Senin di minggu tersebut, format `YYYY-MM-DD`.
- Contoh: `minggu-03_2026-09-29/`

Kalau dalam satu minggu ada lebih dari satu pertemuan untuk matkul yang sama,
tetap satu folder — tambahkan section terpisah di file yang relevan, atau buat file
tambahan dengan prefix `01b-`, `02b-`, dst. jika pertemuan kedua membahas sub-topik
yang cukup berbeda.

### 2c. Breakdown File Per Minggu

Setiap folder minggu WAJIB berisi file-file berikut:

| File | Fungsi |
|------|--------|
| `00-overview.md` | Metadata minggu (frontmatter) + ringkasan singkat topik yang dibahas. Ini adalah "pintu masuk" folder minggu. |
| `01-materi-inti.md` | Poin-poin utama yang diajarkan di kelas. Inti dari catatan kuliah. |
| `02-contoh-demo.md` | Contoh yang diberikan dosen, demonstrasi, studi kasus, code snippet, dsb. |
| `03-catatan-tambahan.md` | Hal penting lain: pengumuman, deadline tugas, info ujian, catatan dosen. |
| `04-pertanyaan.md` | Hal yang belum dipahami, perlu ditanyakan, atau perlu dicari tahu lebih lanjut. |

**Aturan tambahan:**
- Kalau salah satu file tidak relevan untuk minggu tertentu (misal tidak ada contoh/demo),
  tetap buat file-nya tapi isi dengan `<!-- Tidak ada untuk minggu ini -->`.
- Kalau ada materi tambahan yang tidak masuk kategori di atas (misal transkrip diskusi,
  foto papan tulis yang di-OCR, slide yang di-dump), buat file tambahan dengan prefix
  `05-`, `06-`, dst. dan nama deskriptif (misal `05-transkrip-diskusi.md`).

### 2d. Template File Per Minggu

#### `00-overview.md`

```markdown
---
matkul: <Nama Mata Kuliah>
minggu: <nomor>
tanggal_pertemuan: <YYYY-MM-DD>
topik: <Judul Topik>
dosen: <nama dosen jika diketahui>
jumlah_file: <jumlah file dalam folder ini>
---

# Minggu <NN> — <Judul Topik>

## Ringkasan Singkat
<!-- 2-3 kalimat merangkum apa yang dibahas minggu ini -->

## Daftar File Minggu Ini
- [01-materi-inti.md](./01-materi-inti.md) — Materi inti
- [02-contoh-demo.md](./02-contoh-demo.md) — Contoh & demonstrasi
- [03-catatan-tambahan.md](./03-catatan-tambahan.md) — Catatan tambahan
- [04-pertanyaan.md](./04-pertanyaan.md) — Pertanyaan
```

#### `01-materi-inti.md`

```markdown
# Materi Inti — Minggu <NN>

## <Sub-topik 1>
<!-- Penjelasan poin utama -->

## <Sub-topik 2>
<!-- Penjelasan poin utama -->

<!-- Tambahkan sub-topik sesuai kebutuhan -->
```

#### `02-contoh-demo.md`

```markdown
# Contoh & Demonstrasi — Minggu <NN>

## Contoh 1: <Judul>
<!-- Deskripsi contoh, langkah-langkah, atau code snippet -->

## Contoh 2: <Judul>
<!-- Deskripsi contoh -->

<!-- Tambahkan contoh sesuai kebutuhan -->
```

#### `03-catatan-tambahan.md`

```markdown
# Catatan Tambahan — Minggu <NN>

## Pengumuman
<!-- Pengumuman dari dosen -->

## Tugas / Deadline
<!-- Tugas yang diberikan, deadline, format pengumpulan -->

## Lain-lain
<!-- Hal penting lain yang perlu diingat -->
```

#### `04-pertanyaan.md`

```markdown
# Pertanyaan & Belum Dipahami — Minggu <NN>

## Pertanyaan
1. <!-- Pertanyaan yang muncul saat kuliah -->
2. <!-- ... -->

## Perlu Dicari Tahu
- <!-- Konsep yang perlu dipelajari lebih lanjut -->
```

### 2e. Aturan Penulisan Tier 1

- **Bahasa**: Indonesia. Istilah teknis boleh dalam bahasa Inggris.
- **Tujuan**: Menangkap materi **apa adanya** dari kelas. Belum perlu rapi atau lengkap.
- **Kecepatan > kesempurnaan**: Tier 1 adalah catatan mentah. Perbaikan dan pengayaan
  dilakukan di Tier 2.
- Kalau user memberikan foto papan tulis, slide, atau materi mentah, masukkan isinya
  ke dalam file yang sesuai dalam folder minggu tersebut.
- **Satu folder = satu minggu**. Jangan mencampur materi dari minggu berbeda dalam
  satu folder.

---

## 3. Tier 2 — Knowledge Base (Obsidian Vault: `Kuliah/`)

### 3a. Struktur Folder

Folder `Kuliah/` berada di **root vault Obsidian**, setara dengan `Projects/`.

```
Kuliah/
├── 00-index.md                          ← MOC (Map of Content) seluruh matkul
├── Digital Forensic/
│   ├── 00-overview.md                   ← Ringkasan matkul, silabus, referensi
│   ├── rangkuman/
│   │   ├── 01-pengantar-digital-forensic.md
│   │   ├── 02-bukti-digital.md
│   │   └── ...
│   ├── summary/
│   │   ├── summary-01-pengantar-digital-forensic.md
│   │   ├── summary-02-bukti-digital.md
│   │   └── ...
│   ├── jurnal/
│   │   ├── jurnal-01-pengantar-digital-forensic.md
│   │   └── ...
│   ├── latihan-soal/
│   │   ├── soal-01-pengantar-digital-forensic.md
│   │   └── ...
│   └── evaluasi/
│       ├── uts-review.md
│       └── uas-review.md
├── Cyber Security/
│   ├── 00-overview.md
│   ├── rangkuman/
│   ├── summary/
│   ├── jurnal/
│   ├── latihan-soal/
│   └── evaluasi/
├── Komputasi Awan/
│   └── ... (struktur sama)
├── Kecerdasan Artificial/
├── Tata Tulis Ilmiah/
├── Sosio Informatics/
├── Manajemen Projek TIK/
└── Kewarganegaraan/
```

### 3b. Penjelasan Tiap Komponen

#### `00-index.md` (MOC — Map of Content)
- Satu file di root `Kuliah/` yang menjadi **pintu masuk** ke seluruh catatan kuliah.
- Berisi daftar semua mata kuliah dengan wikilink ke masing-masing `00-overview.md`.
- Update otomatis setiap kali ada rangkuman, summary, jurnal, atau evaluasi baru.

#### `00-overview.md` (per mata kuliah)
- Ringkasan mata kuliah: deskripsi, tujuan pembelajaran, referensi utama, nama dosen.
- Daftar topik/silabus (kalau tersedia).
- Wikilink ke semua rangkuman, summary, jurnal, latihan soal, dan evaluasi yang sudah ada.
- **Wajib di-update** setiap kali ada file baru di subfolder mana pun.

#### `rangkuman/` — Rangkuman Per Topik
- Satu file per topik (bukan per minggu). Kalau satu topik dibahas 2-3 minggu, tetap
  satu file rangkuman — tambahkan kontennya.
- Penamaan: `<NN>-<judul-topik-slug>.md` (contoh: `01-pengantar-digital-forensic.md`)
- **Isi harus lebih advance dari Tier 1**:
  - Rangkuman terstruktur dan rapi dari materi kelas
  - Penjelasan tambahan dari sumber lain (buku, paper, artikel, dokumentasi resmi)
  - Diagram, tabel, atau visualisasi kalau relevan
  - Referensi/sumber yang digunakan (dalam section `## Referensi` di akhir file)

#### `summary/` — SUMMARY Komprehensif Per Topik *(BARU)*

Tujuan utama SUMMARY: **membuat user memahami isi konteks topik secara LENGKAP tanpa
perlu membaca seluruh rangkuman, tapi juga TIDAK bertele-tele**. SUMMARY adalah versi
"kalau kamu cuma bisa baca satu file untuk menguasai topik ini, baca file ini."

- Penamaan: `summary-<NN>-<judul-topik-slug>.md`
  (contoh: `summary-01-pengantar-digital-forensic.md`)
- Satu SUMMARY per topik, sejajar dengan rangkuman yang bersesuaian.
- **WAJIB dibuat** setiap kali rangkuman baru dibuat atau di-update signifikan.

**Aturan penulisan SUMMARY:**
1. **Lengkap tapi padat**: Cakup SEMUA konsep penting dari topik. Jangan skip sub-topik
   hanya karena "terlihat sederhana" — kalau itu bagian dari materi, masuk ke summary.
2. **Tidak bertele-tele**: Hindari pengulangan, filler words, dan kalimat pembuka generik.
   Langsung ke inti. Setiap kalimat harus menambah pemahaman baru.
3. **Struktur hierarkis**: Gunakan heading dan sub-heading yang jelas. Reader harus bisa
   scan heading dan langsung tahu topik apa yang dibahas di tiap bagian.
4. **Gunakan analogi dan contoh konkret**: Untuk konsep abstrak, sertakan minimal satu
   analogi atau contoh nyata yang membantu pemahaman.
5. **Hubungkan antar konsep**: Jelaskan bagaimana sub-topik saling terkait, bukan hanya
   daftar poin terpisah. User harus mendapat "big picture."
6. **Panjang proporsional**: Summary untuk topik besar (misal "arsitektur cloud computing")
   boleh lebih panjang dari topik kecil (misal "definisi forensik digital"). Patokan kasar:
   - Topik kecil/sederhana: 500–1000 kata
   - Topik sedang: 1000–2000 kata
   - Topik besar/kompleks: 2000–3500 kata
7. **Sertakan diagram ASCII/mermaid** kalau ada proses, alur, atau hierarki yang lebih mudah
   dipahami secara visual.
8. **Closing: "Key Takeaways"**: Akhiri dengan 3-7 poin takeaway paling kritis yang harus
   diingat, dalam format bullet points.

#### `jurnal/` — Referensi Jurnal Akademik Per Topik *(BARU)*

Tujuan: memberikan **basis ilmiah** untuk setiap topik melalui jurnal/paper akademik
yang relevan dan terkini.

- Penamaan: `jurnal-<NN>-<judul-topik-slug>.md`
  (contoh: `jurnal-01-pengantar-digital-forensic.md`)
- Satu file jurnal per topik, sejajar dengan rangkuman yang bersesuaian.
- **WAJIB dibuat** setiap kali rangkuman baru dibuat.

**Aturan pencarian dan penulisan jurnal:**
1. **Minimal 5 jurnal per topik**. Boleh lebih kalau topik luas atau ada banyak
   perspektif yang perlu dicakup.
2. **Rentang tahun: 5 tahun terakhir** (dari tahun sekarang ke belakang).
   Per tahun 2026, berarti jurnal dari 2021–2026.
   Pengecualian: jurnal seminal/klasik yang menjadi fondasi bidang boleh lebih tua,
   tapi harus diberi catatan "[Seminal Paper]" dan tidak menggantikan kuota 5 jurnal terkini.
3. **Sumber pencarian**: Gunakan `search_web` dengan query yang ditargetkan ke:
   - Google Scholar (site:scholar.google.com)
   - IEEE Xplore, ACM Digital Library, ScienceDirect, Springer, arXiv
   - Repository jurnal Indonesia: Sinta, Garuda, jurnal.id
4. **Untuk setiap jurnal, catat:**
   - Judul lengkap
   - Penulis (semua, atau 3 pertama + "et al." kalau banyak)
   - Tahun publikasi
   - Nama jurnal/konferensi/publisher
   - DOI atau URL langsung ke paper (kalau tersedia)
   - **Ringkasan relevansi** (2-4 kalimat): mengapa jurnal ini relevan dengan topik,
     temuan utama, dan kontribusi ke pemahaman topik
5. **Kategorisasi jurnal**: Kelompokkan jurnal berdasarkan sub-aspek topik yang mereka
   bahas, bukan sekadar daftar datar.
6. **Jangan asal tempel**: Setiap jurnal harus benar-benar relevan dengan topik yang
   sedang dibahas. Lebih baik 5 jurnal sangat relevan daripada 10 yang sebagian nyasar.

#### `latihan-soal/` — Soal Berbobot *(DIPERBARUI)*

- Penamaan: `soal-<NN>-<judul-topik-slug>.md`
  (contoh: `soal-01-pengantar-digital-forensic.md`)
- Satu file soal per topik, sejajar dengan rangkuman.
- **WAJIB dibuat** setiap kali rangkuman baru dibuat.

**Aturan soal berbobot:**
1. **Minimal 10 soal per topik**. Boleh lebih.
2. **Distribusi level wajib** — setiap file HARUS mencakup ketiga level:

   | Level | Jumlah Min. | Deskripsi |
   |-------|-------------|-----------|
   | 🟢 **Mudah** | 3 soal | Pemahaman dasar: definisi, recall fakta, identifikasi konsep. Mahasiswa yang hadir di kelas dan membaca materi seharusnya bisa menjawab. |
   | 🟡 **Sedang** | 4 soal | Aplikasi & analisis: menerapkan konsep ke skenario baru, membandingkan pendekatan, menganalisis kasus, menjelaskan proses. Butuh pemahaman mendalam, bukan sekadar hafalan. |
   | 🔴 **Olimpiade** | 3 soal | Level kompetisi/riset: menggabungkan beberapa konsep, mengevaluasi trade-off kompleks, merancang solusi untuk masalah yang belum pernah dibahas di kelas, membantah/mempertahankan argumen, atau soal yang membutuhkan kreativitas dan deep thinking. Ibarat soal olimpiade atau pertanyaan viva voce. |

3. **Tipe soal bervariasi** — jangan semua pilihan ganda atau semua essay.
   Kombinasikan dari:
   - Pilihan ganda (dengan pengecoh yang masuk akal, bukan asal)
   - Essay pendek (jawaban 1-3 paragraf)
   - Essay panjang / argumentatif (jawaban 4+ paragraf, ada tesis dan argumen)
   - Studi kasus (diberikan skenario, analisis dan beri solusi)
   - Coding challenge (kalau relevan dengan matkul)
   - True/False dengan justifikasi (harus jelaskan mengapa benar/salah)
   - Diagram/flowchart (gambarkan proses, arsitektur, atau alur)

4. **Setiap soal WAJIB punya:**
   - Label level: `🟢 Mudah`, `🟡 Sedang`, atau `🔴 Olimpiade`
   - Tipe soal (pilihan ganda, essay, studi kasus, dll.)
   - Soal yang jelas dan tidak ambigu
   - Jawaban dan pembahasan lengkap (di-collapse pakai callout)
   - Untuk level Olimpiade: sertakan juga **rubrik penilaian** atau **kriteria
     jawaban sempurna** supaya user tahu standar yang diharapkan

5. **Soal harus berbasis materi** — semua soal harus bisa dijawab berdasarkan
   rangkuman + summary + jurnal yang sudah ada. Jangan buat soal tentang materi
   yang belum dicakup.

6. **Soal Olimpiade harus genuinely sulit** — bukan sekadar soal sedang yang
   dipanjangkan. Ciri soal Olimpiade yang baik:
   - Membutuhkan sintesis dari beberapa sub-topik atau bahkan cross-matkul
   - Ada elemen "jebakan" yang menguji ketelitian
   - Memerlukan evaluasi kritis, bukan sekadar aplikasi formula
   - Bisa memicu perdebatan atau punya lebih dari satu pendekatan valid

#### `evaluasi/` — Review untuk Ujian
- `uts-review.md` — Rangkuman komprehensif untuk UTS (mencakup semua topik sebelum UTS)
- `uas-review.md` — Rangkuman komprehensif untuk UAS (mencakup semua topik)
- Bisa juga berisi file evaluasi tambahan seperti `quiz-review-01.md` kalau ada kuis.
- Evaluasi berisi: ringkasan semua topik, poin-poin kunci, rumus/konsep penting,
  dan kumpulan soal latihan terpilih.

### 3c. Aturan Wikilink (WAJIB)

Semua file di `Kuliah/` HARUS saling terhubung via wikilink. Aturan spesifik:

| File | Wajib Link Ke |
|------|---------------|
| `00-index.md` | Semua `00-overview.md` tiap matkul |
| `00-overview.md` | `[[Kuliah/00-index\|Index Kuliah]]` + semua rangkuman, summary, jurnal, latihan, evaluasi di matkul itu |
| `rangkuman/*.md` | `[[Kuliah/<Matkul>/00-overview\|Overview]]` + summary & jurnal yang bersesuaian + rangkuman terkait (prerequisite) + latihan soal yang relevan |
| `summary/*.md` | `[[Kuliah/<Matkul>/00-overview\|Overview]]` + rangkuman yang menjadi basis + jurnal yang bersesuaian |
| `jurnal/*.md` | `[[Kuliah/<Matkul>/00-overview\|Overview]]` + rangkuman & summary yang bersesuaian |
| `latihan-soal/*.md` | `[[Kuliah/<Matkul>/00-overview\|Overview]]` + rangkuman & summary yang menjadi bahan soal |
| `evaluasi/*.md` | `[[Kuliah/<Matkul>/00-overview\|Overview]]` + semua rangkuman & summary yang dicakup |

**Cross-matkul linking**: Kalau ada topik yang berkaitan antar matkul (misal topik
"enkripsi" di Cyber Security relevan dengan "bukti digital" di Digital Forensic),
buat wikilink cross-reference antar rangkuman/summary tersebut.

### 3d. Template Rangkuman

```markdown
---
matkul: <Nama Mata Kuliah>
topik: <Judul Topik>
minggu_terkait: [<nomor minggu yang dicakup>]
sumber:
  - <referensi 1>
  - <referensi 2>
last_updated: <YYYY-MM-DD>
---

# <Judul Topik>

> Rangkuman ini mencakup materi dari [[Kuliah/<Matkul>/00-overview|<Nama Matkul>]]
> Summary: [[Kuliah/<Matkul>/summary/summary-<NN>-<slug>|Summary Topik Ini]]
> Jurnal: [[Kuliah/<Matkul>/jurnal/jurnal-<NN>-<slug>|Jurnal Topik Ini]]

## Konsep Utama

### <Sub-topik 1>
<!-- Penjelasan mendalam -->

### <Sub-topik 2>
<!-- Penjelasan mendalam -->

## Diagram / Visualisasi
<!-- Kalau relevan -->

## Contoh Penerapan
<!-- Studi kasus, contoh nyata -->

## Hubungan dengan Topik Lain
<!-- Wikilink ke rangkuman lain yang terkait, baik di matkul ini maupun matkul lain -->

- Terkait: [[Kuliah/.../rangkuman/xxx|Topik XXX]]

## Referensi

1. ...
2. ...
```

### 3e. Template SUMMARY

```markdown
---
matkul: <Nama Mata Kuliah>
topik: <Judul Topik>
rangkuman_basis: <NN>-<judul-topik-slug>.md
minggu_terkait: [<nomor minggu yang dicakup>]
last_updated: <YYYY-MM-DD>
---

# SUMMARY: <Judul Topik>

> Summary komprehensif dari [[Kuliah/<Matkul>/rangkuman/<NN>-<slug>|Rangkuman Topik Ini]]
> Jurnal pendukung: [[Kuliah/<Matkul>/jurnal/jurnal-<NN>-<slug>|Jurnal Topik Ini]]

## Gambaran Umum
<!-- 1-2 paragraf: Apa topik ini, mengapa penting, dan di mana posisinya dalam
     keseluruhan mata kuliah. Langsung ke inti, tanpa basa-basi. -->

## <Konsep Utama 1>
<!-- Penjelasan padat. Setiap paragraf menambah pemahaman baru.
     Sertakan analogi/contoh konkret untuk konsep abstrak. -->

## <Konsep Utama 2>
<!-- ... -->

## <Konsep Utama N>
<!-- Tambahkan sesuai kebutuhan. Jangan skip sub-topik. -->

## Hubungan Antar Konsep
<!-- Jelaskan bagaimana konsep-konsep di atas saling terkait.
     Bisa pakai diagram mermaid/ASCII kalau membantu. -->

## Key Takeaways

1. <!-- Poin kritis #1 yang HARUS diingat -->
2. <!-- Poin kritis #2 -->
3. <!-- Poin kritis #3 -->
<!-- Minimal 3, maksimal 7 poin -->
```

### 3f. Template Jurnal Akademik

```markdown
---
matkul: <Nama Mata Kuliah>
topik: <Judul Topik>
rangkuman_basis: <NN>-<judul-topik-slug>.md
jumlah_jurnal: <jumlah>
rentang_tahun: 2021-2026
last_updated: <YYYY-MM-DD>
---

# Jurnal Akademik: <Judul Topik>

> Referensi jurnal untuk [[Kuliah/<Matkul>/rangkuman/<NN>-<slug>|Rangkuman Topik Ini]]
> Summary: [[Kuliah/<Matkul>/summary/summary-<NN>-<slug>|Summary Topik Ini]]

## <Aspek/Sub-topik 1>

### Jurnal 1
- **Judul**: <judul lengkap>
- **Penulis**: <penulis>
- **Tahun**: <tahun>
- **Publikasi**: <nama jurnal/konferensi>
- **DOI/URL**: <doi atau url>
- **Relevansi**: <2-4 kalimat mengapa jurnal ini relevan, temuan utama,
  kontribusi ke pemahaman topik>

### Jurnal 2
<!-- format sama -->

## <Aspek/Sub-topik 2>

### Jurnal 3
<!-- ... -->

<!-- Lanjutkan sampai minimal 5 jurnal tercakup -->

## Ringkasan Temuan Lintas Jurnal
<!-- 1-2 paragraf merangkum insight utama yang didapat dari kumpulan jurnal ini.
     Apa konsensus penelitian saat ini? Ada gap atau kontroversi? -->
```

### 3g. Template Latihan Soal Berbobot

```markdown
---
matkul: <Nama Mata Kuliah>
topik_terkait: [<topik yang dicakup>]
jumlah_soal: <jumlah>
distribusi:
  mudah: <jumlah>
  sedang: <jumlah>
  olimpiade: <jumlah>
tipe: [pilihan-ganda, essay, studi-kasus, true-false, coding, diagram]
last_updated: <YYYY-MM-DD>
---

# Latihan Soal: <Judul Topik>

> Berdasarkan materi:
> - [[Kuliah/<Matkul>/rangkuman/<NN>-<slug>|Rangkuman]]
> - [[Kuliah/<Matkul>/summary/summary-<NN>-<slug>|Summary]]
> - [[Kuliah/<Matkul>/jurnal/jurnal-<NN>-<slug>|Jurnal]]

---

## 🟢 Level Mudah

### Soal 1 — 🟢 Mudah | Pilihan Ganda
<!-- Isi soal -->

A. ...
B. ...
C. ...
D. ...

> [!note]- Jawaban & Pembahasan
> **Jawaban: X**
> <!-- Penjelasan mengapa jawaban tersebut benar dan yang lain salah -->

### Soal 2 — 🟢 Mudah | True/False + Justifikasi
<!-- Isi soal -->

> [!note]- Jawaban & Pembahasan
> **Jawaban: True/False**
> <!-- Justifikasi -->

### Soal 3 — 🟢 Mudah | Essay Pendek
<!-- Isi soal -->

> [!note]- Jawaban & Pembahasan
> <!-- Jawaban -->

---

## 🟡 Level Sedang

### Soal 4 — 🟡 Sedang | Studi Kasus
<!-- Isi soal dengan skenario -->

> [!note]- Jawaban & Pembahasan
> <!-- Analisis dan jawaban -->

### Soal 5 — 🟡 Sedang | Essay
<!-- ... -->

### Soal 6 — 🟡 Sedang | ...
### Soal 7 — 🟡 Sedang | ...

---

## 🔴 Level Olimpiade

### Soal 8 — 🔴 Olimpiade | Essay Argumentatif
<!-- Isi soal yang menantang -->

> [!note]- Jawaban, Pembahasan & Rubrik Penilaian
> **Rubrik:**
> - Kriteria 1 (bobot X%): ...
> - Kriteria 2 (bobot X%): ...
>
> **Jawaban model:**
> <!-- Jawaban lengkap -->

### Soal 9 — 🔴 Olimpiade | Studi Kasus Kompleks
<!-- ... -->

### Soal 10 — 🔴 Olimpiade | Sintesis Cross-Topik
<!-- Soal yang menggabungkan beberapa konsep -->

> [!note]- Jawaban, Pembahasan & Rubrik Penilaian
> <!-- ... -->
```

### 3h. Urutan Pembuatan File Tier 2 (Per Topik)

Setiap kali ada topik baru yang masuk, file Tier 2 dibuat dalam urutan ini:

1. **Rangkuman** (`rangkuman/<NN>-<slug>.md`) — basis dari semua file lain
2. **Jurnal** (`jurnal/jurnal-<NN>-<slug>.md`) — cari jurnal, perkaya pemahaman
3. **Summary** (`summary/summary-<NN>-<slug>.md`) — sintesis rangkuman + jurnal
4. **Soal** (`latihan-soal/soal-<NN>-<slug>.md`) — berdasarkan semua file di atas
5. **Update `00-overview.md`** — tambah link ke semua file baru

Urutan ini penting karena setiap file bergantung pada file sebelumnya.

---

## 4. Workflow Pencatatan

### 4a. Saat User Memberikan Materi Kelas (Input Baru)

1. **Identifikasi** mata kuliah dan minggu ke berapa.
2. **Tier 1**: Buat folder `minggu-<NN>_<tanggal>/` di folder matkul yang sesuai,
   lalu isi dengan file-file sesuai breakdown di section 2c-2d:
   - `00-overview.md` — metadata + ringkasan singkat
   - `01-materi-inti.md` — poin-poin utama
   - `02-contoh-demo.md` — contoh dan demonstrasi
   - `03-catatan-tambahan.md` — pengumuman, tugas, dll.
   - `04-pertanyaan.md` — hal yang belum dipahami
   - File tambahan kalau ada materi ekstra
3. **Tier 2**: Setelah Tier 1 selesai, **langsung** buat/update di Obsidian
   mengikuti urutan di section 3h:
   a. Buat/update **rangkuman** di `Kuliah/<Matkul>/rangkuman/`
   b. Cari **jurnal akademik** — minimal 5, rentang 5 tahun terakhir — dan buat
      file di `Kuliah/<Matkul>/jurnal/`
   c. Buat **SUMMARY** komprehensif di `Kuliah/<Matkul>/summary/`
   d. Buat **soal berbobot** (minimal 10, tiga level) di `Kuliah/<Matkul>/latihan-soal/`
   e. Update `00-overview.md` matkul tersebut (tambah link ke semua file baru)
   f. Update `00-index.md` kalau perlu
   g. Pastikan semua wikilink terpasang sesuai aturan section 3c

### 4b. Saat User Minta Latihan Soal (Tambahan)

1. Baca rangkuman, summary, dan jurnal yang relevan di Obsidian terlebih dahulu.
2. Buat/update file soal di `Kuliah/<Matkul>/latihan-soal/`.
3. **Wajib minimal 10 soal** dengan distribusi 3 level sesuai section 3b.
4. Sesuaikan tipe soal dengan nature matkul dan permintaan user.
5. WAJIB sertakan jawaban, pembahasan, dan rubrik (untuk level Olimpiade).
6. Update link di `00-overview.md`.

### 4c. Saat User Minta Review/Evaluasi

1. Baca SEMUA rangkuman, summary, dan jurnal yang relevan di matkul tersebut.
2. Buat/update file evaluasi di `Kuliah/<Matkul>/evaluasi/`.
3. Evaluasi harus komprehensif: ringkasan semua topik, poin kunci, rumus/konsep penting,
   dan kumpulan soal latihan terpilih (dengan distribusi level).
4. Update link di `00-overview.md`.

### 4d. Saat User Minta Catatan Tanpa Menyebut Matkul

Tanya dulu mata kuliah mana. Jangan menebak dari konten.

---

## 5. Aturan Umum

- **Bahasa**: Indonesia. Istilah teknis dalam bahasa Inggris diperbolehkan dan dianjurkan.
- **Jangan baca/tulis ke `Projects/`** dari workflow kuliah ini. `Projects/` diatur oleh
  rules global yang terpisah.
- **Jangan buat folder matkul baru** tanpa konfirmasi user — hanya gunakan 8 matkul
  yang terdaftar di section 1.
- **Konsistensi penamaan**: selalu gunakan slug dari tabel section 1, jangan membuat variasi.
- **Atomicity**: satu rangkuman = satu topik. Satu summary = satu topik. Satu file jurnal =
  satu topik. Satu file soal = satu topik. Jangan menggabungkan beberapa topik berbeda
  ke dalam satu file (kecuali memang satu topik besar yang dibahas beberapa minggu).
- **Jurnal wajib di-search**: Saat membuat file jurnal, agent WAJIB menggunakan `search_web`
  untuk mencari jurnal akademik yang relevan. Minimal 5 jurnal, rentang 5 tahun terakhir.
  SELALU cantumkan DOI/URL dan ringkasan relevansi.
- **Sumber tambahan**: Saat membuat rangkuman dan summary Tier 2, agent dianjurkan mencari
  informasi tambahan dari web (search_web) untuk memperkaya materi — tapi SELALU cantumkan
  sumber di section Referensi.
- **Tidak perlu identity check** (section 0 rules global) untuk workflow kuliah.
  Workflow kuliah tidak menggunakan `project_slug`. Cukup identifikasi mata kuliah.
- **Handoff**: Workflow kuliah **tidak** menggunakan `handoff.md`. Catatan Tier 1 dan Tier 2
  sudah self-documenting. Kalau ada sesi yang terputus, lanjutkan dari file terakhir.

---

## 6. Bootstrap Awal

Saat pertama kali workspace ini digunakan, agent HARUS:

1. Buat semua 8 subfolder matkul di workspace lokal (kalau belum ada).
2. Buat struktur `Kuliah/` di Obsidian vault:
   - `Kuliah/00-index.md`
   - 8 folder matkul, masing-masing berisi:
     - `00-overview.md`
     - `rangkuman/` (folder kosong)
     - `summary/` (folder kosong)
     - `jurnal/` (folder kosong)
     - `latihan-soal/` (folder kosong)
     - `evaluasi/` (folder kosong)
3. Isi `00-index.md` dengan MOC awal (daftar 8 matkul + wikilink).
4. Isi masing-masing `00-overview.md` dengan template dasar.

Bootstrap hanya dijalankan **sekali**. Kalau struktur sudah ada, skip.
