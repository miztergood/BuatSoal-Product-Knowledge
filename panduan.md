# BUATSOAL.ONLINE — PUBLIC PRODUCT KNOWLEDGE BASE

> Dokumen ini adalah sumber kebenaran (source of truth) publik tentang produk BuatSoal.Online: apa yang produk ini lakukan, fitur apa saja yang tersedia, untuk siapa, dan cara membicarakannya secara akurat.
>
> Disusun berdasarkan implementasi produk per **Oktober 2026**. Fitur, harga, dan promo dapat berubah — halaman resmi di [buatsoal.online](https://buatsoal.online) selalu menjadi sumber terkini.

---

## 1. Tentang BuatSoal.Online

**BuatSoal.Online** adalah aplikasi web berbasis AI untuk membuat soal ujian dan menyelenggarakan ujian online (CBT).

Fungsi utama:

1. **Membuat naskah soal otomatis dengan AI** — guru cukup menentukan topik, jenis soal, tingkat kesulitan, dan level kognitif; AI menyusun naskah soal lengkap dengan kunci jawaban.
2. **Mengubah soal menjadi ujian online (CBT)** — soal dipublikasikan sebagai ujian yang bisa dikerjakan siswa lewat link, dengan timer, pengacakan, dan anti-cheat.
3. **Memantau dan menganalisis hasil** — guru melihat nilai, detail jawaban, analisis kompetensi per materi, dan analisis butir soal, lalu mengunduh rekap ke Excel.

Siapa yang menggunakannya:

- **Guru** (SD, SMP, SMA, SMK, dan madrasah MI/MTs/MA) sebagai pengguna utama
- **Sekolah / lembaga pendidikan** untuk penyelenggaraan ujian
- **Pembuat soal / penyusun latihan** (bimbel, pengajar privat, penyusun materi latihan)
- **Agency / reseller** yang mendistribusikan akun premium ke banyak guru

Konteks penggunaan: dibuat untuk kebutuhan ujian harian, PTS/PAS, asesmen nasional (TKA/AKM), olimpiade, hingga latihan TOEFL dan SNBT. Aplikasi berbasis web — tidak perlu instalasi, bisa dibuka dari laptop, tablet, atau HP.

---

## 2. Masalah yang Dibantu Diselesaikan

Setiap manfaat di bawah diturunkan langsung dari fitur yang tersedia.

| Masalah | Fitur | Kemampuan | Manfaat |
|---|---|---|---|
| Membuat soal manual makan waktu berjam-jam | Generator soal AI | Naskah soal lengkap dihasilkan dari topik | Waktu penyusunan soal jauh lebih singkat |
| Menyusun soal dari kisi-kisi itu repetitif | Mode Kisi-Kisi | Upload file kisi-kisi, soal dibuat per baris kisi-kisi | Naskah soal mengikuti kisi-kisi tanpa mengetik ulang |
| Butuh soal dengan level kognitif tertentu | Pilihan Bloom C1–C6 | Soal diarahkan ke level kognitif yang dipilih | Soal sesuai taksonomi HOTS/lower-order yang dibutuhkan |
| Menggelar ujian online itu rumit | Publikasi CBT | Soal jadi ujian online dengan link, timer, dan kode akses | Siswa mengerjakan dari mana saja, guru tidak perlu cetak |
| Sulit mencegah kecurangan ujian daring | Anti-cheat | Fullscreen, deteksi pindah tab, auto-submit, kode akses | Pelanggaran tercatat; kecurangan berkurang |
| Koreksi dan rekap nilai manual | Dashboard hasil | Nilai, jumlah benar, dan status otomatis tercatat | Nilai tersaji otomatis begitu siswa submit |
| Tidak tahu materi mana yang lemah | Analisis kompetensi & butir soal | Skor per materi dan per soal + rekomendasi | Guru tahu materi apa yang perlu diulang |
| Internet siswa tidak stabil saat ujian | Offline Mode | Jawaban tersimpan lokal dan tersinkron otomatis | Ujian tetap berjalan meski koneksi terputus |
| Kebutuhan akun untuk banyak guru | Agency | Beli kuota slot, aktivasi akun guru lewat dashboard | Lembaga/reseller mengelola banyak akun dari satu tempat |

---

## 3. Target Pengguna

Berdasarkan fitur yang benar-benar tersedia:

1. **Guru sekolah & madrasah** — pengguna utama; membuat soal, menggelar ujian, menganalisis hasil.
2. **Sekolah / yayasan** — standarisasi pembuatan soal dan penyelenggaraan ujian serentak dengan proctoring.
3. **KKG / MGMP / komunitas guru** — berbagi latihan soal dan memantau capaian anggota.
4. **Bimbel / pengajar privat / penyusun latihan** — membuat latihan TOEFL, SNBT, olimpiade, dan ujian try-out.
5. **Agency / reseller** — membeli kuota akun premium dan mendistribusikannya ke guru lain lewat dashboard agency.

Peran dalam sistem: **siswa/peserta** (tanpa akun, cukup link ujian), **guru/pembuat soal** (akun berlangganan), **agency owner** (akun + paket agency), dan **admin platform** (pengelolaan internal).

---

## 4. Pembuatan Soal

Halaman generator (`/app`) adalah pusat aplikasi. Naskah diisi identitas: nama sekolah, nama guru, tahun ajaran, mata pelajaran, dan fase/jenjang.

### 4.1 Mode Topik

- **Fungsi:** membuat soal langsung dari topik yang diketik.
- **Input:** topik/materi (contoh: "Fotosintesis", "Persamaan Kuadrat"), jenis soal, tingkat kesulitan, level kognitif, jumlah soal.
- **Output:** naskah soal lengkap dengan kunci jawaban.
- **Opsi:**
  - Tingkat kesulitan **Mudah / Sedang / Sulit** — jumlah soal diatur per tingkat.
  - Level kognitif **Bloom C1–C6** (Mengingat sampai Mencipta) — bisa dipilih lebih dari satu.
  - **Multi-bagian:** satu naskah bisa terdiri dari beberapa bagian dengan konfigurasi berbeda (topik/jenis soal/kesulitan berbeda per bagian).
  - **Mode ruang lingkup:** satu bagian bisa berisi beberapa lingkup materi, masing-masing dengan pengaturan kesulitan dan level kognitifnya sendiri.
- **Catatan:** tersedia untuk semua paket berbayar.

### 4.2 Mode Kisi-Kisi

- **Fungsi:** membuat soal berdasarkan dokumen kisi-kisi yang sudah dimiliki guru.
- **Input:** file kisi-kisi format **PDF atau Word (.docx)** — di-upload, sistem membaca tabelnya otomatis.
- **Output:** soal per baris kisi-kisi (materi/indikator), lengkap dengan kisi-kisi yang bisa diedit.
- **Opsi:** guru memilih baris kisi-kisi mana yang dijadikan soal dan mengatur jumlah soal per baris.
- **Catatan:** tersedia untuk semua paket berbayar.

### 4.3 Preset Struktur Soal

- **Fungsi:** menyimpan konfigurasi bagian soal sebagai preset bernama.
- **Manfaat:** struktur ujian yang sering dipakai (misal format ujian akhir sekolah) tidak perlu disusun ulang — tinggal muat preset.

### 4.4 Pemeriksaan Naskah

- Sebelum ekspor, aplikasi menampilkan **peringatan kualitas naskah** (misalnya kelengkapan butir soal) agar naskah yang keluar lebih rapi.

---

## 5. Jenis Soal

Enam jenis soal inti yang didukung generator:

| Jenis Soal | Penjelasan |
|---|---|
| **Pilihan Ganda** | PG biasa dengan 3, 4, atau 5 opsi (A–E), dilengkapi kunci jawaban |
| **Pilihan Ganda Kompleks** | PG dengan lebih dari satu jawaban benar |
| **Benar / Salah** | Pernyataan dinilai benar atau salah |
| **Menjodohkan** | Premis dan respon dipasangkan; urutan diacak otomatis |
| **Isian Singkat** | Jawaban singkat diketik langsung |
| **Uraian / Essai** | Jawaban panjang, dilengkapi kunci dan rubrik penilaian |

Jenis tambahan yang tersedia pada mode TKA/AKM dan olimpiade madrasah:

- **PG Kategori** — mengelompokkan pernyataan ke kategori (dinilai sebagian benar).
- **PG MCMA** (Multiple Choice Multiple Answer) — PG multi-jawab versi TKA.

Penilaian **nilai sebagian (partial scoring)** diterapkan untuk Menjodohkan, PG Kategori, dan PG MCMA — siswa mendapat nilai proporsional untuk jawaban yang benar sebagian, bukan nol atau penuh.

---

## 6. Mode Khusus

Selain mode reguler, tersedia mode khusus dengan karakteristik masing-masing. Ketersediaan mode mengikuti paket (lihat bagian 4 dan FAQ).

### OSN (Olimpiade Sains Nasional)
- **Tujuan:** latihan soal bergaya olimpiade sains.
- **Cocok untuk:** guru pembina OSN SD/SMP/SMA, siswa yang hendak lomba.
- **Karakteristik:** pilihan bidang (Matematika, IPA, IPS, Fisika, dll per jenjang), tahap **OSN-K / OSN-P / Nasional**, soal HOTS dan problem solving. Sistem menyusun outline materi terlebih dahulu untuk direview sebelum soal dibuat.

### OLIMPABA (Olimpiade PAI & Bahasa Arab)
- **Tujuan:** latihan soal olimpiade PAI dan Bahasa Arab.
- **Cocok untuk:** guru dan siswa madrasah MI/MTs/MA.
- **Karakteristik:** pilihan cabang sesuai jenjang (Al-Qur'an Hadis, Akidah Akhlak, Fikih, SKI, Sejarah Kebudayaan Islam, Bahasa Arab).

### OMI (Olimpiade Madrasah)
- **Tujuan:** latihan soal olimpiade madrasah.
- **Cocok untuk:** guru dan siswa MI/MTs/MA.
- **Karakteristik:** mapel terintegrasi seperti Matematika Terintegrasi, IPAS/IPA-IPS Terintegrasi, hingga mapel pilihan tingkat MA.

### TKA (Tes Kemampuan Akademik)
- **Tujuan:** latihan soal bergaya TKA sesuai kerangka asesmen Kemdikbud.
- **Cocok untuk:** guru SD, SMP, SMA/SMK yang menyiapkan siswa menghadapi TKA.
- **Karakteristik:** jenjang SD/SMP/SMA/SMK, tipe soal PG Biasa, PG Kategori, dan PG MCMA, tersedia pilihan topik drilling per mapel.

### AKM (Asesmen Kompetensi Minimum)
- **Tujuan:** latihan literasi membaca dan numerasi bergaya AKM.
- **Cocok untuk:** guru yang menyiapkan siswa menghadapi asesmen nasional berbasis komputer.
- **Karakteristik:** berbasis stimulus, Level 1–6, sesuai framework Pusmenjar.

### TOEFL
- **Tujuan:** latihan TOEFL PBT.
- **Cocok untuk:** guru bahasa Inggris, siswa/peserta yang menyiapkan TOEFL.
- **Karakteristik:** section Structure, Written Expression, dan Reading Comprehension; output berbahasa Inggris.

### SNBT (Seleksi Nasional Berbasis Tes)
- **Tujuan:** latihan UTBK-SNBT.
- **Cocok untuk:** guru SMA, bimbel, dan peserta seleksi PTN.
- **Karakteristik:** subtes Penalaran Umum (PU, PPU, PBM, PK), Literasi Bahasa Indonesia & Inggris, dan Penalaran Matematika; format PG 5 opsi.

> Mode **ANBK** tampil di antarmuka dengan status "Soon" — belum tersedia.

---

## 7. Fitur Setelah Soal Dibuat

Panel hasil terbagi menjadi tab: **Naskah Soal**, **Kunci & Pembahasan**, **Kisi-Kisi**, dan **Kartu Soal**.

- **Edit per soal dengan AI** — pilih nomor soal, tulis instruksi perubahan (misal "ganti konteks soal ke transaksi jual-beli"), AI merevisi soal tersebut.
- **Generate ulang semua** — membuat ulang seluruh naskah dari awal dengan konfigurasi yang sama.
- **Generate Pembahasan** — menambahkan pembahasan untuk setiap soal pada tab kunci.
- **Generate Kisi-Kisi** — membuat kisi-kisi otomatis dari soal yang sudah ada; kisi-kisi juga bisa diedit manual.
- **Kartu Soal** — format kartu soal resmi per nomor (indikator, materi, level kognitif). Tersedia untuk sebagian besar mode; tidak untuk OSN, TOEFL, SNBT, dan mode Umum.
- **Gambar AI** — menandai soal yang butuh ilustrasi; AI menyusun prompt dan menghasilkan gambar edukatif (diagram/ilustrasi) untuk soal terpilih.
- **Workspace** — naskah yang sudah dibuat tersimpan di workspace dan bisa dimuat kembali. Kapasitas penyimpanan mengikuti paket.

---

## 8. Export dan Publikasi

| Output | Penjelasan |
|---|---|
| **Word (.docx)** | Ekspor sesuai tab aktif: Naskah Soal, Kunci & Pembahasan, Kisi-Kisi (format landscape), atau Kartu Soal. Siap cetak. |
| **PDF** | Naskah diekspor langsung ke PDF dengan pratinjau A4 siap cetak. |
| **Google Forms** | Soal dikonversi menjadi Google Form (untuk paket tertentu — lihat FAQ). Memerlukan penyiapan satu kali yang dipandu di dalam aplikasi. |
| **Ujian Online (CBT)** | Soal dipublikasikan sebagai ujian online yang dikerjakan siswa lewat link (lihat bagian 9). |
| **Kop Surat Sekolah** | Logo/nama sekolah di-upload sekali dan muncul sebagai kop pada hasil cetak/ekspor. |

---

## 9. CBT / Ujian Online

Soal yang sudah dibuat dapat dipublikasikan menjadi ujian online. Siswa **tidak perlu akun** — cukup membuka link dari guru.

### 9.1 Pengaturan Ujian (oleh guru)

- **Durasi:** 1–300 menit, dengan timer hitung mundur.
- **Kode akses:** kode singkat yang wajib dimasukkan siswa sebelum mulai — guru bisa mengubahnya.
- **Jadwal:** waktu mulai dan waktu berakhir ujian, dengan pilihan zona waktu **WIB / WITA / WIT**.
- **Acak soal** dan **acak opsi** — urutan berbeda untuk setiap siswa.
- **Anti-cheat:** fullscreen wajib, deteksi keluar layar/pindah tab, batas pelanggaran (melewati batas → ujian dikumpulkan otomatis). Dua mode operasi: **Mode Kelas** (guru membuka kunci langsung dari dashboard, cocok untuk lab komputer) dan **Mode Daring** (guru membuat PIN sementara untuk siswa di rumah).
- **Tampilkan skor ke siswa** dan **tampilkan analisis ke siswa** — opsional.

### 9.2 Membagikan Ujian

- **Link ujian** — format `buatsoal.online/v2/quiz/...` (versi terbaru) dan versi V1; tinggal salin dan sebar via WhatsApp/LMS.
- **QR Code** — bisa ditampilkan dan di-screenshot untuk discan siswa.
- **Kode akses** dibagikan terpisah agar orang luar tidak bisa masuk.
- Ujian bisa **diaktifkan/dinonaktifkan** kapan saja — ujian nonaktif tidak bisa dikerjakan meski link tersebar.

### 9.3 Pengalaman Siswa

- Mengisi **nama lengkap dan kelas**, lalu kode akses jika ada.
- **Timer** menghitung mundur; waktu tersinkron dengan server agar adil.
- **Panel navigasi soal** dengan filter: Semua / Belum dijawab / Ragu-ragu / Sudah dijawab; soal bisa **ditandai ragu-ragu**.
- **Layar review** sebelum submit menampilkan jumlah soal yang belum dijawab dan ditandai.
- Jawaban **tersimpan otomatis** setiap kali diisi.
- **Offline Mode:** jika koneksi terputus, jawaban tetap tersimpan di perangkat dan **tersinkronisasi otomatis** saat internet kembali. Ada indikator status koneksi dan penyimpanan.
- **Pemulihan sesi:** jika browser tertutup/ter-refresh, siswa dapat melanjutkan percobaan yang sama.
- Jika batas pelanggaran terlampaui, ujian terkunci dan dikumpulkan otomatis; guru dapat membukanya (lihat bagian 10).
- Saat waktu habis, ujian **dikumpulkan otomatis**; siswa juga bisa submit manual lewat layar konfirmasi.

### 9.4 Kelola Ujian (setelah dipublikasikan)

Guru dapat: mengubah judul/durasi/jadwal/zona waktu, **mengedit soal** di dalam ujian yang sudah tayang, mengaktifkan/nonaktifkan ujian, **mereset siswa** agar bisa mengerjakan ulang, menghapus respons (satuan atau massal), dan **menghitung ulang nilai**.

---

## 10. Monitoring dan Proctoring

Halaman **Proktor** memantau ujian yang sedang berlangsung secara real-time.

- **Daftar peserta langsung** dengan status: Sedang Mengerjakan, Dijeda, Selesai, Dipaksa Submit, Kedaluwarsa.
- **Hitungan pelanggaran** per siswa; klik untuk melihat **riwayat pelanggaran** dengan waktu kejadian (misal "Keluar Layar / Pindah Tab").
- **Force Submit** — mengumpulkan ujian siswa tertentu secara paksa.
- **Buka kunci siswa** — pada Mode Kelas guru membuka kunci langsung; pada Mode Daring guru membuat **PIN 4 digit berbatas waktu** yang diberikan ke siswa.
- **Kunci nilai** — hasil siswa dikunci agar tidak berubah saat proses review kecurangan.

---

## 11. Hasil dan Analisis

Begitu siswa submit, hasil tercatat otomatis di dashboard guru.

### Yang terlihat per siswa
- **Nilai**, jumlah benar dari total soal, status (mengerjakan / selesai / auto-submit / terkunci), waktu submit, dan jumlah pelanggaran.
- **Detail jawaban** — matriks per nomor: jawaban siswa, kunci, status benar/salah/sebagian.
- **Rapor siswa** yang bisa dicetak — laporan hasil ujian per siswa.

### Analisis kelas
- **Statistik kelas:** rata-rata, nilai tertinggi/terendah, rekap per kelas.
- **Analisis kompetensi:** skor per materi/indikator (mengikuti kisi-kisi), menunjukkan materi yang dikuasai dan yang perlu diulang.
- **Analisis butir soal:** persentase benar/salah/kosong per soal, label tingkat kesulitan soal (Mudah/Sedang/Sulit), dan **distribusi jawaban pengecoh** untuk soal pilihan ganda — berguna untuk menilai kualitas butir soal.

### Export laporan
Unduhan **Excel** berisi beberapa sheet: **Rekap Nilai**, **Analisis Kompetensi**, **Rekomendasi** (materi dengan skor di bawah ambang ditandai "pelajari kembali"), **Jawaban Per Nomor** (matriks siswa × nomor), **Kunci Jawaban**, dan **Detail Jawaban**.

---

## 12. Agency

Fitur **Agency** menjawab kebutuhan lembaga, konsultan pendidikan, komunitas guru, dan reseller yang ingin menyediakan akun premium BuatSoal untuk banyak guru sekaligus.

### Konsep
- Agency owner membeli **paket kuota (slot)**. Setiap slot dapat diaktifkan menjadi **satu akun premium berlangganan 1 tahun**.
- **1 slot otomatis terpakai untuk akun agency owner sendiri**; sisanya didistribusikan.
- Agency owner **menentukan sendiri harga jual** ke guru lain — selisih dari harga beli menjadi keuntungannya.
- Kuota **tidak memiliki kedaluwarsa** — bisa dijual sesuai ritme.

### Dua jenis lisensi
- **Agency Pro** — semua slot mengaktifkan akun **Pro**.
- **Agency Max** — slot bersifat **fleksibel**: saat mengundang guru, owner memilih mengaktifkan akun **Max atau Pro** (sama-sama memotong 1 slot). Jika kuota Pro habis, invite akun Pro otomatis memakai kuota Max. Sebaliknya, Agency Pro tidak bisa mengaktifkan akun Max.

### Alur kerja Agency Owner
1. Beli paket lewat halaman **`/paketagency`** (presentasi + kalkulator simulasi profit) atau **`/pricing-agency`** (halaman pemesanan). Pemesanan dan aktivasi dikonfirmasi melalui WhatsApp admin.
2. Buka **dashboard agency** (`/agency`): melihat sisa kuota Pro & Max, member aktif, dan invite pending.
3. **Mengundang guru:** masukkan email guru, pilih tier akun (Pro/Max), kirim invite. Sistem memotong 1 kuota dan menghasilkan link undangan.
4. Guru membuka link undangan, mendaftar/masuk dengan **email yang sama**, dan akunnya langsung aktif 1 tahun.
5. Pantau daftar invite (bisa salin ulang link) dan daftar member (mulai, kedaluwarsa, sisa hari) — semuanya terbarui real-time.

> ⚠️ 1 invite = 1 kuota terpakai **permanen**, walaupun guru tidak pernah mendaftar.

### Paket & harga
- **Harga retail akun** yang menjadi acuan margin: Pro **Rp 149.000/tahun**, Max **Rp 249.000/tahun** (sesuai halaman utama buatsoal.online).
- **Paket agency** tersedia dalam tingkat slot **Starter (10), Advance (30), dan Master (60)** untuk masing-masing lisensi Pro dan Max. Harga paket agency dapat berubah dan tersedia promo berkala — **selalu rujuk harga terkini di `/paketagency` dan `/pricing-agency`**, jangan menghardcode angka di materi promosi.
- Halaman `/paketagency` juga menyebutkan bonus untuk agency owner (materi pendukung penjualan, grup support, panduan berjualan) — rujuk halaman tersebut untuk daftar bonus terkini.

---

## 13. Store / Produk Digital

Fitur **Store** memungkinkan pengguna menjual produk digital berupa **dokumen soal** (bank soal, paket latihan) di etalase publik. *(Fitur masih dalam tahap pengembangan aktif.)*

- **Siapa:** semua pengguna dengan akun dapat membuka toko sendiri (`/app/store-management`).
- **Produk:** listing dokumen soal dengan kategori, deskripsi, dan harga; sebuah listing juga bisa ditautkan ke kuis yang sudah dipublikasikan.
- **Etalase publik (`/store`):** marketplace dengan pencarian dan kategori; setiap penjual punya halaman toko (`/store/nama-toko`) dan halaman produk.
- **Alur pembelian:** pembeli memesan → membayar **transfer bank manual ke rekening penjual** → mengonfirmasi via **WhatsApp** ke penjual (sudah disediakan tombol dengan ringkasan pesanan) → penjual menyetujui → pembeli mengunduh file.
- **Lacak pesanan (`/lacak-pesanan`):** pembeli memeriksa status pesanan dengan email + nomor invoice, dan mengunduh file yang sudah disetujui.
- Penjual dapat mengelola **kupon diskon** dan memantau **daftar pesanan** dari dashboard tokonya.

---

## 14. Use Cases

### Guru ingin membuat soal ujian harian dengan cepat
Buka generator → mode Topik → isi topik, jenis soal, kesulitan, level kognitif → generate → review → ekspor Word/PDF untuk dicetak.

### Guru sudah punya kisi-kisi dari sekolah
Mode Kisi-Kisi → upload file kisi-kisi (PDF/Word) → centang baris yang mau disoalkan → generate. Naskah otomatis mengikuti kisi-kisi, dan kisi-kisinya ikut terekspor.

### Guru ingin ujian online tanpa kertas
Susun soal → publikasikan sebagai ujian online → atur durasi, kode akses, jadwal, pengacakan → bagikan link/QR ke siswa → pantau lewat halaman Proktor saat ujian berlangsung.

### Sekolah menggelar ujian serentak di lab komputer
Aktifkan anti-cheat Mode Kelas + fullscreen → siswa mengerjakan di lab → guru memantau realtime dari halaman Proktor dan membuka kunci bila ada gangguan → nilai otomatis terkumpul.

### Guru ingin tahu materi mana yang harus diulang
Pastikan soal memiliki kisi-kisi → setelah ujian, buka analisis kompetensi dan analisis butir soal → unduh Excel untuk dibahas di rapat MGMP/KKG.

### Pengajar bimbel menyiapkan try-out TOEFL/SNBT/OSN
Gunakan mode khusus (TOEFL, SNBT, OSN) → generate latihan → publikasikan sebagai ujian online berbayar/private dengan kode akses.

### Lembaga ingin menyediakan akun untuk 25 guru
Beli paket agency sesuai jumlah slot → undang guru satu per satu lewat dashboard agency → semua akun aktif tanpa perlu saling berbagi login.

### Guru ingin mendapatkan penghasilan tambahan
Ambil lisensi agency → jual slot akun premium ke sesama guru dengan harga retail — hitung dulu estimasi profitnya di kalkulator di `/paketagency`. Atau jual bank soal digital lewat Store.

---

## 15. FAQ

**Q: Apakah siswa perlu membuat akun untuk ikut ujian?**
> Tidak. Siswa cukup membuka link ujian dari guru (dan memasukkan kode akses jika guru mengaktifkannya).

**Q: Apakah soal yang dibuat AI bisa diedit?**
> Ya. Setiap soal bisa direvisi dengan menulis instruksi ke AI, dan seluruh naskah bisa dibuat ulang sebelum dipakai.

**Q: Apakah ujian bisa dikerjakan online dari rumah?**
> Ya. Ujian dipublikasikan sebagai CBT dengan link; cocok untuk mode daring maupun di lab komputer (Mode Kelas).

**Q: Apakah ada mode offline jika internet siswa terputus?**
> Ya, pada ujian versi terbaru (V2). Jawaban tersimpan di perangkat siswa dan otomatis tersinkronisasi saat koneksi kembali.

**Q: Bagaimana guru melihat hasil ujian?**
> Nilai, jumlah benar, dan status setiap siswa tampil otomatis di dashboard. Detail jawaban per siswa, analisis kompetensi, dan analisis butir soal juga tersedia, plus ekspor Excel.

**Q: Format ekspor soal apa saja yang tersedia?**
> Word (.docx), PDF, Google Forms (paket tertentu), dan publikasi langsung menjadi ujian online (CBT).

**Q: AI yang dipakai apa, dan apakah saya perlu API key sendiri?**
> Aplikasi menggunakan AI Google Gemini. Untuk penggunaan tanpa batas, pengguna dapat memasukkan API key Gemini miliknya sendiri lewat menu pengaturan di dalam aplikasi.

**Q: Apa bedanya paket Pro dan Max?**
> Pro mencakup semua mode pembuatan soal dan ekspor. Max menambahkan fitur pembeda: **ujian online (CBT)**, **Import Soal dari PDF/Word**, dan **ekspor Google Forms**.

**Q: Apa bedanya Agency Pro dan Agency Max?**
> Agency Pro hanya bisa mengaktifkan akun Pro untuk member. Agency Max bisa mengaktifkan akun Max **dan** akun Pro (slot fleksibel), sehingga potensi margin per akunnya lebih besar.

**Q: Apakah kuota slot agency punya masa kedaluwarsa?**
> Tidak. Kuota tersimpan sampai dipakai. Namun langganan setiap member yang diaktifkan berlaku 1 tahun.

**Q: Bisakah menjual soal yang saya buat?**
> Ya, lewat fitur Store: daftarkan toko, unggah listing dokumen soal, dan pembeli membayar lewat transfer bank yang dikonfirmasi via WhatsApp.

**Q: Apakah aplikasi perlu di-install?**
> Tidak. BuatSoal.Online berbasis web dan bisa dibuka dari browser di laptop, tablet, atau HP.

---

## 16. Terminologi Produk

| Istilah | Penjelasan |
|---|---|
| **BuatSoal.Online** | Nama produk: generator soal ujian berbasis AI + platform CBT. |
| **CBT** | Computer-Based Test — ujian online yang dikerjakan lewat browser. |
| **Workspace** | Penyimpanan naskah soal milik pengguna; naskah bisa dimuat kembali. Kapasitas mengikuti paket. |
| **Kisi-Kisi** | Tabel materi/indikator ujian; bisa di-upload sebagai dasar pembuatan soal atau dibuat otomatis. |
| **Kartu Soal** | Format dokumen resmi per nomor soal berisi indikator, materi, dan level kognitif. |
| **Pembahasan** | Penjelasan jawaban untuk setiap soal, dibuat otomatis. |
| **Level Kognitif / Bloom** | Taksonomi Bloom C1 (Mengingat) sampai C6 (Mencipta) yang menentukan kedalaman soal. |
| **Fase** | Level jenjang Kurikulum Merdeka, Fase A (kelas 1–2) sampai F (kelas 11–12). |
| **Preset** | Konfigurasi struktur bagian soal yang disimpan untuk dipakai ulang. |
| **Mode Topik** | Membuat soal langsung dari topik yang diketik. |
| **Mode Kisi-Kisi** | Membuat soal dari file kisi-kisi (PDF/Word) yang di-upload. |
| **TKA** | Tes Kemampuan Akademik — asesmen bergaya Kemdikbud untuk SD/SMP/SMA/SMK. |
| **AKM** | Asesmen Kompetensi Minimum — literasi & numerasi berbasis stimulus. |
| **ANBK** | Asesmen Nasional Berbasis Komputer — mode terkait sedang dikembangkan (Soon). |
| **OSN** | Olimpiade Sains Nasional. |
| **OLIMPABA** | Olimpiade PAI & Bahasa Arab untuk madrasah. |
| **OMI** | Olimpiade Madrasah (mapel terintegrasi MI/MTs/MA). |
| **TOEFL (PBT)** | Tes bahasa Inggris berbasis kertas; aplikasi membuat latihan 3 section-nya. |
| **SNBT** | Seleksi Nasional Berbasis Tes (UTBK) untuk masuk PTN. |
| **Kop Surat** | Identitas sekolah (logo/nama) yang muncul di hasil cetak/ekspor. |
| **Kode Akses / PIN** | Kode yang wajib dimasukkan siswa sebelum ujian dimulai. |
| **Mode Kelas / Mode Daring** | Dua mode anti-cheat: pengawasan langsung di lab vs ujian dari rumah dengan PIN sementara. |
| **Offline Mode** | Kemampuan ujian V2 menyimpan jawaban di perangkat saat offline lalu menyinkronkannya otomatis. |
| **Attempt** | Satu kali kesempatan siswa mengerjakan ujian; bisa direset oleh guru agar bisa mengulang. |
| **Proctoring** | Pemantauan ujian berlangsung: status peserta, pelanggaran, force submit, unlock. |
| **Analisis Butir Soal** | Statistik per soal: persentase benar/salah/kosong, tingkat kesulitan, distribusi pengecoh. |
| **Pengecoh** | Opsi jawaban salah yang sengaja mirip benar; distribusinya dianalisis untuk menilai kualitas soal. |
| **Partial Scoring** | Penilaian sebagian untuk soal seperti Menjodohkan dan PG multi-jawab. |
| **Agency** | Skema reseller: membeli slot kuota lalu mengaktifkan akun premium untuk guru lain. |
| **Agency Owner** | Pemilik lisensi agency yang mengelola slot dan member. |
| **Member** | Guru yang akunnya diaktifkan lewat undangan agency; berlangganan 1 tahun. |
| **Slot / Kuota** | Satuan hak aktivasi satu akun premium dalam paket agency. |
| **Store** | Etalase publik untuk menjual produk digital berupa dokumen soal. |

---

## 17. Copywriting Knowledge

Bagian ini memandu AI (dan manusia) menyusun copy promosi yang akurat.

### 17.1 Core Value

> **BuatSoal.Online membuat guru lebih cepat membuat soal ujian dengan AI, langsung bisa menggelarnya sebagai ujian online, dan mendapatkan analisis hasil otomatis — semuanya dalam satu aplikasi web tanpa instalasi.**

Tiga pilar: **Buat** (generator soal AI dengan banyak mode dan jenis soal) → **Gelar** (CBT dengan keamanan dan offline mode) → **Analisis** (nilai, kompetensi, butir soal, Excel).

### 17.2 Key Benefits

**Efisiensi**
- Naskah soal lengkap terbentuk dari satu input topik.
- Kisi-kisi tinggal di-upload, tidak perlu mengetik ulang.
- Struktur ujian rutin bisa disimpan sebagai preset.
- Nilai dan rekap otomatis — tidak perlu koreksi manual.

**Pembuatan soal**
- 6 jenis soal inti + tipe khusus TKA/AKM (PG Kategori, PG MCMA) dengan nilai sebagian.
- Kontrol kedalaman soal lewat tingkat kesulitan dan Bloom C1–C6.
- Multi-bagian untuk naskah ujian campuran.
- Soal bisa diedit per nomor lewat instruksi AI sebelum dipakai.

**Pelaksanaan ujian**
- Ujian online dengan link dan QR — siswa tidak perlu akun.
- Timer, jadwal, kode akses, dan zona waktu WIB/WITA/WIT.
- Offline mode menjaga ujian tetap aman saat koneksi terputus.

**Monitoring**
- Pantau peserta real-time saat ujian berlangsung.
- Pelanggaran fullscreen/pindah tab tercatat otomatis.
- Force submit dan buka kunci tersedia dari dashboard guru.

**Analisis hasil**
- Nilai, detail jawaban, dan rapor per siswa.
- Analisis kompetensi per materi + rekomendasi materi yang perlu diulang.
- Analisis butir soal untuk menilai kualitas soal dan pengecoh.
- Rekap lengkap siap unduh ke Excel.

**Fleksibilitas**
- Mode untuk hampir semua kebutuhan: harian, TKA, AKM, OSN, OLIMPABA, OMI, TOEFL, SNBT.
- Multi perangkat: laptop, tablet, HP — berbasis browser.
- Ekspor Word/PDF/Google Form, atau langsung online.

### 17.3 Key Selling Points

- AI membuat naskah soal lengkap dengan kunci jawaban dalam hitungan menit.
- Mendukung 6 jenis soal, termasuk tipe khusus asesmen (PG Kategori, PG MCMA) dengan penilaian nilai sebagian.
- Soal bisa dibuat dari kisi-kisi (PDF/Word) tanpa mengetik ulang.
- Setiap soal bisa diedit dengan instruksi AI sebelum dipakai.
- Ada mode khusus: OSN, OLIMPABA, OMI, TKA, AKM, TOEFL, SNBT.
- Soal bisa langsung dipublikasikan menjadi ujian online (CBT) dengan link dan QR code.
- Ujian dilengkapi timer, kode akses, pengacakan soal/opsi, dan anti-cheat.
- Siswa tanpa akun bisa ikut ujian; jawaban tersimpan otomatis.
- Offline mode: jawaban aman saat koneksi terputus dan tersinkron otomatis.
- Proctoring real-time: status peserta, catatan pelanggaran, force submit, buka kunci.
- Hasil ujian otomatis: nilai, detail jawaban, analisis kompetensi, analisis butir soal.
- Laporan bisa diekspor ke Excel dengan beberapa sheet siap pakai.
- Ekspor ke Word dan PDF siap cetak, lengkap dengan kop sekolah.
- Fitur agency untuk lembaga/reseller: kelola banyak akun guru dari satu dashboard.
- Store untuk menjual produk digital berupa bank soal.

### 17.4 Pain Points (yang dijawab produk)

- "Membuat 30 soal butuh berhari-hari." → generator AI + multi-bagian.
- "Kisi-kisi dari sekolah harus diketik ulang jadi soal." → mode Kisi-Kisi upload.
- "Saya tidak paham cara menyusun soal HOTS." → pilihan level Bloom C1–C6 dan mode khusus.
- "Ujian kertas ribet: cetak, bagi, koreksi, rekap." → publikasi CBT + nilai otomatis.
- "Siswa suka nyontek saat ujian online." → kode akses, acak soal/opsi, fullscreen, pelanggaran tercatat.
- "Internet sekolah/ siswa sering putus." → offline mode dengan sinkronisasi otomatis.
- "Koreksi esai dan rekap nilai makan waktu akhir semester." → nilai otomatis + ekspor Excel.
- "Tidak tahu materi mana yang lemah per kelas." → analisis kompetensi dan butir soal.
- "Lembaga saya butuh banyak akun, capek kelola satu-satu." → dashboard agency dengan invite email.
- "Penghasilan guru pas-pasan." → program agency reseller (jual slot akun premium).

### 17.5 Audience Angles

**Guru (sekolah & madrasah)**
- Hemat waktu menyusun naskah soal harian, PTS/PAS.
- Soal langsung sesuai kisi-kisi dan Kurikulum Merdeka (Fase A–F).
- Analisis hasil membuat pembahasan di kelas lebih terarah.

**Sekolah / yayasan**
- Standarisasi kualitas soal antar guru dan antar mapel.
- Ujian serentak lintas kelas dengan monitoring dan rekap otomatis.
- Arsip naskah rapi di workspace setiap guru.

**KKG / MGMP / komunitas guru**
- Membuat bank latihan soal bersama, dibagikan sebagai CBT.
- Data analisis butir soal sebagai bahan diskusi kualitas soal.

**Bimbel / pengajar privat / penyusun latihan**
- Paket latihan TOEFL, SNBT, OSN, TKA, AKM siap dipakai try-out.
- CBT dengan kode akses cocok untuk kelas online.

**Agency / reseller**
- Bisnis sampingan tanpa ganggu mengajar: beli slot, jual akun premium.
- Slot fleksibel (Agency Max) — aktifkan akun Max atau Pro sesuai kebutuhan pembeli.
- Dashboard mandiri: aktivasi member via email, kuota tanpa kedaluwarsa.
- Kalkulator profit tersedia di halaman paket agency.

**Guru yang ingin jual produk digital**
- Bank soal bisa dijual lewat Store dengan pembayaran transfer + konfirmasi WhatsApp.

---

## 18. Product Claim Rules

Aturan wajib saat menyusun klaim promosi tentang BuatSoal.Online:

1. **Jangan mengklaim fitur yang tidak tersedia.** Rujuk dokumen ini dan halaman resmi. Contoh: mode ANBK masih "Soon" — jangan promosikan sebagai fitur aktif.
2. **Jangan mengklaim angka performa tanpa sumber.** (misal "hemat 90% waktu", "10.000 guru") kecuali angka tersebut tampil resmi di halaman perusahaan.
3. **Jangan membuat testimonial palsu.** Testimoni hanya boleh dikutip dari yang dipublikasikan resmi.
4. **Hindari klaim superlatif** ("terbaik", "nomor 1", "paling cepat") tanpa bukti.
5. **Jangan mengarang harga atau diskon.** Harga retail akun (Pro Rp 149.000/tahun, Max Rp 249.000/tahun) tampil resmi di halaman utama. Harga paket agency dinamis — selalu rujuk `/paketagency` atau `/pricing-agency` untuk angka terkini.
6. **Jangan membuat deadline promo.** Promo harian (bila ada) hanya tampil di halaman resmi.
7. **Jangan membuat scarcity palsu** (stok terbatas, slot tersisa X) kecuali benar-benar ditampilkan di halaman resmi.
8. **Jangan mengklaim integrasi yang tidak tersedia.** Integrasi resmi yang ada: ekspor Google Forms (paket tertentu) dan pembayaran/aktivasi manual via WhatsApp admin. Jangan klaim integrasi LMS, WhatsApp bot, atau payment gateway otomatis.
9. **Jangan mengklaim keamanan absolut.** Sebutkan fitur anti-cheat yang ada (fullscreen, deteksi pindah tab, kode akses, catatan pelanggaran) tanpa janji "mustahil curang".
10. **Jangan melebih-lebihkan manfaat.** Gunakan pola FITUR → KEMAMPUAN → MANFAAT yang masuk akal, seperti contoh di bagian 2.

---

*Dokumen publik — boleh dibagikan dan dikutip dengan mencantumkan sumber: buatsoal.online.*
