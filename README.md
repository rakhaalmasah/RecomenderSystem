# Laporan Proyek Machine Learning - Muhammad Rakha Almasah

## Project Overview

Sistem rekomendasi buku adalah alat yang memanfaatkan algoritma untuk menyarankan buku kepada pengguna berdasarkan preferensi dan perilaku mereka. Dalam era digital saat ini, di mana informasi dan pilihan buku sangat melimpah, pembaca sering menghadapi kesulitan dalam menentukan buku apa yang akan dibaca selanjutnya. Hal ini dapat menyebabkan kebingungan dan keputusan yang kurang optimal dalam pemilihan buku.

**Rubrik/Kriteria Tambahan (Opsional)**:

Penerapan sistem rekomendasi buku menjadi penting karena beberapa alasan:
  1. Meningkatkan Pengalaman Pengguna: Dengan memberikan saran buku yang sesuai dengan minat dan preferensi individu, sistem ini membantu pembaca menemukan buku yang relevan dan menarik, sehingga meningkatkan kepuasan dan keterlibatan mereka.
  2. Mengatasi Informasi yang Berlebihan: Di tengah banyaknya pilihan buku yang tersedia, sistem rekomendasi membantu menyaring dan menyoroti buku-buku yang paling sesuai dengan kebutuhan dan minat pengguna, mengurangi beban dalam proses pemilihan.
  3. Meningkatkan Penjualan dan Promosi Buku: Bagi penerbit dan penjual buku, sistem rekomendasi dapat mendorong penjualan dengan menampilkan buku-buku yang mungkin tidak ditemukan oleh pembaca tanpa bantuan teknologi tersebut. 
  4. Personalisasi Konten: Sistem ini memungkinkan personalisasi yang lebih dalam, memberikan saran berdasarkan riwayat membaca, preferensi genre, dan bahkan suasana hati pengguna, sehingga setiap rekomendasi menjadi lebih relevan dan tepat sasaran. 

Penelitian sebelumnya telah menunjukkan efektivitas metode item-based collaborative filtering dan content-based filtering dalam sistem rekomendasi buku, yang memberikan rekomendasi berdasarkan kemiripan antar buku dan preferensi pengguna (Ritdrix & Wirawan, 2018).  Metode content-based filtering juga telah diterapkan untuk memberikan rekomendasi buku berdasarkan preferensi pengguna, dengan mengukur keakuratan rekomendasi yang diberikan" (Universitas Airlangga, 2023, p. 12).

Dengan demikian, pengembangan sistem rekomendasi buku yang efektif tidak hanya meningkatkan pengalaman membaca bagi pengguna, tetapi juga memberikan manfaat signifikan bagi industri penerbitan dan penjualan buku.

  Referensi :
  
  [Sistem Rekomendasi Buku Menggunakan Metode Item-Based Collaborative Filtering](https://ejournal.undip.ac.id/index.php/jmasif/article/view/31482)
  
  [Meningkatkan Layanan Perpustakaan dengan Kecerdasan Buatan](https://unair.ac.id/meningkatkan-layanan-perpustakaan-dengan-kecerdasan-buatan/) 

## Business Understanding

Bagian laporan ini mencakup:

### Problem Statements

Dalam era informasi, pengguna sering kali menghadapi kesulitan dalam menemukan buku yang sesuai dengan preferensi mereka dari jumlah koleksi yang sangat besar. Masalah utama yang muncul adalah:

- Overload Informasi: Dengan jutaan buku yang tersedia secara online maupun offline, pengguna menghadapi kesulitan dalam menemukan buku yang relevan tanpa bantuan sistem rekomendasi yang efektif.
- Preferensi yang Berbeda: Setiap pengguna memiliki preferensi yang unik, baik berdasarkan penulis favorit, genre, maupun penilaian dari pembaca lain.
- Pengalaman Pengguna Baru (Cold Start): Pengguna baru yang belum memberikan banyak rating atau interaksi dengan sistem sering kali tidak mendapatkan rekomendasi yang sesuai.

Tanpa sistem rekomendasi yang andal, pengguna mungkin merasa kewalahan dan akhirnya meninggalkan platform karena tidak menemukan buku yang sesuai dengan minat mereka.

### Goals

Tujuan dari proyek ini adalah untuk membangun sistem rekomendasi buku berbasis machine learning yang dapat:

- Memberikan Rekomendasi Buku yang Relevan: Menghasilkan rekomendasi buku yang sesuai dengan preferensi individu pengguna.
- Mengurangi Cold Start Problem: Menyediakan rekomendasi yang bermanfaat bahkan untuk pengguna baru dengan data interaksi yang terbatas.
- Meningkatkan Pengalaman Pengguna: Membuat pengalaman pengguna lebih personal dengan menghadirkan buku-buku yang menarik dan relevan.
- Meningkatkan Retensi Pengguna: Dengan pengalaman yang lebih baik, sistem dapat mempertahankan lebih banyak pengguna dalam platform.

**Rubrik/Kriteria Tambahan (Opsional)**:

### Solution statements

Untuk mencapai tujuan tersebut, digunakan dua pendekatan utama dalam membangun sistem rekomendasi, yaitu content-based filtering dan collaborative filtering. Berikut adalah penjelasan kedua metode:
- Solution 1: Content-Based Filtering

  Pendekatan collaborative filtering bekerja dengan menganalisis pola interaksi pengguna, seperti rating atau ulasan, untuk memberikan rekomendasi. Sistem ini memanfaatkan kemiripan antara pengguna atau item untuk           menghasilkan rekomendasi.

- Solution 2: Collaborative Filtering

  Pendekatan collaborative filtering bekerja dengan menganalisis pola interaksi pengguna, seperti rating atau ulasan, untuk memberikan rekomendasi. Sistem ini memanfaatkan kemiripan antara pengguna atau item untuk menghasilkan rekomendasi.

## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai jumlah data, kondisi data, dan informasi mengenai data yang digunakan. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
