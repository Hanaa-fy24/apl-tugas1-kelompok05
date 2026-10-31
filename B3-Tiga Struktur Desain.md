# B3. Tiga Struktur Desain Arsitektur

Dokumen ini menjelaskan tiga diagram struktur desain arsitektur perangkat lunak untuk subsistem Layanan KKN Tematik (Membangun Desa) Universitas Muslim Indonesia.

---

### 1. Struktur Modul (*Module Structure*)
* **Deskripsi:** Mengelompokkan elemen-elemen kode program dan logika bisnis ke dalam unit-unit modul fungsional yang terpisah sesuai dengan tanggung jawabnya.
* **Keterangan Penjelasan:**
  1. Modul disusun menjadi tiga lapisan utama: *UI/Presentation Module* (Pendaftaran, Penempatan, Bimbingan, Penilaian), *Business Logic Module* (Manajer Validasi Syarat, Manajer Kuota Desa, Manajer Evaluasi), dan *Data Access Module*.
  2. Pemisahan modul ini mempermudah perawatan dan pembaruan fitur (misal: perubahan aturan pendaftaran atau format nilai) tanpa memengaruhi bagian aplikasi lainnya.
  3. Setiap modul saling berkomunikasi melalui antarmuka (*interface*) yang terdefinisi rapi untuk menjaga *low coupling*.

---

### 2. Struktur Komponen dan Konektor (*Component & Connector / C&C Structure*)
* **Deskripsi:** Menggambarkan komponen-komponen utama yang berjalan (*runtime*) serta jalur komunikasi/konektor di antara mereka saat sistem beroperasi.
* **Keterangan Penjelasan:**
  1. Komponen *Web/Mobile Client* terhubung ke *API Gateway* melalui konektor HTTPS/REST API aman untuk menangani autentikasi pengguna.
  2. *API Gateway* meneruskan permintaan ke *KKN Core Services* yang menangani transaksi data (pendaftaran, penempatan, dan laporan) serta *Auth Service* untuk pengujian hak akses berbasis peran (RBAC).
  3. Komponen layanan terhubung ke *Database Cluster* utama menggunakan konektor JDBC/Connection Pool dengan mekanisme *database transaction* untuk mencegah data ganda atau tersimpan secara tidak lengkap saat lonjakan beban.

---

### 3. Struktur Alokasi (*Allocation Structure*)
* **Deskripsi:** Memetakan elemen software (modul/komponen) ke dalam infrastruktur fisik atau hardware deployment lingkungan kampus.
* **Keterangan Penjelasan:**
  1. Komponen aplikasi di-*deploy* ke dalam beberapa kontainer aplikasi (*Application Server Node*) di bawah *Load Balancer* untuk mendistribusikan lalu lintas data pengguna.
  2. Basis data dihosting di server basis data terpisah (*Primary-Replica DB Nodes*) dengan mekanisme cadangan otomatis (*automated backup storage*) untuk pemulihan bencana teknis.
  3. Struktur ini memastikan keberlangsungan operasi administrasi KKN tetap stabil dan aman meskipun terjadi gangguan pada salah satu simpul server.
