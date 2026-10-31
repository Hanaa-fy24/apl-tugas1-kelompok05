
# B1. Identifikasi dan Klasifikasi Karakteristik Arsitektur

Karakteristik arsitektur merupakan aspek kualitas atau kebutuhan teknis yang memengaruhi bagaimana sebuah sistem dirancang dan dikembangkan. Pada layanan KKN Tematik, karakteristik arsitektur perlu diperhatikan agar sistem dapat mengelola data dan proses KKN dengan baik, aman, serta mudah digunakan oleh setiap pihak yang terlibat.

## 1. Daftar Kandidat Karakteristik Arsitektur

Berikut adalah 10 kandidat karakteristik arsitektur yang dapat dipertimbangkan dalam perancangan layanan KKN Tematik.

| No. | Karakteristik | Kategori | Sifat | Alasan |
|---|---|---|---|---|
| 1 | Keamanan (Security) | Lintas sektor | Eksplisit | Data pribadi mahasiswa dan nilai perlu dilindungi. Setiap pengguna harus memiliki hak akses sesuai perannya. |
| 2 | Integritas Data (Data Integrity) | Lintas sektor | Implisit | Data pendaftaran, kelompok, penempatan, laporan, dan nilai harus konsisten serta tidak mengalami kesalahan atau perubahan tanpa izin. |
| 3 | Keandalan (Reliability) | Operasional | Implisit | Sistem diharapkan dapat menjalankan proses KKN dengan baik dan meminimalkan kegagalan ketika digunakan. |
| 4 | Kinerja (Performance) | Operasional | Implisit | Sistem perlu memberikan respons yang cukup cepat ketika pengguna membuka informasi, mengunggah laporan, atau mengakses nilai. |
| 5 | Kemudahan Penggunaan (Usability) | Operasional | Eksplisit | Informasi KKN diharapkan tersedia secara terpusat sehingga mahasiswa, DPL, dan pengelola lebih mudah mengakses informasi yang dibutuhkan. |
| 6 | Ketersediaan (Availability) | Operasional | Implisit | Informasi jadwal, penempatan, bimbingan, dan laporan perlu dapat diakses ketika dibutuhkan oleh pengguna. |
| 7 | Kemudahan Pemeliharaan (Maintainability) | Struktural | Implisit | Sistem perlu dirancang agar lebih mudah diperbaiki dan diperbarui apabila terdapat perubahan proses atau kebutuhan KKN. |
| 8 | Kemudahan Pengembangan (Modifiability) | Struktural | Implisit | Sistem perlu memungkinkan penyesuaian fitur, misalnya perubahan aturan pendaftaran, pembagian kelompok, atau format laporan. |
| 9 | Interoperabilitas (Interoperability) | Struktural | Implisit | Sistem mungkin perlu bertukar data dengan sistem akademik kampus atau layanan lain yang berkaitan, sesuai kebutuhan integrasi yang ditetapkan. |
| 10 | Auditabilitas (Auditability) | Lintas sektor | Implisit | Aktivitas penting seperti verifikasi pendaftaran, perubahan penempatan, persetujuan laporan, dan penilaian perlu dapat ditelusuri. |

### Keterangan Kategori

- **Operasional:** Berkaitan dengan bagaimana sistem berjalan dan digunakan.
- **Struktural:** Berkaitan dengan bagaimana sistem disusun, dikembangkan, dan dipelihara.
- **Lintas sektor:** Berkaitan dengan aspek yang memengaruhi beberapa bagian sistem sekaligus.

### Keterangan Sifat

- **Eksplisit:** Kebutuhan disebutkan secara langsung oleh pengguna atau sumber informasi.
- **Implisit:** Kebutuhan tidak disebutkan secara langsung, tetapi dapat disimpulkan dari proses dan kebutuhan sistem.

**Catatan:** Karakteristik yang bersifat implisit merupakan hasil analisis kebutuhan rancangan, bukan pernyataan langsung dari narasumber.

## 2. Pemilihan Tiga Karakteristik Pendorong

Berdasarkan 10 kandidat di atas, dipilih tiga karakteristik yang paling penting sebagai pendorong arsitektur layanan KKN Tematik, yaitu:

### 1. Keamanan (Security)

Keamanan menjadi prioritas karena sistem mengelola informasi pribadi mahasiswa, data pendaftaran, serta hasil penilaian. Tidak semua pengguna boleh mengakses atau mengubah seluruh informasi.

Oleh karena itu, sistem perlu menerapkan autentikasi dan pembatasan hak akses berdasarkan peran pengguna, seperti mahasiswa, DPL, panitia KKN, dan pemerintah desa.

### 2. Integritas Data (Data Integrity)

Integritas data penting karena seluruh proses KKN saling berhubungan. Data mahasiswa yang sudah diverifikasi akan digunakan dalam proses pembagian kelompok dan penempatan desa, kemudian berkaitan dengan bimbingan, laporan, hingga penilaian.

Jika data tidak konsisten atau mengalami kesalahan, proses berikutnya juga dapat terganggu. Karena itu, sistem perlu memiliki validasi data dan pencatatan perubahan.

### 3. Keandalan (Reliability)

Keandalan diperlukan agar layanan KKN dapat menjalankan prosesnya dengan baik tanpa sering mengalami gangguan atau kegagalan. Sistem harus mampu mendukung pengguna ketika melakukan pendaftaran, mengakses informasi kelompok, mengunggah laporan, dan melihat hasil penilaian.

Keandalan juga penting agar data dan proses yang sudah dilakukan pengguna tidak mudah hilang ketika terjadi gangguan sistem.

## 3. Pengujian Tiga Karakteristik Pendorong

Untuk memastikan ketiga karakteristik tersebut benar-benar penting bagi arsitektur, digunakan tiga ciri karakteristik arsitektur sebagai alat uji.

| Ciri Pengujian | Penjelasan |
|---|---|
| 1. Berpengaruh terhadap keputusan desain | Karakteristik tersebut memengaruhi cara sistem dirancang, misalnya pembagian modul, pengelolaan database, dan pengaturan hak akses. |
| 2. Berkaitan dengan kebutuhan nonfungsional | Karakteristik tersebut tidak hanya menjelaskan fitur yang tersedia, tetapi juga bagaimana sistem harus bekerja dan memenuhi kualitas tertentu. |
| 3. Penting bagi keberhasilan sistem | Jika karakteristik tersebut tidak terpenuhi, sistem dapat mengalami masalah yang berdampak pada pengguna dan proses layanan KKN. |

Berikut hasil pengujiannya:

| Karakteristik | Berpengaruh terhadap desain | Kebutuhan nonfungsional | Penting bagi keberhasilan | Hasil |
|---|---|---|---|---|
| Keamanan | Ya | Ya | Ya | Lolos |
| Integritas Data | Ya | Ya | Ya | Lolos |
| Keandalan | Ya | Ya | Ya | Lolos |

## 4. Kesimpulan

Berdasarkan hasil identifikasi dan klasifikasi, terdapat 10 kandidat karakteristik arsitektur yang dapat dipertimbangkan dalam perancangan layanan KKN Tematik. Dari seluruh kandidat tersebut, dipilih tiga karakteristik utama, yaitu keamanan, integritas data, dan keandalan.

Ketiga karakteristik tersebut diprioritaskan karena memiliki pengaruh terhadap keputusan desain, berkaitan dengan kebutuhan nonfungsional, dan penting bagi keberhasilan layanan KKN Tematik. Hasil ini juga sejalan dengan ASR dan ADR pada Bagian A, khususnya mengenai perlindungan data, konsistensi informasi, serta pengelolaan proses KKN yang terintegrasi.
