# BAB IV. Penutup

## 4.1 Kesimpulan

Berdasarkan analisis dan perancangan arsitektur pada layanan tugas di subsistem *Assignment & Assessment* SPADA UMI-Kalam FIKOM UMI, dapat disimpulkan beberapa hal berikut:
1. **Layanan dan pemangku kepentingan.** Layanan tugas mencakup pemberian tugas, pengumpulan tugas, pengelolaan tenggat waktu, pemeriksaan kemiripan, serta penilaian dan umpan balik. Terdapat enam pemangku kepentingan utama, dengan dosen dan Ketua Program Studi sebagai pihak yang perlu dikelola paling erat karena memiliki pengaruh dan kepentingan tertinggi.
2. **Batasan dan kebutuhan signifikan.** Perancangan dibatasi oleh integrasi dengan basis data pusat SPADA tanpa mengubah skema inti, batas unggah berkas 25 MB, kepatuhan terhadap kalender akademik, serta pengaturan hak akses berbasis peran. Tiga kebutuhan signifikan arsitektur (ASR) yang dihasilkan adalah kinerja saat lonjakan beban (hingga 500 pengguna bersamaan dengan waktu muat rata-rata kurang dari 3 detik), integritas data dengan rekam jejak audit, serta keamanan dan otorisasi akses berkas.
3. **Karakteristik pendorong.** Tiga karakteristik arsitektur yang paling menentukan adalah *Performance Efficiency*, *Security & Integrity*, dan *Maintainability*. Ketiganya dirumuskan secara terukur, yaitu 95% proses halaman dan unggah selesai dalam waktu kurang dari 3 detik, 100% data nilai dan berkas terenkripsi dengan 0 kerentanan kritis pada sistem otorisasi, serta perubahan aturan bisnis dapat diselesaikan dalam waktu kurang dari 2 hari kerja. Ketiganya juga telah dipetakan ke standar ISO/IEC 25010.
4. **Struktur desain.** Sistem dirancang dalam tiga sudut pandang, yaitu struktur modul (tujuh modul), struktur komponen dan konektor (termasuk *Message Queue*, *Database*, dan *File Storage*), serta struktur alokasi (*Client*, *Application Server*, *Processing Worker*, *Database Server*, dan *File Storage Server*). Pemisahan *Processing Worker* menjaga proses pemeriksaan kemiripan tidak membebani server utama.
5. **Keputusan arsitektur dan trade-off.** Dua keputusan utama yang dicatat dalam ADR adalah penggunaan *Cloud Object Storage* untuk berkas tugas dan *asynchronous message queue* untuk pemeriksaan kemiripan. Analisis trade-off menunjukkan bahwa keamanan didahulukan pada modul nilai dan penyimpanan berkas, kinerja didahulukan pada antarmuka unggah harian, dan skalabilitas penyimpanan diprioritaskan dengan tetap menjaga struktur kode yang modular.

## 4.2 Saran

Berdasarkan hasil perancangan tersebut, saran yang dapat diberikan adalah:
1. **Pengujian sebelum penerapan.** Lakukan pengujian beban (*load testing*) dengan 500 permintaan bersamaan serta *penetration testing* dasar dan pengujian RBAC sebelum sistem digunakan penuh, agar target pada atribut kualitas terukur benar-benar terbukti.
2. **Pemantauan antrean dan penyimpanan.** Sediakan pemantauan status antrean pemeriksaan kemiripan dan akses berkas pada *Object Storage*, karena keputusan arsitektur yang diambil menambah kompleksitas operasional.
3. **Pelibatan pemangku kepentingan.** Libatkan Tim PDTI UMI dan LPMI sejak tahap awal agar kebutuhan infrastruktur dan standar mutu penilaian terpenuhi, serta berikan informasi berkala kepada mahasiswa dan staf administrasi akademik.
4. **Pemeliharaan dokumen ADR.** Perbarui dokumen ADR di repositori setiap ada perubahan keputusan atau regulasi akademik, supaya perdebatan yang sama tidak terulang.
5. **Pengembangan karakteristik lain.** Karakteristik yang belum menjadi pendorong utama, seperti *Availability*, *Reliability*, dan *Usability*, perlu dikaji lebih lanjut pada tahap pengembangan berikutnya.
6. **Penelitian lanjutan.** Rancangan ini dapat dilanjutkan dengan pembuatan prototipe dan validasi terhadap pengguna nyata, lalu dibandingkan dengan target kuantitatif yang telah ditetapkan.
