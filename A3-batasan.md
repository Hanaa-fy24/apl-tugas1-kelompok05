# A3. Batasan Sistem

Penanggung jawab: [ Ashfy Nur Raihana ]

Batasan sistem adalah kondisi atau ketentuan yang tidak dapat diubah oleh tim perancang dan harus diterima sebagai pembatas dalam merancang arsitektur. Batasan pada bagian ini dikelompokkan ke dalam tiga kategori: **teknologi**, **bisnis**, dan **operasional**. Batasan diidentifikasi dari hasil wawancara dengan lima responden (R1 sampai R5) dan dari alur layanan KKN Tematik. Untuk setiap batasan dijelaskan dampaknya terhadap sistem dan arsitektur.

### A3.1 Batasan Teknologi

**Tabel 2.3. Batasan teknologi**

| ID | Batasan | Penjelasan | Dampak pada Sistem dan Arsitektur | Sumber |
|---|---|---|---|---|
| T1 | Integrasi dengan sistem akademik kampus belum dipastikan | Staf IT menyatakan bahwa integrasi perlu dipastikan lebih dulu kepada pengelola sistem. Jika diperlukan, pengembangannya harus menyesuaikan kebutuhan data dan kebijakan kampus, termasuk format data, hak akses, dan mekanisme pertukaran informasi | Sistem harus dapat berjalan mandiri tanpa bergantung pada sistem akademik. Integrasi dirancang sebagai antarmuka terpisah yang dapat ditambahkan kemudian, dengan ekspor data manual sebagai alternatif. Format dan mekanisme pertukaran baru ditetapkan setelah ada konfirmasi | R5 |
| T2 | Rancangan harus sesuai kesiapan infrastruktur kampus | Kesiapan infrastruktur, keamanan data, kestabilan jaringan, dan kapasitas penyimpanan perlu diperiksa sebelum sistem dikembangkan agar rancangan sesuai dengan kemampuan kampus | Arsitektur dipilih sesederhana mungkin dan tidak mengandalkan infrastruktur yang belum tentu tersedia. Keputusan yang bergantung pada infrastruktur (penyimpanan, penyebaran, pencadangan) dicatat sebagai asumsi dan diverifikasi sebelum implementasi | R5 |
| T3 | Koneksi jaringan dapat terputus saat data disimpan | Dosen dan staf IT menekankan bahwa pengguna harus mengetahui berhasil atau tidaknya penyimpanan laporan dan nilai ketika terjadi gangguan atau koneksi terputus | Penyimpanan laporan dan nilai harus bersifat utuh (berhasil seluruhnya atau tidak sama sekali), dan sistem wajib menampilkan status penyimpanan. Antarmuka perlu memungkinkan pengiriman ulang tanpa menyebabkan data ganda atau tersimpan tidak lengkap | R3, R5 |

### A3.2 Batasan Bisnis

**Tabel 2.4. Batasan bisnis**

| ID | Batasan | Penjelasan | Dampak pada Sistem dan Arsitektur | Sumber |
|---|---|---|---|---|
| B1 | Penempatan, pembagian kelompok, dan penetapan DPL ditentukan kampus; perubahan memerlukan persetujuan pihak berwenang | Mahasiswa mengikuti penempatan yang ditetapkan kampus, DPL ditetapkan berdasarkan kebijakan pengelola, dan perubahan penempatan atau kelompok harus disetujui pihak berwenang | Sistem tidak menentukan kebijakan penempatan sendiri, melainkan menjalankan dan mencatat keputusan pengelola. Perlu alur persetujuan untuk perubahan beserta riwayatnya, dan data mahasiswa, kelompok, serta DPL harus diperbarui mengikuti penetapan terbaru | R1, R3, R4 |
| B2 | Persyaratan pendaftaran ditetapkan kampus dan sebagian berkas dikumpulkan secara fisik melalui fakultas | Persyaratan meliputi formulir, tabulasi nilai, bukti pembayaran, dan bukti hafalan Juz 30. Pendaftaran berjalan secara kombinasi: formulir *online* melalui tautan panitia dan berkas melalui bagian akademik fakultas | Sistem harus mendukung alur campuran *online* dan fisik, termasuk pencatatan status verifikasi berkas. Daftar persyaratan dikelola sebagai konfigurasi karena ketentuan dapat berubah mengikuti kebijakan kampus | R1, R2, R4 |
| B3 | Komponen penilaian ditetapkan pengelola dan hasil disampaikan melalui saluran resmi | Penilaian mengacu pada komponen dan kriteria yang ditetapkan pengelola, dicatat agar dapat diperiksa kembali, dan hasilnya diterima mahasiswa melalui pihak LPKM | Rubrik dan bobot tidak ditanam di kode melainkan dikonfigurasi. Nilai harus tercatat beserta riwayat perubahannya, dan publikasi hasil mengikuti saluran resmi yang ditetapkan pengelola, bukan langsung oleh sistem tanpa persetujuan | R1, R3, R4 |

### A3.3 Batasan Operasional

**Tabel 2.5. Batasan operasional**

| ID | Batasan | Penjelasan | Dampak pada Sistem dan Arsitektur | Sumber |
|---|---|---|---|---|
| O1 | Beban penggunaan melonjak pada periode tertentu | Jumlah pengguna meningkat saat pendaftaran dan pengumpulan laporan sehingga kinerja sistem perlu diperhatikan dan diuji | Arsitektur harus tahan beban pada periode puncak. Perlu pengujian beban sebelum digunakan, serta pemisahan pekerjaan yang tidak mendesak agar tidak mengganggu layanan utama | R5 |
| O2 | Administrasi harus tetap berjalan saat sistem terganggu | Pengelola memerlukan prosedur alternatif agar kegiatan administrasi penting dapat dilanjutkan, dan pencadangan data perlu direncanakan serta pemulihannya diuji | Sistem perlu pencadangan terjadwal dan mekanisme pemulihan yang teruji. Data penting (pendaftaran, penempatan, nilai) harus dapat diekspor agar proses manual tetap dapat berjalan sementara | R4, R5 |
| O3 | Sistem menggantikan kanal informasi yang sudah berjalan | Informasi saat ini disampaikan melalui grup KKN, dosen pembimbing, dan media komunikasi panitia, sehingga mahasiswa harus mencari ulang informasi pada pesan lama. Pengelola dan DPL juga belum memiliki satu sumber terpusat | Sistem harus menjadi sumber informasi resmi tunggal (jadwal, kelompok, penempatan, DPL, laporan, nilai) dengan antarmuka yang mudah dipahami berbagai peran. Transisi dari kanal lama perlu bertahap dan disertai sosialisasi | R1, R2 |

### A3.4 Ringkasan Batasan

| Kategori | Jumlah | Batasan yang Paling Memengaruhi Arsitektur |
|---|---|---|
| Teknologi | 3 | T1 (integrasi belum pasti) dan T3 (penyimpanan utuh saat koneksi terputus) |
| Bisnis | 3 | B1 (persetujuan perubahan penempatan) dan B3 (rubrik dan nilai bersifat konfigurasi dan tercatat) |
| Operasional | 3 | O1 (beban puncak) dan O2 (pencadangan dan prosedur alternatif) |

Batasan di atas menjadi masukan bagi pendorong arsitektur pada bagian berikutnya dan membatasi pilihan struktur sistem. Batasan teknologi T1 dan T2 masih bergantung pada konfirmasi pihak kampus dan harus diverifikasi sebelum keputusan arsitektur yang terkait ditetapkan.

<!--
CATATAN PENYESUAIAN (hapus sebelum dikumpulkan):
- Setiap batasan didasarkan pada pernyataan responden (kolom Sumber). Batasan yang tidak disebut responden (misalnya anggaran,
  jumlah tim pengelola, atau teknologi tertentu yang wajib dipakai) sengaja tidak dimasukkan agar tidak mengarang fakta.
  Tambahkan bila ada dokumen resmi atau informasi dari dosen yang mendukung.
- Minimal 2 batasan per kategori sudah terpenuhi (3 per kategori).
- Istilah "LPKM" mengikuti ucapan responden (R1); tuliskan kepanjangannya sesuai dokumen resmi UMI.
- Jika T1 dikonfirmasi (misalnya integrasi wajib atau tidak ada), ubah penjelasan dan dampaknya.
-->
<!-- Yang diminta: Minimal 2 batasan untuk tiap kategori (teknologi, bisnis, operasional), disertai dampaknya. -->
<!-- Hapus komentar ini setelah bagian selesai. -->

