# A4. Kebutuhan Signifikan (Architecturally Significant Requirements/ASR)

Penanggung jawab: [ Eka Putri Aulia ]

## 1. Pengertian

Architecturally Significant Requirements (ASR) merupakan kebutuhan sistem yang memiliki pengaruh besar terhadap perancangan arsitektur perangkat lunak. Kebutuhan ini perlu diperhatikan karena dapat menentukan bagaimana sistem dibangun, bagaimana data dikelola, serta bagaimana sistem memenuhi kebutuhan pengguna.

Pada subsistem Assignment & Assessment untuk layanan KKN Tematik (Membangun Desa), identifikasi ASR dilakukan berdasarkan lima proses utama, yaitu pendaftaran peserta, penempatan desa, bimbingan dosen, pengumpulan laporan kegiatan, serta penilaian dan rekapitulasi nilai akhir.

Berdasarkan ruang lingkup tersebut dan hasil analisis kebutuhan pengguna, terdapat tiga kebutuhan signifikan yang perlu diperhatikan dalam perancangan arsitektur sistem.

## 2. Identifikasi Kebutuhan Signifikan (ASR)

### ASR-01 - Integrasi Pengelolaan Proses Layanan KKN

**Jenis:** Kebutuhan Fungsional

**Deskripsi kebutuhan:**

Sistem harus mampu mengintegrasikan seluruh proses layanan KKN Tematik, mulai dari pendaftaran peserta, verifikasi persyaratan, penempatan desa, pembagian kelompok, bimbingan dosen, pengumpulan laporan kegiatan, hingga penilaian dan rekapitulasi nilai akhir dalam satu sistem.

**Alasan menjadi kebutuhan signifikan:**

Berdasarkan hasil wawancara dengan mahasiswa peserta KKN (R1), proses pendaftaran masih dilakukan melalui kombinasi online dan offline. Mahasiswa mengisi formulir melalui tautan yang dibagikan panitia, sedangkan berkas persyaratan dikumpulkan secara langsung melalui bagian akademik fakultas. Informasi mengenai kelompok, lokasi KKN, dan dosen pembimbing juga disampaikan melalui grup KKN.

Responden menyampaikan bahwa fitur yang paling dibutuhkan adalah informasi jadwal kegiatan, agenda penting, proses pendaftaran, pembagian kelompok, dan penempatan lokasi dalam satu sistem. Selain itu, transparansi pembagian kelompok dan penentuan lokasi KKN juga perlu ditingkatkan.

Kebutuhan ini sangat memengaruhi arsitektur karena sistem harus mampu menghubungkan setiap proses layanan KKN agar data dan informasi dari satu tahapan dapat digunakan pada tahapan berikutnya. Sebagai contoh, data mahasiswa yang telah diverifikasi dapat digunakan dalam proses penempatan desa, kemudian dihubungkan dengan kelompok dan dosen pembimbing, hingga menjadi dasar pengelolaan laporan serta penilaian.

Dengan demikian, diperlukan rancangan sistem yang memiliki modul-modul saling terhubung sehingga seluruh proses Assignment & Assessment dapat dikelola secara terintegrasi.

### ASR-02 - Keamanan dan Pembatasan Hak Akses Pengguna

**Jenis:** Atribut Kualitas (Security)

**Deskripsi kebutuhan:**

Sistem harus menerapkan autentikasi dan pembatasan hak akses berdasarkan peran pengguna, yaitu mahasiswa, Dosen Pembimbing Lapangan (DPL), panitia KKN, dan pemerintah desa. Setiap pengguna hanya dapat mengakses dan mengelola informasi sesuai dengan tugas serta kewenangannya.

**Alasan menjadi kebutuhan signifikan:**

Berdasarkan hasil wawancara R1, data pribadi mahasiswa dan nilai akademik merupakan informasi yang perlu dibatasi aksesnya. Informasi tersebut hanya boleh diketahui oleh pihak yang memiliki kepentingan dan kewenangan.

Dalam subsistem Assignment & Assessment, terdapat beberapa jenis data yang perlu dilindungi, seperti data pribadi mahasiswa, dokumen persyaratan pendaftaran, catatan bimbingan, laporan kegiatan, dan hasil penilaian.

Kebutuhan ini sangat memengaruhi arsitektur karena sistem harus memiliki mekanisme autentikasi dan otorisasi untuk membedakan hak akses setiap pengguna.

Sebagai contoh, mahasiswa hanya dapat mengakses informasi dan laporan miliknya sendiri, DPL dapat melihat serta memeriksa laporan mahasiswa yang menjadi tanggung jawabnya, panitia dapat mengelola administrasi dan rekapitulasi nilai, sedangkan pemerintah desa dapat memberikan konfirmasi atau penilaian sesuai kewenangannya.

Dengan adanya pembatasan hak akses tersebut, keamanan informasi dapat lebih terjaga dan risiko penyalahgunaan data oleh pihak yang tidak berwenang dapat dikurangi.

### ASR-03 - Integritas dan Konsistensi Data KKN

**Jenis:** Atribut Kualitas (Data Integrity)

**Deskripsi kebutuhan:**

Sistem harus menjaga agar seluruh data yang berkaitan dengan pendaftaran, penempatan desa, pembagian kelompok, penugasan DPL, bimbingan, laporan kegiatan, dan penilaian tersimpan secara konsisten, akurat, serta dapat ditelusuri apabila terjadi perubahan.

**Alasan menjadi kebutuhan signifikan:**

Subsistem Assignment & Assessment memiliki beberapa proses yang saling berkaitan. Data mahasiswa yang telah mendaftar harus sesuai dengan hasil verifikasi, penempatan desa, kelompok, dan dosen pembimbing yang telah ditetapkan. Begitu pula dengan laporan kegiatan dan hasil penilaian yang harus terhubung dengan mahasiswa yang benar.

Berdasarkan hasil wawancara R1, penempatan lokasi dan pembagian kelompok ditentukan oleh pihak kampus. Responden juga menyampaikan bahwa pembagian kelompok dan penentuan lokasi perlu dibuat lebih transparan dan mudah dipantau.

Kebutuhan ini sangat memengaruhi arsitektur karena sistem membutuhkan basis data yang terstruktur, mekanisme validasi data, serta pencatatan riwayat perubahan. Hal tersebut diperlukan agar setiap perubahan informasi, seperti perubahan kelompok, penempatan desa, status laporan, maupun hasil penilaian, tidak menyebabkan ketidaksesuaian dengan data lainnya.

Dengan demikian, sistem dapat mengurangi risiko kesalahan pencatatan, data ganda, dan ketidaksesuaian informasi selama pelaksanaan KKN Tematik.

## 3. Ringkasan Kebutuhan Signifikan (ASR)
**Tabel 1. Ringkasan Kebutuhan Signifikan Arsitektur pada Subsistem Assignment & Assessment**
| Kode | Kebutuhan Signifikan | Jenis |
|---|---|---|
| ASR-01 | Integrasi pengelolaan proses layanan KKN | Fungsional |
| ASR-02 | Keamanan dan pembatasan hak akses pengguna | Atribut kualitas |
| ASR-03 | Integritas dan konsistensi data KKN | Atribut kualitas |

## 4. Kesimpulan

Berdasarkan hasil identifikasi, terdapat tiga kebutuhan signifikan yang perlu diperhatikan dalam perancangan arsitektur subsistem Assignment & Assessment pada layanan KKN Tematik (Membangun Desa).

Ketiga kebutuhan tersebut meliputi integrasi pengelolaan proses layanan KKN, keamanan dan pembatasan hak akses pengguna, serta integritas dan konsistensi data. Ketiganya dipilih karena memiliki pengaruh langsung terhadap struktur sistem, pengelolaan data, dan hubungan antarproses layanan KKN.

Dengan memperhatikan kebutuhan tersebut, sistem diharapkan mampu mendukung seluruh tahapan KKN, mulai dari pendaftaran hingga penilaian akhir, secara lebih terintegrasi, aman, dan terstruktur.
