# BAB I. Pendahuluan

## 1.1 Gambaran Layanan Inti

Kuliah Kerja Nyata (KKN) Tematik "Membangun Desa" adalah program pengabdian kepada masyarakat. Dalam program ini mahasiswa tinggal dan bekerja di desa selama periode tertentu untuk membantu menyelesaikan persoalan lokal, seperti pemberdayaan ekonomi, literasi, kesehatan, lingkungan, dan transformasi digital desa. Pelaksanaannya melibatkan banyak pihak: mahasiswa peserta, Dosen Pembimbing Lapangan (DPL), panitia KKN di tingkat universitas, dan pemerintah desa sebagai mitra.

Saat ini kegiatan administrasi dan akademik KKN umumnya masih tersebar di beberapa kanal, seperti formulir manual, spreadsheet, grup pesan instan, dan dokumen cetak. Kondisi ini menimbulkan beberapa masalah:

1. Data peserta dan penempatan sulit disinkronkan.
2. Bimbingan DPL sulit dipantau.
3. Laporan kegiatan terlambat atau tidak seragam.
4. Penilaian akhir kurang transparan dan sulit ditelusuri.

Karena itu diperlukan subsistem **Assignment & Assessment** sebagai inti layanan KKN Tematik. Subsistem ini mengelola alur dari pendaftaran peserta, penempatan ke desa, bimbingan dosen, pelaporan kegiatan, hingga penilaian akhir dalam satu layanan terintegrasi.

Alur layanan inti dapat diringkas sebagai berikut:

| Tahap | Fungsi Utama | Aktor Utama |
|---|---|---|
| Pendaftaran | Mahasiswa mendaftar dan diverifikasi kelayakannya | Mahasiswa, Panitia |
| Penempatan desa | Peserta dikelompokkan dan ditempatkan di desa berdasarkan kuota dan kriteria | Panitia, Pemerintah Desa |
| Bimbingan dosen | Penugasan DPL, jadwal, dan catatan bimbingan | DPL, Mahasiswa |
| Laporan kegiatan | Pengumpulan logbook, laporan mingguan, dan laporan akhir | Mahasiswa, DPL |
| Penilaian | Penilaian oleh DPL dan mitra desa, serta rekapitulasi nilai akhir | DPL, Panitia, Pemerintah Desa |

Dokumen ini berfokus pada **analisis dan rancangan arsitektur** subsistem tersebut. Pembahasannya mencakup konteks dan keputusan arsitektur (BAB II) serta karakteristik dan atribut kualitas (BAB III).

## 1.2 Ruang Lingkup (Kasus Penggunaan)

Ruang lingkup dibatasi pada lima kasus penggunaan utama yang mewakili seluruh siklus layanan:

| Kode | Kasus Penggunaan | Deskripsi | Aktor |
|---|---|---|---|
| UC-01 | Pendaftaran peserta KKN | Mahasiswa mengisi data diri, memilih tema atau preferensi desa, dan mengunggah berkas persyaratan. Panitia memverifikasi kelayakan, misalnya jumlah SKS dan status akademik. | Mahasiswa, Panitia |
| UC-02 | Penempatan desa | Panitia membentuk kelompok dan menetapkan lokasi desa berdasarkan kuota, tema, dan keseimbangan prodi. Hasilnya dipublikasikan dan dikonfirmasi oleh desa. | Panitia, Pemerintah Desa, Mahasiswa |
| UC-03 | Bimbingan dosen | DPL ditugaskan ke kelompok. Mahasiswa dan DPL menjadwalkan bimbingan, mencatat hasilnya, dan memberi umpan balik. | DPL, Mahasiswa |
| UC-04 | Pengumpulan laporan kegiatan | Mahasiswa mengunggah logbook harian atau mingguan, dokumentasi, dan laporan akhir. DPL meninjau dan menyetujui atau meminta revisi. | Mahasiswa, DPL |
| UC-05 | Penilaian dan rekapitulasi nilai | DPL dan pemerintah desa memberi nilai berdasarkan rubrik. Sistem menghitung nilai akhir dan menyerahkannya ke panitia. | DPL, Pemerintah Desa, Panitia |

**Batasan ruang lingkup.** Dokumen ini tidak membahas:

- implementasi kode program;
- sistem keuangan atau pembiayaan KKN;
- logistik transportasi dan akomodasi;
- integrasi mendalam dengan sistem akademik lain di luar kebutuhan penyerahan nilai, yang diasumsikan hanya melalui antarmuka (*interface*) terdefinisi.

## 1.3 Sumber Data

Analisis dan rancangan arsitektur disusun berdasarkan data dan informasi dari beberapa sumber berikut:

| No | Sumber Data | Jenis | Digunakan untuk |
|---|---|---|---|
| 1 | Buku pedoman KKN dan dokumen kebijakan KKN universitas | Dokumen resmi | Alur layanan, aturan kelayakan, komponen dan bobot penilaian |
| 2 | Formulir, rubrik penilaian, dan format laporan KKN yang digunakan | Dokumen operasional | Kebutuhan data, atribut entitas, dan format keluaran |
| 3 | Wawancara atau diskusi dengan pemangku kepentingan (mahasiswa pernah ikut KKN, DPL, panitia) | Data primer | Kebutuhan, kendala, dan prioritas pemangku kepentingan (peta *power/interest*) |
| 4 | Observasi proses KKN yang berjalan (kanal komunikasi, spreadsheet, dan alur manual) | Data primer | Kondisi sistem saat ini dan masalah yang ingin diselesaikan |
| 5 | Literatur dan standar (arsitektur perangkat lunak, atribut kualitas, ISO/IEC 25010) | Data sekunder | Dasar keputusan arsitektur dan atribut kualitas |

Seluruh sumber dicatat dalam daftar pustaka berformat IEEE, dan bukti pengumpulan data (misalnya tangkapan layar dokumen atau catatan wawancara) dilampirkan pada bagian Lampiran.

<!--
CATATAN PENYESUAIAN (hapus sebelum dikumpulkan):
- Sesuaikan butir 1-4 pada tabel 1.3 dengan sumber yang benar-benar digunakan kelompok
  (nama dokumen pedoman KKN UMI, jumlah dan peran narasumber wawancara).
- Jika belum ada wawancara/observasi, ganti dengan data yang sudah ada agar tidak mengklaim data yang tidak dikumpulkan.
- Jika kasus penggunaan ditambah atau dikurangi, ubah UC-01 s.d. UC-05 dan sesuaikan Bab II dan III.
-->
<!-- Gambaran subsistem dan layanan inti yang ditugaskan, ruang lingkup, dan sumber data. -->
<!-- Penanggung jawab: [nama] -->

<!-- Pengalaman pengguna, informasi publik, wawancara responden. Tanpa identitas pribadi. -->
