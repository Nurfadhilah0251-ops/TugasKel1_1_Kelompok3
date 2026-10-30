# B3. Tiga Struktur Desain

Berikut adalah tiga diagram sederhana pada subsistem Assignment & Assessment yang diklasifikasikan berdasarkan jenis struktur diantaranya : 
## 1. Struktur Modul
Struktur modul menggambarkan pembagian sistem menjadi beberapa modul berdasarkan fungsi dan tanggung jawabnya. Setiap modul memiliki tugas masing-masing agar sistem lebih mudah dikembangkan dan dipelihara.

<img width="223" height="127" alt="image" src="https://github.com/user-attachments/assets/bfbbe0ea-343c-4ef6-bcce-7490e8515e50" />

#### Alasan pemilihan struktur : 
Pembagian modul membuat setiap fungsi memiliki tanggung jawab yang jelas. Misalnya, proses pengumpulan tugas tidak perlu digabungkan dengan proses pemeriksaan kemiripan. Dengan demikian, ketika terjadi perubahan pada fitur pemeriksaan dokumen, modul pengumpulan tugas tidak harus mengalami perubahan besar.

## 2. Struktur Komponen dan Konektor (C&C)
Struktur komponen dan konektor menggambarkan bagaimana komponen sistem saling berinteraksi ketika sistem sedang berjalan (runtime). Komponen merupakan bagian yang menjalankan fungsi tertentu, sedangkan konektor merupakan penghubung komunikasi dan pertukaran data antarkomponen.

<img width="221" height="128" alt="image" src="https://github.com/user-attachments/assets/802b7880-7fbe-4f47-9ab4-5bb11da02c5b" />

#### Alasan pemilihan struktur : 
Struktur ini memungkinkan setiap komponen berkomunikasi sesuai tanggung jawabnya. Contohnya, ketika mahasiswa mengunggah tugas, Submission Service memvalidasi tenggat melalui Deadline Service, menyimpan dokumen ke File Storage, kemudian memasukkan permintaan pemeriksaan ke Message Queue. Pemeriksaan kemiripan dilakukan secara asinkron sehingga proses tersebut tidak menghambat mahasiswa ketika mengumpulkan tugas.

## 3. Struktur Alokasi
Struktur alokasi menggambarkan bagaimana komponen atau modul perangkat lunak ditempatkan pada infrastruktur perangkat keras, server, maupun lingkungan pengembangan dan operasional.

<img width="455" height="67" alt="image" src="https://github.com/user-attachments/assets/48e0b962-7df8-47b0-82ab-bdd2b241b475" />

#### Alasan pemilihan struktur : 
Pemisahan penempatan komponen memungkinkan beban kerja sistem dibagi sesuai kebutuhan. Application Server menangani permintaan pengguna, sedangkan Processing Server secara khusus menangani pemeriksaan kemiripan dokumen. Dengan demikian, ketika banyak mahasiswa mengunggah tugas secara bersamaan, proses pemeriksaan kemiripan dapat berjalan melalui server pemrosesan tanpa terlalu membebani layanan utama.


## Hubungan Ketiga Struktur Desain
Ketiga struktur tersebut saling melengkapi dalam menggambarkan arsitektur sistem.

|  Struktur Desain |  Fokus Utama |  Contoh Penerapan |
|:---------------- |:------------ |:----------------- |
| Struktur Modul   | Pembagian Fungsi Sistem | Modul pengumpulan, tenggat, dan pemeriksaan kemiripan |
| Struktur Komponen dan Konektor | Interaksi antarkomponen | Submission Service berkomunikasi dengan Database dan Message Queue |
| Struktur Alokasi | Penempatan komponen | Similarity Service ditempatkan pada Processing Server |
