# B1. Identifikasi dan Klasifikasi Karakteristik Arsitektur

Penanggung jawab: [ Eka Putri Aulia ]

Karakteristik arsitektur merupakan aspek kualitas atau kebutuhan teknis yang memengaruhi bagaimana sebuah sistem dirancang dan dikembangkan. Pada layanan KKN Tematik, karakteristik arsitektur perlu diperhatikan agar sistem dapat mengelola data dan proses KKN dengan baik, aman, serta mudah digunakan oleh setiap pihak yang terlibat.

## 1. Daftar Kandidat Karakteristik Arsitektur

Berikut adalah 10 kandidat karakteristik arsitektur yang dapat dipertimbangkan dalam perancangan layanan KKN Tematik.

**Tabel 1. Daftar Kandidat Karakteristik Arsitektur Layanan KKN Tematik**
| Karakteristik | Kategori | Sifat | Atribut terukur | ISO/IEC 25010 |
|---|---|---|---|---|
| Keamanan (Security) | Lintas sektor | Implisit | 100% akses terhadap data sensitif harus melalui autentikasi dan pemeriksaan hak akses. Seluruh aktivitas penting yang ditetapkan harus tercatat dalam log dan diperiksa melalui pengujian. | Security |
| Integritas Data (Data Integrity) | Lintas sektor | Implisit | 100% data pendaftaran, kelompok, penempatan, dan penilaian harus melewati validasi sebelum disimpan. Pengujian dilakukan menggunakan data valid dan tidak valid. | Security |
| Keandalan (Reliability) | Operasional | Implisit | Minimal 99% transaksi utama yang diuji harus selesai tanpa kegagalan pada skenario pengujian yang ditetapkan. | Reliability |
| Kinerja (Performance) | Operasional | Implisit | Minimal 95% permintaan halaman utama selesai dalam waktu kurang dari 3 detik saat diuji dengan 100 pengguna bersamaan. | Performance efficiency |
| Kemudahan Penggunaan (Usability) | Operasional | Implisit | Minimal 90% pengguna uji dapat menyelesaikan tugas utama tanpa bantuan. | Usability |
| Ketersediaan (Availability) | Operasional | Implisit | Layanan memiliki target ketersediaan minimal 99% selama periode operasional yang ditetapkan, berdasarkan hasil pemantauan. | Reliability |
| Kemudahan Pemeliharaan (Maintainability) | Struktural | Implisit | Perubahan aturan KKN dapat dilakukan tanpa mengubah lebih dari satu modul lain yang tidak terkait, berdasarkan skenario pengujian yang ditetapkan. | Maintainability |
| Kemudahan Pengembangan (Modifiability) | Struktural | Implisit | Penambahan satu fitur baru dapat dilakukan tanpa mengubah modul yang tidak terkait, berdasarkan skenario pengujian yang ditetapkan. | Maintainability |
| Interoperabilitas (Interoperability) | Struktural | Implisit | 100% data yang dipertukarkan dengan sistem lain dalam skenario integrasi harus sesuai dengan format dan aturan validasi yang disepakati. | Compatibility |
| Auditabilitas (Auditability) | Lintas sektor | Implisit | 100% perubahan penting pada penempatan dan penilaian yang diuji harus mencatat pelaku, waktu, dan jenis perubahan. | Security |

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

**Tabel 2. Pengujian Tiga Karakteristik Pendorong Arsitektur**
| Ciri Pengujian | Penjelasan |
|---|---|
| 1. Berpengaruh terhadap keputusan desain | Karakteristik tersebut memengaruhi cara sistem dirancang, misalnya pembagian modul, pengelolaan database, dan pengaturan hak akses. |
| 2. Berkaitan dengan kebutuhan nonfungsional | Karakteristik tersebut tidak hanya menjelaskan fitur yang tersedia, tetapi juga bagaimana sistem harus bekerja dan memenuhi kualitas tertentu. |
| 3. Penting bagi keberhasilan sistem | Jika karakteristik tersebut tidak terpenuhi, sistem dapat mengalami masalah yang berdampak pada pengguna dan proses layanan KKN. |

Berikut hasil pengujiannya:

**Tabel 3. Hasil Pengujian Tiga Karakteristik Pendorong Arsitektur**
| Karakteristik | Berpengaruh terhadap desain | Kebutuhan nonfungsional | Penting bagi keberhasilan | Hasil |
|---|---|---|---|---|
| Keamanan (Security) | Ya | Ya | Ya | Lolos |
| Integritas Data (Data Integrity) | Ya | Ya | Ya | Lolos |
| Keandalan (Reliability) | Ya | Ya | Ya | Lolos |

Berdasarkan hasil pengujian tersebut, ketiga karakteristik dinyatakan lolos karena memiliki pengaruh terhadap keputusan desain, termasuk dalam kebutuhan kualitas sistem, dan penting bagi keberhasilan layanan KKN Tematik.

Hasil pengujian ini merupakan penilaian berdasarkan analisis rancangan. Hasil tersebut tidak berarti bahwa sistem sudah terbukti memenuhi target keamanan, integritas data, dan keandalan melalui pengujian teknis.

## 4. Kesimpulan

Berdasarkan identifikasi dan klasifikasi yang telah dilakukan, terdapat 10 kandidat karakteristik arsitektur yang dapat dipertimbangkan dalam perancangan layanan KKN Tematik. Kandidat tersebut mencakup keamanan, integritas data, keandalan, kinerja, kemudahan penggunaan, ketersediaan, kemudahan pemeliharaan, kemudahan pengembangan, interoperabilitas, dan auditabilitas.

Dari 10 kandidat tersebut, dipilih tiga karakteristik utama sebagai pendorong arsitektur, yaitu keamanan, integritas data, dan keandalan. Keamanan diprioritaskan untuk melindungi informasi dan membatasi akses pengguna. Integritas data diprioritaskan untuk menjaga konsistensi informasi pada setiap proses KKN. Keandalan diprioritaskan untuk mendukung pelaksanaan proses utama dan meminimalkan kegagalan layanan.

Ketiga karakteristik tersebut dinilai berpengaruh terhadap keputusan desain, berkaitan dengan kebutuhan nonfungsional, dan penting bagi keberhasilan layanan KKN Tematik. Oleh karena itu, ketiganya dapat dijadikan dasar dalam menentukan keputusan arsitektur dan menyusun keputusan arsitektur yang terdokumentasi pada bagian ADR.

Target atribut terukur yang dicantumkan dalam tabel merupakan usulan awal yang perlu disepakati dan diverifikasi melalui pengujian. Dengan demikian, hasil identifikasi ini menjadi dasar untuk melanjutkan perancangan arsitektur layanan KKN Tematik agar lebih aman, konsisten, dan andal.
