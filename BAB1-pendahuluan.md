# BAB I. Pendahuluan

## 1.1 Gambaran Layanan Inti

Kuliah Kerja Nyata (KKN) merupakan mata kuliah wajib dan kegiatan intrakurikuler di Universitas Muslim Indonesia (UMI) yang memadukan pelaksanaan Tri Dharma Perguruan Tinggi dengan pengalaman belajar dan bekerja mahasiswa dalam pemberdayaan masyarakat [1]. Penyelenggaranya adalah Lembaga Pengabdian kepada Masyarakat (LPkM) UMI. UMI menyelenggarakan tiga jenis KKN: KKN Reguler/Tematik, KKN Program Pemberdayaan Masyarakat Desa (PPMD), dan KKN Profesi [1]. Dokumen ini berfokus pada **KKN Tematik (Membangun Desa)**, yaitu bentuk pengabdian ketika mahasiswa hidup di tengah masyarakat selama satu bulan, bersama warga mengidentifikasi persoalan desa, dan menyusun program kerja sesuai tema dan keahlian masing-masing [1].

Skala layanan ini cukup besar. Pada KKN Angkatan 72, tercatat 3.179 mahasiswa peserta, dan 1.035 di antaranya mengikuti KKN Tematik di tujuh desa di Kabupaten Maros [2]. Pelaksanaan KKN Tematik Angkatan 77 diakhiri dengan penarikan mahasiswa dari Kabupaten Bantaeng pada Agustus 2026 [3]. Dengan ratusan hingga ribuan peserta per angkatan, pengelolaan tanpa dukungan sistem terpadu rawan menimbulkan kendala administratif.

Berdasarkan Panduan KKN UMI 2024, sejumlah proses inti masih bertumpu pada dokumen dan tahapan manual [1]:

1. **Pendaftaran.** Mahasiswa mengambil formulir pembayaran di LPkM, membayar ke BMT UMI, lalu menyerahkan satu lembar bukti pembayaran ke LPkM untuk memperoleh berkas pendaftaran. Kelayakan juga bergantung pada beberapa bukti terpisah, yaitu pemrograman KKN di Simpadu, kelulusan minimal 100 SKS, kelulusan Pencerahan Qalbu, dan surat keterangan tes baca Al-Qur'an dari WD IV.
2. **Penempatan.** Lokasi ditentukan LPkM dan dikukuhkan melalui SK Rektor. DPL menerima salinan SK dan melakukan absensi sebelum keberangkatan.
3. **Bimbingan.** DPL memantau presensi harian dan lembar rencana kegiatan, mengevaluasi disiplin dan kerja sama, serta menyampaikan laporan singkat kepada LPkM. Semua ini dilakukan secara mingguan dan sebagian besar berbasis tanda tangan.
4. **Laporan.** Laporan harian, laporan perorangan, dan laporan akhir dibuat dalam 3 rangkap, disahkan dengan tanda tangan dan stempel, lalu diserahkan paling lambat dua minggu setelah penarikan.
5. **Penilaian.** Nilai disusun dari tiga komponen oleh pihak berbeda dan diserahkan DPL ke LPkM dalam bentuk daftar nilai bertanda tangan.

Panduan yang sama juga menggolongkan pemalsuan tanda tangan dan stempel sebagai pelanggaran berat [1]. Hal ini menunjukkan perlunya mekanisme verifikasi yang dapat ditelusuri.

Karena itu diperlukan subsistem **Assignment & Assessment** yang mengintegrasikan lima layanan inti KKN Tematik UMI: pendaftaran, penempatan desa, bimbingan dosen (DPL), laporan kegiatan, dan penilaian. Ringkasan alurnya:

| Tahap | Fungsi Utama | Aktor Utama |
|---|---|---|
| Pendaftaran | Verifikasi persyaratan peserta dan pembayaran biaya KKN | Mahasiswa, Fakultas, LPkM, BMT UMI |
| Penempatan desa | Pembagian lokasi, kelompok, dan DPL, serta penetapan melalui SK Rektor | LPkM, Rektor, Pemda/Pemerintah Desa |
| Bimbingan DPL | Presensi, rencana kegiatan, monitoring mingguan, dan evaluasi | DPL, Mahasiswa, Koordinator Desa/Kecamatan |
| Laporan kegiatan | Laporan harian, program kerja, laporan perorangan, laporan kelompok, dan laporan akhir | Mahasiswa, DPL, Kepala Desa, LPkM |
| Penilaian | Penilaian oleh Pemda/instansi dan DPL, penetapan kelulusan, dan nilai akhir | Pemda/Kepala Desa, DPL, LPkM |

Dokumen ini berfokus pada **analisis dan rancangan arsitektur** subsistem tersebut, yaitu konteks dan keputusan arsitektur (BAB II) serta karakteristik dan atribut kualitas (BAB III).

## 1.2 Ruang Lingkup (Kasus Penggunaan)

Ruang lingkup dibatasi pada lima kasus penggunaan utama yang mengikuti siklus KKN Tematik UMI:

| Kode | Kasus Penggunaan | Deskripsi (mengacu pada Panduan KKN UMI 2024) | Aktor |
|---|---|---|---|
| UC-01 | Pendaftaran peserta KKN | Mahasiswa diverifikasi terhadap syarat: terdaftar dan memprogram KKN di Simpadu, lulus minimal 100 SKS, lulus Pencerahan Qalbu, lulus tes baca Al-Qur'an (surat keterangan WD IV), dan telah membayar biaya KKN. Setelah itu LPkM menerbitkan berkas pendaftaran. | Mahasiswa, Fakultas, LPkM, BMT UMI |
| UC-02 | Penempatan desa | LPkM menentukan lokasi berdasarkan jumlah peserta dan hasil observasi lokasi. Mahasiswa dikelompokkan per desa/kecamatan, DPL ditugaskan, dan penempatan ditetapkan melalui SK Rektor. Koordinator kecamatan dan desa dipilih. | LPkM, Rektor, DPL, Pemda/Pemerintah Desa |
| UC-03 | Bimbingan dosen (DPL) | DPL mendampingi pada fase sosialisasi (minggu I), memantau presensi harian dan lembar rencana kegiatan (minggu I-IV), mengevaluasi disiplin dan kerja sama, serta menyampaikan laporan singkat ke LPkM. | DPL, Mahasiswa |
| UC-04 | Pelaporan kegiatan | Mahasiswa menyusun program kerja dan laporan harian, laporan perorangan, dan laporan akhir kelompok. Laporan disetujui DPL, disahkan Kepala Desa, dan diserahkan ke LPkM paling lambat 2 minggu setelah penarikan. | Mahasiswa, DPL, Kepala Desa, LPkM |
| UC-05 | Penilaian dan penetapan kelulusan | Komponen nilai: pelaksanaan program kerja (35%, dinilai Pemda/instansi), laporan akhir (35%, dinilai DPL), dan sikap (30%). Kelulusan mensyaratkan pembekalan 100%, kehadiran minimal 80%, dan laporan yang telah disetorkan serta disahkan. Nilai dikonversi ke huruf dan mutu. | Pemda/Kepala Desa, DPL, LPkM |

**Batasan ruang lingkup.** Dokumen ini tidak membahas:

- KKN PPMD dan KKN Profesi, kecuali bila istilah atau proses yang sama dipakai bersama;
- pelaksanaan teknis program kerja di lapangan (misalnya isi penyuluhan);
- pembekalan dan Pencerahan Qalbu sebagai kegiatan pembelajaran, kecuali statusnya sebagai data syarat dan kehadiran;
- sistem keuangan secara menyeluruh, termasuk operasional BMT UMI dan pengelolaan *living cost*, selain status pembayaran sebagai syarat pendaftaran;
- implementasi kode program.

Integrasi dengan sistem lain, yaitu Simpadu dan BMT UMI, diasumsikan melalui antarmuka (*interface*) terdefinisi.

## 1.3 Sumber Data

Analisis dan rancangan arsitektur disusun berdasarkan sumber berikut:

| No | Sumber Data | Jenis | Digunakan untuk | Rujukan |
|---|---|---|---|---|
| 1 | Panduan KKN UMI 2024 (LPkM UMI): persyaratan peserta, tahap pelaksanaan, tugas DPL, sistematika laporan, bobot penilaian, tata tertib dan sanksi | Dokumen resmi | Alur layanan, aturan bisnis (syarat, bobot nilai, batas waktu laporan), peran aktor | [1] |
| 2 | Berita resmi LPkM UMI dan pemberitaan KKN Tematik UMI (Angkatan 72 dan 77) | Dokumen sekunder | Gambaran skala peserta, lokasi, dan siklus pelepasan-penarikan | [2], [3] |
| 3 | Contoh format dalam lampiran panduan: laporan program kerja perorangan, rencana program kerja, sampul dan lembar pengesahan | Dokumen operasional | Kebutuhan data dan format keluaran | [1] |
| 4 | Wawancara/diskusi dengan pemangku kepentingan (misalnya alumni peserta KKN, DPL, staf LPkM) | Data primer | Kendala nyata, prioritas pemangku kepentingan, peta *power/interest* | *(diisi kelompok)* |
| 5 | Literatur arsitektur perangkat lunak dan standar kualitas (misalnya ISO/IEC 25010) | Data sekunder | Dasar keputusan arsitektur dan atribut kualitas | *(diisi kelompok)* |

Seluruh sumber dicatat dalam daftar pustaka berformat IEEE, dan bukti pengumpulan data dilampirkan pada bagian Lampiran.

---

### Referensi Bab I (IEEE, bagian dari Daftar Pustaka)

[1] Lembaga Pengabdian kepada Masyarakat UMI, *Panduan Kuliah Kerja Nyata (KKN) UMI 2024*, Universitas Muslim Indonesia, Makassar, Indonesia, Nov. 2024. [Online]. Available: https://lpkm.umi.ac.id/wp-content/uploads/2026/05/2024_PANDUAN-KKN-UMI.pdf

[2] ANTARA, "Bupati Maros sambut program KKN Tematik UMI," *ANTARA News*. [Online]. Available: https://m.antaranews.com/amp/berita/3837786/bupati-maros-sambut-program-kkn-tematik-umi (diakses 31 Okt. 2026).

[3] LPkM UMI, "Penarikan KKN Tematik Angkatan 77 UMI berlangsung sukses, seluruh peserta tiba dengan selamat di Makassar," Makassar, Indonesia, 6 Agu. 2026. [Online]. Available: https://lpkm.umi.ac.id/penarikan-kkn-tematik-angkatan-77-umi-berlangsung-sukses-seluruh-peserta-tiba-dengan-selamat-di-makassar

<!--
CATATAN PENYESUAIAN (hapus sebelum dikumpulkan):
- Butir 4 dan 5 pada tabel 1.3 harus diisi sesuai data yang benar-benar dikumpulkan kelompok. Jika belum ada wawancara, hapus butir 4.
- Panduan yang dirujuk adalah edisi 2024. Cek apakah ada edisi terbaru di situs LPkM UMI (lpkm.umi.ac.id).
- Panduan tidak memakai istilah "Membangun Desa". Panduan menyebut "KKN Reguler/Tematik". Pertahankan "Membangun Desa" karena merupakan judul tugas.
- Tambahkan tanggal terbit pada referensi [2] jika ditemukan di halaman beritanya.
-->
<!-- Gambaran subsistem dan layanan inti yang ditugaskan, ruang lingkup, dan sumber data. -->
<!-- Penanggung jawab: [nama] -->

<!-- Pengalaman pengguna, informasi publik, wawancara responden. Tanpa identitas pribadi. -->
