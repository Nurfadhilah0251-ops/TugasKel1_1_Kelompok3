# A1. Analisis Empat Konteks Arsitektur

<!-- Penanggung jawab: [Nur Fadhilah Fauziah] -->

Tabel di bawah ini menjabarkan kondisi Layanan Tugas Akhir pada subsistem *Assignment & Assessment* di lingkungan Universitas Muslim Indonesia (UMI) berdasarkan empat konteks arsitektur perangkat lunak:

| Konteks Arsitektur | Kondisi Subsistem pada Layanan Tugas Akhir |
| :--- | :--- |
| **1. Teknis (Technical)** | Subsistem mengelola unggahan tugas berkapasitas besar dan mengintegrasikan mesin pemindai teks otomatis untuk pemeriksaan kemiripan (similarity check). Arsitektur dirancang agar komunikasi data antara pengguna dan basis data berjalan aman serta terenkripsi. |
| **2. Siklus Hidup Proyek (Project Life Cycle)** | Pada tahap pengembangan, fokus utama adalah perancangan basis data relasional untuk pengumpulan tugas dan deadline. Pada tahap pemeliharaan, sistem disiapkan untuk skalabilitas tinggi guna menghadapi lonjakan akses saat ujian atau tenggat pengumpulan tugas. |
| **3. Bisnis (Business)** | Layanan ini mendukung efisiensi akademik universitas melalui digitalisasi pengumpulan dan penilaian tugas yang transparan. Proses ini mengurangi penggunaan kertas (paperless) serta memberikan objektivitas dalam rekapitulasi nilai mahasiswa |
| **4. Profesional (Professional)** | Pengembang dan administrator wajib menjaga integritas akademik, keamanan data tugas, serta ketersediaan layanan (uptime) secara konsisten. Standar keamanan diterapkan ketat untuk melindungi kerahasiaan karya ilmiah mahasiswa.|
