# A5 – Architecture Decision Record (ADR)

## ADR-001: Penerapan Arsitektur Modular pada Layanan KKN Tematik

- **Status:** Diterima (Accepted)
- **Tanggal:** 31-10-2026
- **Pengambil keputusan:** Kelompok II-5 (Ashfy Nur Raihana, Eka Putri Aulia, Nabila Sinta Salsabila, Siti Mutiah Nurhaliza)

### Context

Layanan KKN Tematik memiliki beberapa proses yang saling berkaitan, mulai dari pendaftaran mahasiswa, penempatan desa, bimbingan dosen, pengumpulan laporan kegiatan, hingga penilaian. Berdasarkan hasil wawancara dengan R1, proses pendaftaran dilakukan melalui kombinasi online dan offline. Informasi mengenai kelompok dan dosen pembimbing disampaikan melalui grup KKN, sedangkan penempatan lokasi dan pembagian kelompok ditentukan oleh pihak kampus.

Responden juga menyampaikan kebutuhan terhadap sistem yang menyediakan informasi pendaftaran, jadwal kegiatan, agenda penting, pembagian kelompok, dan lokasi penempatan secara lebih teratur. Selain itu, transparansi pembagian kelompok dan lokasi KKN masih perlu ditingkatkan.

Oleh karena itu, diperlukan rancangan arsitektur yang dapat mengintegrasikan proses-proses tersebut agar pengelolaan layanan menjadi lebih terstruktur.

Keputusan ini berkaitan dengan ASR-01 tentang integrasi proses layanan KKN dan ASR-03 tentang integritas data pada A4.

### Decision

Kami akan menerapkan arsitektur modular dengan membagi layanan Assignment & Assessment menjadi beberapa modul berdasarkan tanggung jawab masing-masing, yaitu:

1. **Modul Pendaftaran:** Mengelola proses pendaftaran dan persyaratan mahasiswa.
2. **Modul Penempatan Desa:** Mengelola informasi lokasi penempatan dan pembagian kelompok mahasiswa.
3. **Modul Bimbingan Dosen:** Mengelola informasi dosen pembimbing dan kegiatan bimbingan mahasiswa.
4. **Modul Laporan Kegiatan:** Mengelola pengumpulan dan pemeriksaan laporan kegiatan KKN.
5. **Modul Penilaian:** Mengelola proses penilaian dan rekapitulasi hasil KKN.

Setiap modul memiliki tanggung jawab masing-masing, tetapi tetap saling terhubung agar seluruh proses layanan KKN Tematik dapat berjalan secara terintegrasi.

### Consequences

**Dampak positif:**

- Pengelolaan setiap proses layanan KKN menjadi lebih terstruktur.
- Hubungan data antarproses lebih mudah dikelola.
- Perubahan pada satu modul dapat dilakukan tanpa harus mengubah seluruh bagian sistem.
- Pemeliharaan dan pengembangan sistem menjadi lebih mudah.
- Informasi dari setiap tahapan KKN dapat dikelola secara lebih terorganisasi.

**Dampak negatif:**

- Membutuhkan perencanaan hubungan antar-modul agar pertukaran data berjalan dengan baik.
- Memerlukan koordinasi dalam pengembangan setiap modul.
- Kesalahan dalam pertukaran data antar-modul dapat memengaruhi proses lainnya.
- Perancangan awal membutuhkan waktu lebih banyak.

### Compliance

Keputusan ini dipastikan melalui pemeriksaan pembagian tanggung jawab setiap modul dan pengujian terhadap fungsi masing-masing modul. Pengujian integrasi dilakukan untuk memastikan data pendaftaran dapat terhubung dengan proses penempatan desa, pembagian kelompok, bimbingan dosen, laporan kegiatan, dan penilaian. Selain itu, konsistensi data antar-modul juga perlu diperiksa agar tidak terjadi perbedaan informasi pada setiap tahapan layanan KKN.

---

## ADR-002: Penerapan Role-Based Access Control (RBAC) pada Layanan KKN Tematik

- **Status:** Diterima (Accepted)
- **Tanggal:** 31-10-2026
- **Pengambil keputusan:** Kelompok II-5 (Ashfy Nur Raihana, Eka Putri Aulia, Nabila Sinta Salsabila, Siti Mutiah Nurhaliza)

### Context

Layanan KKN Tematik melibatkan beberapa jenis pengguna, yaitu mahasiswa, dosen pembimbing, panitia KKN, dan pemerintah desa. Setiap pengguna memiliki kebutuhan informasi dan kewenangan yang berbeda dalam menggunakan sistem.

Berdasarkan hasil wawancara dengan R1, data pribadi mahasiswa dan nilai akademik merupakan informasi yang perlu dibatasi aksesnya. Informasi tersebut hanya boleh diakses oleh pihak yang berkepentingan sesuai dengan kewenangannya.

Oleh karena itu, diperlukan pengaturan hak akses agar setiap pengguna hanya dapat melihat dan mengelola informasi sesuai dengan perannya.

Keputusan ini berkaitan dengan ASR-02 tentang keamanan dan pembatasan hak akses pengguna pada A4.

### Decision

Kami akan menerapkan Role-Based Access Control (RBAC), yaitu pengaturan hak akses berdasarkan peran pengguna. Pembagian hak akses dalam sistem meliputi:

1. **Mahasiswa:** Dapat mengelola data pendaftaran miliknya, melihat informasi kelompok, lokasi penempatan, dosen pembimbing, mengunggah laporan, dan melihat hasil penilaian miliknya sendiri.
2. **Dosen Pembimbing:** Dapat melihat mahasiswa yang menjadi tanggung jawabnya, memantau perkembangan kegiatan, memberikan bimbingan, memeriksa laporan, dan melakukan penilaian sesuai kewenangannya.
3. **Panitia KKN:** Dapat mengelola pendaftaran, memverifikasi persyaratan, mengatur penempatan desa, membagi kelompok, serta mengelola administrasi dan rekapitulasi penilaian.
4. **Pemerintah Desa:** Dapat melihat informasi kelompok mahasiswa yang ditempatkan di wilayahnya sesuai dengan kewenangan yang diberikan.

Selain pembagian hak akses, sistem juga menerapkan autentikasi pengguna untuk memastikan identitas pengguna dan pencatatan aktivitas pada bagian penting sistem.

### Consequences

**Dampak positif:**

- Melindungi data pribadi dan nilai akademik mahasiswa.
- Mencegah pengguna mengakses informasi di luar kewenangannya.
- Mempermudah pengelolaan hak akses berdasarkan peran pengguna.
- Mengurangi risiko penyalahgunaan data.
- Meningkatkan keamanan dan kepercayaan pengguna terhadap sistem.

**Dampak negatif:**

- Pengelolaan akun dan hak akses membutuhkan perhatian khusus.
- Membutuhkan waktu tambahan dalam proses pengembangan sistem.
- Kesalahan pengaturan hak akses dapat menyebabkan pengguna tidak dapat mengakses fitur yang seharusnya tersedia.
- Hak akses perlu diperiksa dan diperbarui secara berkala.

### Compliance

Keputusan ini dipastikan melalui pengujian menggunakan akun dengan peran yang berbeda. Pengujian dilakukan untuk memastikan mahasiswa tidak dapat melihat nilai mahasiswa lain, dosen hanya dapat mengakses mahasiswa yang menjadi tanggung jawabnya, dan pemerintah desa hanya dapat melihat informasi kelompok di wilayahnya. Panitia KKN diberikan akses sesuai tanggung jawab pengelolaan administrasi. Selain itu, autentikasi pengguna dan pencatatan aktivitas juga perlu diperiksa untuk memastikan keamanan akses sistem.
