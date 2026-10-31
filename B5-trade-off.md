
# B5 - Analisis Trade-off

penanggung jawab:[Nabila Sinta Salsabila]

## 1. Keamanan dan Kinerja Sistem

Keamanan dan kinerja merupakan dua karakteristik yang saling memengaruhi dalam pengembangan Layanan KKN Tematik (Membangun Desa). Sistem harus melindungi data mahasiswa, dosen pembimbing, penempatan desa, laporan kegiatan, dan hasil penilaian dari akses yang tidak berwenang. Penerapan autentikasi, pembatasan hak akses, dan validasi data dapat meningkatkan keamanan, tetapi juga dapat menambah waktu pemrosesan.

Sebaliknya, sistem yang terlalu berfokus pada kecepatan tanpa perlindungan yang memadai dapat meningkatkan risiko kebocoran data dan perubahan nilai secara tidak sah.

**Dampak trade-off:**
- Keamanan yang kuat membantu menjaga kerahasiaan dan keutuhan data akademik.
- Penerapan mekanisme keamanan yang berlebihan dapat memperlambat proses login dan pengiriman laporan.
- Kinerja yang baik memungkinkan pengguna mengakses informasi dan menyelesaikan aktivitas KKN dengan lebih cepat.
- Sistem yang mengutamakan kecepatan tanpa pengamanan yang memadai dapat meningkatkan risiko penyalahgunaan data.

**Prioritas:** Keamanan didahulukan karena sistem mengelola data pribadi dan data akademik yang harus dijaga kerahasiaan serta keutuhannya. Namun, mekanisme keamanan tetap perlu dirancang secara efisien agar kinerja sistem tidak terganggu.

**Strategi penyeimbangan:**
1. Menggunakan autentikasi dan pembatasan hak akses sesuai peran mahasiswa, dosen, dan administrator.
2. Melakukan validasi data pada proses pendaftaran, pengumpulan laporan, dan penilaian.
3. Mengoptimalkan pemrosesan data agar sistem tetap responsif.
4. Melakukan pencatatan aktivitas penting untuk membantu pemeriksaan apabila terjadi kesalahan atau penyalahgunaan.

## 2. Kemudahan Penggunaan dan Kelengkapan Fitur

Kemudahan penggunaan dan kelengkapan fitur saling memengaruhi karena sistem menyediakan fitur pendaftaran mahasiswa, penempatan desa, bimbingan dosen, pengumpulan laporan kegiatan, dan penilaian. Semakin banyak fitur yang tersedia, semakin lengkap layanan yang diberikan. Namun, terlalu banyak menu dan proses dalam satu tampilan dapat membuat pengguna kesulitan menggunakan sistem.

Sebaliknya, antarmuka yang terlalu sederhana dapat mempermudah pengguna, tetapi berisiko menghilangkan fitur penting yang dibutuhkan selama pelaksanaan KKN.

**Dampak trade-off:**
- Fitur yang lengkap mendukung seluruh tahapan pelaksanaan KKN dalam satu sistem.
- Terlalu banyak menu dapat membuat pengguna kesulitan menemukan fungsi yang dibutuhkan.
- Antarmuka yang sederhana membantu pengguna memahami alur kerja dengan lebih cepat.
- Pengurangan fitur secara berlebihan dapat menyebabkan proses tertentu harus dilakukan secara manual di luar sistem.

**Prioritas:** Kemudahan penggunaan didahulukan dengan tetap mempertahankan seluruh fitur utama. Alasannya, mahasiswa, dosen pembimbing, dan administrator perlu dapat menggunakan sistem secara efektif. Pengelompokan menu berdasarkan fungsi dan peran pengguna dapat membantu menjaga keseimbangan antara kemudahan penggunaan dan kelengkapan fitur.

**Strategi penyeimbangan:**
1. Mengelompokkan menu berdasarkan fungsi, seperti pendaftaran, penempatan desa, bimbingan, laporan, dan penilaian.
2. Menampilkan fitur berdasarkan peran pengguna agar setiap pengguna hanya melihat menu yang relevan.
3. Menggunakan petunjuk dan pesan kesalahan yang jelas pada formulir.
4. Menyediakan navigasi yang konsisten agar pengguna mudah berpindah antarhalaman.
5. Mempertahankan fitur utama dan menghindari penambahan fitur yang tidak diperlukan.
