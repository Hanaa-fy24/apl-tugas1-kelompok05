# A1. Analisis Empat Konteks Arsitektur

Penanggung jawab: [ Ashfy Nur Raihana ]

**Tabel 2.1. Kondisi subsistem Assignment & Assessment KKN Tematik pada empat konteks arsitektur dan pengaruhnya**

| Konteks | Kondisi Subsistem pada Konteks Ini | Pengaruh pada Arsitektur |
|---|---|---|
| **Teknis** | Proses saat ini memakai formulir, spreadsheet, dan grup pesan instan, sedangkan nilai akhir harus diserahkan ke SIAKAD. Sistem menangani data pribadi dan nilai yang sensitif. Penggunaan melonjak saat pendaftaran dan batas laporan. Sebagian mahasiswa di desa memiliki sinyal terbatas. | Memilih basis data relasional dengan transaksi untuk menjaga integritas nilai. Menerapkan kendali akses berbasis peran dan jejak audit. Menjalankan notifikasi dan rekap secara asinkron melalui antrian agar tahan lonjakan beban. Menyediakan antarmuka ringan dengan unggahan berkas yang dapat dilanjutkan. Menyediakan antarmuka ekspor nilai ke SIAKAD. |
| **Siklus hidup proyek** | Pengembangan dilakukan tim kecil dengan waktu terbatas, bertahap per kasus penggunaan (UC-01 sampai UC-05). Sistem harus siap sebelum periode pendaftaran dibuka. Program KKN berulang tiap periode, dan rubrik, kuota, serta format laporan dapat berubah. Pengelola TI terbatas. | Menggunakan monolit modular berlapis dengan batas modul yang jelas, sehingga pekerjaan dapat dibagi, diuji, dan disebarkan sebagai satu unit sederhana. Memisahkan logika aturan dari antarmuka agar mudah diuji. Menjadikan rubrik dan parameter sebagai data konfigurasi sehingga perubahan antar periode tidak memerlukan rilis ulang. |
| **Bisnis** | KKN merupakan bagian dari Tridharma Perguruan Tinggi sehingga universitas membutuhkan pelaksanaan yang rapi dan dapat diaudit. Panitia menanggung beban verifikasi, penempatan, dan rekap nilai secara manual. Penempatan dan nilai kerap dipertanyakan peserta. Anggaran dan tenaga pengelola terbatas, dan mitra desa memiliki literasi digital beragam. | Menjadikan keterlacakan keputusan penempatan dan nilai serta pelaporan capaian sebagai fitur inti. Mengotomatiskan verifikasi, penempatan berbasis aturan, dan rekap nilai. Mengutamakan komponen *open source* dan operasi sederhana, serta menghindari arsitektur terdistribusi yang mahal. Menyediakan akses desa yang terbatas dengan antarmuka sederhana. |
| **Profesional** | Tim berlatar Teknik Informatika dengan pengalaman rekayasa perangkat lunak dan basis data, tetapi pengalaman sistem terdistribusi skala besar terbatas. Praktik yang dianut meliputi pemodelan berbasis pandangan arsitektur dan pencatatan keputusan dengan ADR. Sistem memegang data pribadi serta keputusan yang memengaruhi masa depan akademik peserta. | Memilih teknologi yang sudah dikuasai tim dan berdokumentasi baik untuk menekan risiko teknis. Menyusun dokumentasi arsitektur dan ADR sejak awal. Menerapkan prinsip akses minimal, pemisahan wewenang antar peran, dan pencatatan setiap perubahan nilai demi privasi dan integritas penilaian. |

<!--
CATATAN PENYESUAIAN (hapus sebelum dikumpulkan):
- Sesuaikan baris "Profesional" dengan keahlian dan pengalaman tim yang sebenarnya.
- Jika teknologi tertentu sudah ditetapkan kelompok (misalnya framework dan basis data), sebutkan namanya pada kolom "Pengaruh pada Arsitektur".
-->

<!-- Yang diminta: Tabel 4 baris (teknis, siklus hidup proyek, bisnis, profesional): kondisi subsistem pada tiap konteks dan pengaruhnya pada arsitektur. -->
<!-- Hapus komentar ini setelah bagian selesai. -->

