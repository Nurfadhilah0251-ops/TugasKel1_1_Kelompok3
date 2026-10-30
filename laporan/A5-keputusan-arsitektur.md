# A5. Keputusan Arsitektur dan ADR

<!-- Penanggung jawab: [Nur Afifah] -->

Berikut adalah dua dokumen Architecture Decision Record (ADR) untuk Layanan Tugas pada subsistem Assignment & Assessment di SPADA UMI-Kalam FIKOM UMI, beserta penjelasan rencana komunikasi kelompok untuk menghindari anti-pattern dalam pengambilan keputusan arsitektur.

---

## 1. Arsitektur Decision Record (ADR)

### ADR-001: Penggunaan Cloud Object Storage untuk Penyimpanan Berkas Draf Tugas Akhir
* **Status:** Accepted
* **Context:** Mahasiswa FIKOM UMI mengunggah dokumen tugas, laporan praktikum, serta file pendukung berukuran hingga 25 MB per dokumen. Jika disimpan langsung di direktori lokal server aplikasi utama SPADA, kapasitas penyimpanan server akan cepat penuh dan berisiko mengganggu kinerja basis data relasional saat terjadi unggah massal menjelang batas waktu (deadline).
* **Decision:** Kami akan menggunakan layanan Cloud Object Storage terpusat yang terisolasi khusus untuk menampung seluruh berkas digital tugas mahasiswa.
* **Consequences:** 
  * *Untung:* Skalabilitas penyimpanan tinggi, aman, dan tidak membebani database relasional utama SPADA UMI-Kalam.
  * *Rugi:* Memerlukan tambahan konfigurasi jaringan aman (SDK/API khusus) serta manajemen otorisasi akses unduh berkas yang ketat.
* **Compliance:** Ditinjau setiap akhir semester dan diuji melalui pemeriksaan integritas tautan unggah dokumen sebelum masa pendaftaran sidang dimulai.

### ADR-002: Implementasi Asynchronous Message Queue untuk Proses Pemeriksaan Kemiripan (Similarity Check)
* **Status:** Accepted
* **Context:* *Proses pemindaian teks dan pemeriksaan kemiripan (similarity check) dokumen tugas mahasiswa memerlukan waktu komputasi yang cukup berat. Jika dijalankan secara langsung (synchronous), proses ini akan membuat server mengalami bottleneck dan memperlambat respons antarmuka saat banyak mahasiswa mengunggah tugas secara bersamaan.
* **Decision:* *Kami akan mengimplementasikan antrean pesan asinkron (asynchronous message queue seperti RabbitMQ atau Redis Queue) untuk memproses antrean pemeriksaan plagiarisme di latar belakang (background worker).
* **Consequences:** 
  * *Untung:* Menjaga performa antarmuka web tetap responsif bagi mahasiswa dan dosen meskipun server sedang memproses banyak file besar.
  * *Rugi:* Kompleksitas arsitektur meningkat karena memerlukan pemantauan tambahan terhadap status antrean tugas (queue monitoring).
* **Compliance:** Diuji melalui simulasi beban (load testing) dengan mengirimkan 500 permintaan unggah bersamaan sebelum sistem di-deploy secara penuh di lingkungan FIKOM UMI.
---

## 2. Rencana Komunikasi dan Pencegahan Anti-Pattern

Untuk memastikan pengambilan keputusan arsitektur berjalan objektif dan terhindar dari jebakan anti-pattern (seperti Design by Committee atau Architecture Astronauts), kelompok kami menerapkan mekanisme komunikasi berikut:

* **Penyimpanan Dokumen ADR:** Seluruh dokumen ADR disimpan secara transparan di dalam folder /adr pada repository GitHub kelompok, sehingga setiap anggota dapat meninjau, melacak perubahan, serta menyesuaikannya dengan kebutuhan teknis nyata di lingkungan FIKOM UMI.
* **Saluran Pemberitahuan:** Anggota tim diberi tahu mengenai adanya keputusan atau pembaruan ADR melalui pesan singkat (instant messaging) berupa tautan langsung ke berkas terkait di repository, bukan melalui isi email yang rentan terabaikan.
* **Pencegahan Tiga Anti-Pattern Keputusan Arsitektur:**
  1. *Covering Your Assets (CYA):* Menghindari pembuatan keputusan arsitektur yang terlalu rumit atau berlebihan (misalnya penggunaan teknologi yang tidak diperlukan) hanya untuk menghindari disalahkan; setiap keputusan harus berdasarkan kebutuhan nyata mahasiswa dan dosen FIKOM UMI (ASR).
  2. *Groundhog Day:* Menghindari perdebatan berulang terhadap masalah yang sama (seperti penentuan batas ukuran file tugas atau metode similarity check) dengan cara mendokumentasikan alasan dan konteks keputusan secara jelas di dalam format ADR.
  3. *Email-Driven Architecture:* Menghindari keputusan arsitektur yang hanya diputuskan lewat percakapan pribadi; seluruh keputusan teknis wajib dicatat secara resmi melalui Pull Request atau commit berkas markdown di dalam repository kelompok.
