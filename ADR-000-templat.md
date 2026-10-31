# A5 – Architecture Decision Record (ADR) 

Penanggung jawab: [ Eka Putri Aulia ]

## ADR-001: Penerapan Arsitektur Modular untuk Integrasi Layanan KKN

- **Status:** Diterima (Accepted)
- **Tanggal:** 31 Oktober 2026
- **Pengambil keputusan:** Anggota Kelompok II-5 (Ashfy Nur Raihana, Eka Putri Aulia, Nabila Sinta Salsabila, Siti Mutiah Nurhaliza)

### Context

Subsistem Assignment & Assessment memiliki lima proses utama yang saling berkaitan, yaitu pendaftaran peserta, penempatan desa, bimbingan dosen, pengumpulan laporan kegiatan, serta penilaian dan rekapitulasi nilai akhir.

Berdasarkan hasil wawancara dengan mahasiswa peserta KKN (R1), proses pendaftaran masih dilakukan melalui kombinasi online dan offline. Pendaftaran online menggunakan tautan yang dibagikan panitia, sedangkan berkas persyaratan dikumpulkan secara langsung melalui bagian akademik fakultas. Informasi mengenai kelompok, lokasi KKN, dan dosen pembimbing disampaikan melalui grup KKN.

Responden juga menyampaikan bahwa informasi pendaftaran, jadwal kegiatan, agenda penting, dan penempatan mahasiswa perlu tersedia dalam satu sistem. Selain itu, pembagian kelompok dan penentuan lokasi KKN perlu dibuat lebih transparan dan mudah dipantau.

Kondisi tersebut menunjukkan perlunya sistem yang dapat menghubungkan seluruh proses layanan KKN agar informasi tidak tersebar di berbagai media dan setiap tahapan dapat dikelola secara lebih terstruktur.

Kebutuhan tersebut berkaitan dengan ASR-01 (Integrasi Layanan KKN) dan ASR-03 (Integritas Data) pada A4, yang menekankan pentingnya keterhubungan proses serta konsistensi data pada setiap tahapan layanan KKN.

### Decision

Kami akan menerapkan arsitektur modular, yaitu pendekatan perancangan sistem dengan membagi layanan ke dalam beberapa modul berdasarkan fungsi masing-masing.

Modul yang dirancang meliputi:

1. **Modul Pendaftaran:** Mengelola data mahasiswa, formulir pendaftaran, unggahan persyaratan, dan verifikasi kelayakan peserta.

2. **Modul Penempatan Desa:** Mengelola pembentukan kelompok, penentuan lokasi desa, kuota, serta informasi penempatan mahasiswa.

3. **Modul Bimbingan Dosen:** Mengelola penugasan DPL, jadwal bimbingan, catatan konsultasi, dan umpan balik.

4. **Modul Laporan Kegiatan:** Mengelola pengumpulan logbook, dokumentasi, laporan mingguan, dan laporan akhir.

5. **Modul Penilaian:** Mengelola penilaian oleh DPL dan pemerintah desa, perhitungan nilai akhir, serta rekapitulasi nilai untuk panitia.

Setiap modul memiliki tanggung jawab masing-masing, tetapi tetap saling terhubung melalui data dan proses yang dibutuhkan oleh modul lainnya.

### Consequences

Penerapan arsitektur modular memiliki beberapa dampak positif dan negatif yang perlu dipertimbangkan.

**Dampak Positif:**

- Setiap proses layanan KKN dapat dikelola berdasarkan fungsi masing-masing.
- Hubungan antara pendaftaran, penempatan, bimbingan, laporan, dan penilaian menjadi lebih terstruktur.
- Pengembangan dan perbaikan sistem dapat dilakukan pada modul tertentu tanpa harus mengubah seluruh bagian sistem.
- Mempermudah pemeliharaan serta pengembangan fitur apabila terdapat perubahan kebutuhan layanan KKN.

**Dampak Negatif:**

- Membutuhkan perencanaan hubungan antar modul agar tidak terjadi ketidaksesuaian data.
- Pengembangan sistem membutuhkan koordinasi yang baik karena setiap modul saling berkaitan.
- Kesalahan dalam komunikasi atau pertukaran data antar modul dapat mengganggu proses layanan lainnya.
- Perancangan awal membutuhkan waktu lebih banyak untuk menentukan pembagian tanggung jawab setiap modul.

### Compliance

Keputusan ini diterapkan dengan memastikan setiap modul memiliki fungsi dan tanggung jawab yang jelas sesuai dengan ruang lingkup layanan KKN.

Pengujian dilakukan terhadap setiap modul untuk memastikan proses pendaftaran, penempatan desa, bimbingan dosen, pengumpulan laporan, dan penilaian dapat berjalan sesuai fungsinya.

Selain itu, dilakukan pengujian integrasi untuk memastikan data dari satu modul dapat digunakan oleh modul lainnya secara tepat. Contohnya, data mahasiswa yang telah diverifikasi pada modul pendaftaran harus dapat digunakan dalam proses penempatan desa dan pembentukan kelompok.

---

## ADR-002: Penerapan Role-Based Access Control (RBAC) untuk Keamanan Data

- **Status:** Diterima (Accepted)
- **Tanggal:** 31 Oktober 2026
- **Pengambil keputusan:** Anggota Kelompok II-5 (Ashfy Nur Raihana, Eka Putri Aulia, Nabila Sinta Salsabila, Siti Mutiah Nurhaliza)

### Context

Subsistem Assignment & Assessment melibatkan beberapa aktor, yaitu mahasiswa, Dosen Pembimbing Lapangan (DPL), panitia KKN, dan pemerintah desa. Setiap aktor memiliki tanggung jawab serta kebutuhan akses informasi yang berbeda.

Berdasarkan hasil wawancara R1, data pribadi mahasiswa, dokumen administrasi, dan nilai akademik merupakan informasi yang perlu dilindungi. Mahasiswa hanya seharusnya dapat mengakses informasi yang berkaitan dengan dirinya, sedangkan dosen pembimbing dan pengelola memperoleh akses sesuai dengan tanggung jawab masing-masing.

Hal tersebut menunjukkan bahwa sistem membutuhkan mekanisme pengaturan hak akses agar informasi penting tidak dapat dilihat atau diubah oleh pihak yang tidak memiliki kewenangan.

Kebutuhan tersebut berkaitan dengan ASR-02 (Keamanan dan Hak Akses Pengguna) pada A4, yang menekankan perlindungan data serta pembatasan akses berdasarkan peran dan kewenangan pengguna.

### Decision

Kami akan menerapkan Role-Based Access Control (RBAC), yaitu mekanisme pengaturan hak akses berdasarkan peran pengguna.

Pembagian hak akses dirancang sebagai berikut:

1. **Mahasiswa:** Dapat mengelola data pendaftaran miliknya, melihat informasi kelompok dan penempatan desa, mengakses informasi DPL, mengikuti proses bimbingan, mengunggah laporan kegiatan, serta melihat hasil penilaian miliknya sendiri.

2. **Dosen Pembimbing Lapangan (DPL):** Dapat melihat data mahasiswa yang menjadi tanggung jawabnya, mengelola jadwal dan catatan bimbingan, memeriksa laporan kegiatan, memberikan umpan balik, serta mengelola penilaian sesuai kewenangannya.

3. **Panitia KKN:** Dapat mengelola data pendaftaran, memverifikasi persyaratan, mengatur penempatan desa dan kelompok, serta mengelola administrasi dan rekapitulasi nilai akhir.

4. **Pemerintah Desa:** Dapat mengakses informasi kelompok yang ditempatkan di wilayahnya serta memberikan konfirmasi dan penilaian sesuai dengan kewenangan yang diberikan.

Selain pembagian hak akses, sistem juga akan menggunakan autentikasi untuk memastikan identitas pengguna serta pencatatan aktivitas untuk membantu menelusuri perubahan pada data penting.

### Consequences

Penerapan RBAC memiliki beberapa dampak positif dan negatif sebagai berikut.

**Dampak Positif:**

- Melindungi data pribadi mahasiswa, dokumen administrasi, dan hasil penilaian.
- Setiap pengguna hanya dapat mengakses fitur sesuai dengan peran dan kewenangannya.
- Mengurangi risiko penyalahgunaan atau perubahan data oleh pihak yang tidak berwenang.
- Mempermudah pengelolaan hak akses karena pengaturannya dilakukan berdasarkan peran pengguna.
- Membantu meningkatkan keamanan dan kepercayaan pengguna terhadap sistem.

**Dampak Negatif:**

- Membutuhkan pengelolaan akun dan hak akses yang lebih terstruktur.
- Pengembangan sistem membutuhkan proses tambahan untuk mengatur setiap peran pengguna.
- Kesalahan dalam pengaturan hak akses dapat menyebabkan pengguna tidak dapat mengakses fitur yang sebenarnya dibutuhkan.
- Pengelola perlu melakukan pemeriksaan dan pemeliharaan hak akses secara berkala apabila terdapat perubahan tugas atau tanggung jawab pengguna.

### Compliance

Keputusan ini diterapkan dengan memastikan setiap peran pengguna memiliki hak akses yang sesuai dengan tanggung jawabnya.

Pengujian dilakukan menggunakan beberapa akun dengan peran berbeda untuk memastikan mahasiswa, DPL, panitia KKN, dan pemerintah desa hanya dapat mengakses fitur sesuai dengan kewenangannya.

Sebagai contoh, dilakukan pengujian untuk memastikan mahasiswa tidak dapat melihat nilai mahasiswa lain, DPL tidak dapat mengubah data administrasi yang menjadi kewenangan panitia, dan pemerintah desa hanya dapat mengakses informasi serta penilaian yang berkaitan dengan wilayah penempatannya.

Selain itu, dilakukan pemeriksaan terhadap mekanisme autentikasi dan pencatatan aktivitas agar keamanan informasi dapat terjaga.
