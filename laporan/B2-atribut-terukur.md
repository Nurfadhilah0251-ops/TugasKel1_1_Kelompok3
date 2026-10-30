# B2. Atribut Kualitas yang Terukur

<!-- Penanggung jawab: [ST. Nabila Azira Zamzani A] -->

Berikut adalah rumusan ukuran kuantitatif terukur untuk 3 karakteristik pendorong utama pada Layanan SPADA-UMI (subsistem *Assignment & Assessment*), yang mencakup angka target, kondisi pengukuran, dan cara pengujiannya:

| No | Karakteristik Pendorong | Angka Target Kuantitatif | Kondisi Pengukuran | Cara Menguji |
| :--- | :--- | :--- | :--- | :--- |
| 1 | **Performance Efficiency** | **95%** halaman layanan dan proses unggah berkas tugas mahasiswa **(< 25 MB)** selesai dalam waktu **< 3 detik.** | Dites pada saat jam sibuk, misalnya saat 500 mahasiswa dan dosen bareng-bareng akses sistem pas mendekati tenggat waktu (deadline) pengumpulan tugas. | Dilakukan pengujian beban (load testing) menggunakan tool seperti JMeter atau k6 sebelum modul di-deploy ke server utama. |
| 2 | **Security & Integrity** | **100%** data nilai tugas dan berkas laporan terenkripsi dengan standar keamanan tinggi dan 0 celah kerentanan kritis (*critical vulnerability*) pada sistem otorisasi.| Saat proses penginputan nilai oleh dosen pengampu dan pengunggahan berkas tugas/praktikum oleh mahasiswa FIKOM UMI. | Dilakukan Penetration Testing dasar dan pengujian kontrol akses berbasis peran (*Role-Based Access Control* / RBAC). |
| 3 | **Maintainability** | Penyesuaian atau perubahan aturan logika bisnis (misalnya aturan batas waktu deadline atau rubrik penilaian baru) dapat diselesaikan dalam waktu < 2 hari kerja tanpa memengaruhi modul lainnya. | Saat terjadi pembaruan pedoman akademik atau penyesuaian regulasi penilaian tugas akhir dari pihak fakultas atau universitas. | Dilakukan simulasi pengujian perubahan kode (*change scenario testing*) dan audit tingkat modularitas (*code coupling*). |
