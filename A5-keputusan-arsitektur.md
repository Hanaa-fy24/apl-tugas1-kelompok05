
# A5. Keputusan Arsitektur dan Architecture Decision Record (ADR)

## 1. Pengertian

Keputusan arsitektur merupakan keputusan penting yang dibuat dalam proses perancangan sistem untuk menentukan bagaimana sistem akan dibangun agar dapat memenuhi kebutuhan yang telah diidentifikasi.

Dalam perancangan subsistem Assignment & Assessment pada layanan KKN Tematik (Membangun Desa), keputusan arsitektur dibuat dengan mempertimbangkan kebutuhan integrasi proses layanan, keamanan informasi pengguna, serta konsistensi data.

Untuk mendokumentasikan keputusan tersebut, digunakan Architecture Decision Record (ADR). ADR merupakan dokumen yang mencatat keputusan arsitektur beserta alasan pemilihan, kondisi yang melatarbelakangi, konsekuensi, dan cara memastikan keputusan tersebut diterapkan.

Berdasarkan kebutuhan yang telah diidentifikasi pada bagian A4, berikut dua ADR yang ditetapkan untuk subsistem Assignment & Assessment.

## 2. Architecture Decision Record (ADR)

### ADR-001 - Penerapan Arsitektur Modular untuk Integrasi Layanan KKN

**a. Title (Judul)**

Penerapan Arsitektur Modular untuk Mengintegrasikan Proses Assignment & Assessment pada Layanan KKN Tematik.

**b. Status**

Accepted – Disetujui.

Keputusan ini telah disepakati oleh anggota kelompok dan ditetapkan sebagai keputusan arsitektur untuk subsistem Assignment & Assessment pada layanan KKN Tematik.

**c. Context (Konteks)**

Subsistem Assignment & Assessment memiliki lima proses utama yang saling berkaitan, yaitu pendaftaran peserta, penempatan desa, bimbingan dosen, pengumpulan laporan kegiatan, serta penilaian dan rekapitulasi nilai akhir.

Berdasarkan hasil wawancara dengan mahasiswa peserta KKN (R1), proses pendaftaran masih dilakukan melalui kombinasi online dan offline. Pendaftaran online menggunakan tautan yang dibagikan panitia, sedangkan berkas persyaratan dikumpulkan secara langsung melalui bagian akademik fakultas. Informasi mengenai kelompok, lokasi KKN, dan dosen pembimbing disampaikan melalui grup KKN.

Responden juga menyampaikan bahwa informasi pendaftaran, jadwal kegiatan, agenda penting, dan penempatan mahasiswa perlu tersedia dalam satu sistem. Selain itu, pembagian kelompok dan penentuan lokasi KKN perlu dibuat lebih transparan dan mudah dipantau.

Kondisi tersebut menunjukkan perlunya sistem yang dapat menghubungkan seluruh proses layanan KKN agar informasi tidak tersebar di berbagai media dan setiap tahapan dapat dikelola secara lebih terstruktur.

**d. Decision (Keputusan)**

Kami memutuskan untuk menggunakan arsitektur modular, yaitu pendekatan perancangan sistem dengan membagi layanan ke dalam beberapa modul berdasarkan fungsi masing-masing.

Modul yang dirancang meliputi:

1. **Modul Pendaftaran:** Mengelola data mahasiswa, formulir pendaftaran, unggahan persyaratan, dan verifikasi kelayakan peserta.
2. **Modul Penempatan Desa:** Mengelola pembentukan kelompok, penentuan lokasi desa, kuota, serta informasi penempatan mahasiswa.
3. **Modul Bimbingan Dosen:** Mengelola penugasan DPL, jadwal bimbingan, catatan konsultasi, dan umpan balik.
4. **Modul Laporan Kegiatan:** Mengelola pengumpulan logbook, dokumentasi, laporan mingguan, dan laporan akhir.
5. **Modul Penilaian:** Mengelola penilaian oleh DPL dan pemerintah desa, perhitungan nilai akhir, serta rekapitulasi nilai untuk panitia.

Setiap modul memiliki tanggung jawab masing-masing, tetapi tetap saling terhubung melalui data dan proses yang dibutuhkan oleh modul lainnya.

**e. Consequences (Konsekuensi)**

Penerapan arsitektur modular memiliki beberapa keuntungan dan kerugian yang perlu dipertimbangkan.

**Keuntungan:**

- Setiap proses layanan KKN dapat dikelola berdasarkan fungsi masing-masing.
- Hubungan antara pendaftaran, penempatan, bimbingan, laporan, dan penilaian menjadi lebih terstruktur.
- Pengembangan dan perbaikan sistem dapat dilakukan pada modul tertentu tanpa harus mengubah seluruh bagian sistem.
- Mempermudah pemeliharaan serta pengembangan fitur apabila terdapat perubahan kebutuhan layanan KKN.

**Kerugian:**

- Membutuhkan perencanaan hubungan antarmodul agar tidak terjadi ketidaksesuaian data.
- Pengembangan sistem membutuhkan koordinasi yang baik karena setiap modul saling berkaitan.
- Kesalahan dalam komunikasi atau pertukaran data antarmodul dapat mengganggu proses layanan lainnya.
- Perancangan awal membutuhkan waktu lebih banyak untuk menentukan pembagian tanggung jawab setiap modul.

**f. Compliance (Kepatuhan)**

Keputusan ini diterapkan dengan memastikan setiap modul memiliki fungsi dan tanggung jawab yang jelas sesuai dengan ruang lingkup layanan KKN.

Pengujian dilakukan terhadap setiap modul untuk memastikan proses pendaftaran, penempatan desa, bimbingan dosen, pengumpulan laporan, dan penilaian dapat berjalan sesuai fungsinya.

Selain itu, dilakukan pengujian integrasi untuk memastikan data dari satu modul dapat digunakan oleh modul lainnya secara tepat. Contohnya, data mahasiswa yang telah diverifikasi pada modul pendaftaran harus dapat digunakan dalam proses penempatan desa dan pembentukan kelompok.

---

### ADR-002 - Penerapan Role-Based Access Control (RBAC) untuk Keamanan Data

**a. Title (Judul)**

Penerapan Role-Based Access Control (RBAC) untuk Mengatur Hak Akses Pengguna pada Subsistem Assignment & Assessment.

**b. Status**

Accepted – Disetujui.

Keputusan ini telah disepakati oleh anggota kelompok dan ditetapkan sebagai keputusan arsitektur untuk subsistem Assignment & Assessment pada layanan KKN Tematik.

**c. Context (Konteks)**

Subsistem Assignment & Assessment melibatkan beberapa aktor, yaitu mahasiswa, Dosen Pembimbing Lapangan (DPL), panitia KKN, dan pemerintah desa. Setiap aktor memiliki tanggung jawab serta kebutuhan akses informasi yang berbeda.

Berdasarkan hasil wawancara R1, data pribadi mahasiswa, dokumen administrasi, dan nilai akademik merupakan informasi yang perlu dilindungi. Mahasiswa hanya seharusnya dapat mengakses informasi yang berkaitan dengan dirinya, sedangkan dosen pembimbing dan pengelola memperoleh akses sesuai dengan tanggung jawab masing-masing.

Hal tersebut menunjukkan bahwa sistem membutuhkan mekanisme pengaturan hak akses agar informasi penting tidak dapat dilihat atau diubah oleh pihak yang tidak memiliki kewenangan.

**d. Decision (Keputusan)**

Kami memutuskan untuk menerapkan Role-Based Access Control (RBAC), yaitu mekanisme pengaturan hak akses berdasarkan peran pengguna.

Pembagian hak akses dirancang sebagai berikut:

1. **Mahasiswa:** Dapat mengelola data pendaftaran miliknya, melihat informasi kelompok dan penempatan desa, mengakses informasi DPL, mengikuti proses bimbingan, mengunggah laporan kegiatan, serta melihat hasil penilaian miliknya sendiri.
2. **Dosen Pembimbing Lapangan (DPL):** Dapat melihat data mahasiswa yang menjadi tanggung jawabnya, mengelola jadwal dan catatan bimbingan, memeriksa laporan kegiatan, memberikan umpan balik, serta mengelola penilaian sesuai kewenangannya.
3. **Panitia KKN:** Dapat mengelola data pendaftaran, memverifikasi persyaratan, mengatur penempatan desa dan kelompok, serta mengelola administrasi dan rekapitulasi nilai akhir.
4. **Pemerintah Desa:** Dapat mengakses informasi kelompok yang ditempatkan di wilayahnya serta memberikan konfirmasi dan penilaian sesuai dengan kewenangan yang diberikan.

Selain pembagian hak akses, sistem juga dirancang menggunakan autentikasi untuk memastikan identitas pengguna serta pencatatan aktivitas untuk membantu menelusuri perubahan pada data penting.

**e. Consequences (Konsekuensi)**

Penerapan RBAC memiliki beberapa keuntungan dan kerugian sebagai berikut.

**Keuntungan:**

- Melindungi data pribadi mahasiswa, dokumen administrasi, dan hasil penilaian.
- Setiap pengguna hanya dapat mengakses fitur sesuai dengan peran dan kewenangannya.
- Mengurangi risiko penyalahgunaan atau perubahan data oleh pihak yang tidak berwenang.
- Mempermudah pengelolaan hak akses karena pengaturannya dilakukan berdasarkan peran pengguna.
- Membantu meningkatkan keamanan dan kepercayaan pengguna terhadap sistem.

**Kerugian:**

- Membutuhkan pengelolaan akun dan hak akses yang lebih terstruktur.
- Pengembangan sistem membutuhkan proses tambahan untuk mengatur setiap peran pengguna.
- Kesalahan dalam pengaturan hak akses dapat menyebabkan pengguna tidak dapat mengakses fitur yang sebenarnya dibutuhkan.
- Pengelola perlu melakukan pemeriksaan dan pemeliharaan hak akses secara berkala apabila terdapat perubahan tugas atau tanggung jawab pengguna.

**f. Compliance (Kepatuhan)**

Keputusan ini diterapkan dengan memastikan setiap peran pengguna memiliki hak akses yang sesuai dengan tanggung jawabnya.

Pengujian dilakukan menggunakan beberapa akun dengan peran berbeda untuk memastikan mahasiswa, DPL, panitia KKN, dan pemerintah desa hanya dapat mengakses fitur sesuai dengan kewenangannya.

Sebagai contoh, dilakukan pengujian untuk memastikan mahasiswa tidak dapat melihat nilai mahasiswa lain, DPL tidak dapat mengubah data administrasi yang menjadi kewenangan panitia, dan pemerintah desa hanya dapat mengakses informasi serta penilaian yang berkaitan dengan wilayah penempatannya.

Selain itu, dilakukan pemeriksaan terhadap mekanisme autentikasi dan pencatatan aktivitas agar keamanan informasi dapat terjaga.

## 3. Rencana Komunikasi dan Dokumentasi ADR

Setiap keputusan arsitektur yang telah dibuat perlu didokumentasikan dan dikomunikasikan kepada seluruh anggota kelompok. Hal ini bertujuan agar setiap anggota memahami keputusan yang telah disepakati dan dapat menggunakannya sebagai pedoman dalam mengerjakan bagian masing-masing.

Rencana komunikasi ADR pada kelompok II-5 adalah sebagai berikut.

### a. Tempat Penyimpanan ADR

Dokumentasi ADR disimpan dalam repository kelompok pada branch `main`, melalui file `A5-keputusan-arsitektur.md`.

Setiap keputusan diberi nomor dan judul yang jelas agar mudah ditemukan, yaitu:

- ADR-001 - Penerapan Arsitektur Modular untuk Integrasi Layanan KKN.
- ADR-002 - Penerapan Role-Based Access Control (RBAC) untuk Keamanan Data.

Repository digunakan sebagai tempat penyimpanan utama agar seluruh anggota kelompok dapat melihat, membaca, dan memperbarui dokumentasi keputusan arsitektur apabila terdapat perubahan yang telah disepakati.

### b. Pihak yang Diberi Tahu

Informasi mengenai keputusan arsitektur disampaikan kepada seluruh anggota kelompok II-5, terutama anggota yang bertanggung jawab terhadap perancangan sistem, pengelolaan data, keamanan, dan dokumentasi laporan.

Apabila terdapat keputusan baru atau perubahan terhadap ADR yang sudah dibuat, anggota kelompok akan diberi tahu melalui grup komunikasi kelompok dengan menyertakan tautan dokumen ADR yang telah diperbarui.

Dengan demikian, seluruh anggota dapat mengetahui perkembangan keputusan arsitektur tanpa harus mencari informasi dari percakapan sebelumnya.

### c. Cara Menghindari Tiga Anti-Pattern dalam Pengambilan Keputusan

Dalam proses pengambilan keputusan arsitektur, terdapat tiga anti-pattern yang perlu dihindari agar keputusan yang dihasilkan jelas, terdokumentasi, dan dapat dipahami oleh seluruh anggota kelompok.

**1. Covering Your Assets**

Covering Your Assets merupakan kondisi ketika seseorang mengambil keputusan hanya untuk melindungi dirinya dari tanggung jawab apabila terjadi kesalahan.

Cara menghindarinya adalah dengan mencatat setiap keputusan beserta alasan, konsekuensi, dan pihak yang menyetujuinya. Setiap anggota kelompok juga perlu terbuka terhadap masukan dan bertanggung jawab atas keputusan yang telah disepakati bersama.

**2. Groundhog Day**

Groundhog Day merupakan kondisi ketika pembahasan mengenai keputusan yang sama terus diulang karena tidak adanya dokumentasi atau kesepakatan yang jelas.

Cara menghindarinya adalah dengan mendokumentasikan setiap keputusan yang telah disepakati ke dalam ADR dan menyimpannya di repository kelompok. Dengan demikian, anggota dapat melihat kembali hasil pembahasan sebelumnya tanpa harus mengulang diskusi dari awal.

**3. Email-Driven Architecture**

Email-Driven Architecture merupakan kondisi ketika keputusan arsitektur tersebar dalam berbagai percakapan atau pesan sehingga sulit menemukan keputusan yang benar-benar telah disepakati.

Cara menghindarinya adalah dengan menjadikan repository kelompok sebagai sumber dokumentasi utama. Grup komunikasi hanya digunakan untuk menyampaikan informasi, pemberitahuan, dan tautan menuju dokumen ADR, bukan sebagai tempat penyimpanan keputusan utama.

## 4. Kesimpulan

Berdasarkan hasil analisis dan kebutuhan yang telah diidentifikasi, terdapat dua keputusan arsitektur yang ditetapkan untuk subsistem Assignment & Assessment pada layanan KKN Tematik (Membangun Desa).

Keputusan pertama adalah penerapan arsitektur modular untuk mengintegrasikan lima proses utama layanan KKN, mulai dari pendaftaran peserta hingga penilaian akhir. Keputusan kedua adalah penerapan Role-Based Access Control (RBAC) untuk mengatur hak akses berdasarkan peran pengguna sehingga keamanan informasi dapat lebih terjaga.

Kedua keputusan tersebut diharapkan dapat membantu menghasilkan rancangan sistem yang lebih terstruktur, terintegrasi, dan aman. Selain itu, dokumentasi ADR dalam repository serta komunikasi yang jelas antaranggota kelompok diperlukan agar setiap keputusan dapat dipahami, ditelusuri, dan dijadikan pedoman selama proses perancangan sistem.
