# B3. Tiga Struktur Desain

Berikut adalah tiga diagram sederhana pada subsistem Assignment & Assessment yang diklasifikasikan berdasarkan jenis struktur diantaranya : 
## 1. Struktur Modul
Struktur modul menggambarkan pembagian sistem menjadi beberapa modul berdasarkan fungsi dan tanggung jawabnya. Setiap modul memiliki tugas masing-masing agar sistem lebih mudah dikembangkan dan dipelihara. Pertama, Modul Autentikasi berfungsi untuk mengelola proses login serta mengatur hak akses pengguna, baik dosen maupun mahasiswa, agar setiap pengguna dapat mengakses fitur sesuai dengan perannya. Kedua, Modul Pengelolaan Tugas digunakan oleh dosen untuk membuat, mengubah, dan menghapus tugas, termasuk memberikan deskripsi serta instruksi pengerjaan. Selanjutnya, Modul Pengumpulan Tugas berfungsi untuk mengelola proses pengunggahan jawaban oleh mahasiswa serta mencatat status pengumpulan tugas, sehingga dosen dapat mengetahui mahasiswa yang sudah maupun belum mengumpulkan tugas.
Selain itu, terdapat Modul Tenggat Waktu yang bertugas mengatur batas waktu pengumpulan dan menentukan status keterlambatan mahasiswa. Untuk mendukung keaslian hasil pengerjaan, Modul Pemeriksaan Kemiripan digunakan untuk membandingkan dokumen tugas mahasiswa dan menghasilkan persentase kemiripan yang dapat dijadikan bahan evaluasi oleh dosen. Sistem juga dilengkapi dengan Modul Notifikasi yang berfungsi memberikan pemberitahuan kepada dosen dan mahasiswa mengenai tugas baru, pengingat tenggat waktu, serta informasi status pengumpulan. Terakhir, Modul Laporan digunakan untuk menampilkan rekapitulasi pengumpulan tugas dan hasil pemeriksaan kemiripan, sehingga dosen dapat memantau serta mengevaluasi aktivitas pengumpulan tugas mahasiswa secara lebih mudah.

## 2. Struktur Komponen dan Konektor (C&C)
Struktur komponen dan konektor menggambarkan bagaimana komponen sistem saling berinteraksi ketika sistem sedang berjalan (runtime). Komponen merupakan bagian yang menjalankan fungsi tertentu, sedangkan konektor merupakan penghubung komunikasi dan pertukaran data antarkomponen.

## 3. Struktur Alokasi
Struktur alokasi menggambarkan bagaimana komponen atau modul perangkat lunak ditempatkan pada infrastruktur perangkat keras, server, maupun lingkungan pengembangan dan operasional.


