# Laporan Proyek Machine Learning - Muhammad Rakha Almasah

## Project Overview

Sistem rekomendasi buku adalah alat yang memanfaatkan algoritma untuk menyarankan buku kepada pengguna berdasarkan preferensi dan perilaku mereka. Dalam era digital saat ini, di mana informasi dan pilihan buku sangat melimpah, pembaca sering menghadapi kesulitan dalam menentukan buku apa yang akan dibaca selanjutnya. Hal ini dapat menyebabkan kebingungan dan keputusan yang kurang optimal dalam pemilihan buku.

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

### Solution statements

Untuk mencapai tujuan tersebut, digunakan dua pendekatan utama dalam membangun sistem rekomendasi, yaitu content-based filtering dan collaborative filtering. Berikut adalah penjelasan kedua metode:
- **Solution 1: Content-Based Filtering**

  Pendekatan collaborative filtering bekerja dengan menganalisis pola interaksi pengguna, seperti rating atau ulasan, untuk memberikan rekomendasi. Sistem ini memanfaatkan kemiripan antara pengguna atau item untuk           menghasilkan rekomendasi.

- **Solution 2: Collaborative Filtering**

  Pendekatan collaborative filtering bekerja dengan menganalisis pola interaksi pengguna, seperti rating atau ulasan, untuk memberikan rekomendasi. Sistem ini memanfaatkan kemiripan antara pengguna atau item untuk menghasilkan rekomendasi.

## Data Understanding

### **1. Jumlah dan Kondisi Data**

Dataset yang digunakan dalam proyek ini merupakan dataset rekomendasi buku yang berisi informasi mengenai buku, pengguna, dan interaksi rating antara keduanya. Berikut adalah rincian jumlah data pada masing-masing file:

1. **Books Dataset (`Books.csv`)**:
   - **Jumlah Data**: 271,360 entri
   - **Kolom**: 8 kolom
   - **Informasi Kolom**:
     - `ISBN`: Nomor unik untuk setiap buku.
     - `Book-Title`: Judul buku.
     - `Book-Author`: Nama penulis buku.
     - `Year-Of-Publication`: Tahun publikasi buku.
     - `Publisher`: Penerbit buku.
     - `Image-URL-S`, `Image-URL-M`, `Image-URL-L`: URL gambar sampul buku dalam berbagai resolusi.
   - **Kondisi Data**:
     - Data tidak memiliki nilai duplikasi.
     - Terdapat nilai kosong pada kolom `Book-Author` (2 entri), `Publisher` (2 entri), dan `Image-URL-L` (3 entri).

2. **Ratings Dataset (`Ratings.csv`)**:
   - **Jumlah Data**: 1,149,780 entri
   - **Kolom**: 3 kolom
   - **Informasi Kolom**:
     - `User-ID`: ID unik untuk setiap pengguna.
     - `ISBN`: Nomor unik untuk setiap buku yang dirating.
     - `Book-Rating`: Skor rating yang diberikan pengguna untuk buku (rentang 0-10).
   - **Kondisi Data**:
     - Tidak ada nilai kosong maupun duplikasi pada dataset ini.

3. **Users Dataset (`Users.csv`)**:
   - **Jumlah Data**: 278,858 entri
   - **Kolom**: 3 kolom
   - **Informasi Kolom**:
     - `User-ID`: ID unik untuk setiap pengguna.
     - `Location`: Lokasi pengguna.
     - `Age`: Umur pengguna (opsional).
   - **Kondisi Data**:
     - Kolom `Age` memiliki banyak nilai kosong (110,762 entri).
     - Tidak ada nilai duplikasi pada dataset ini.

### **2. Sumber Data**

- **Dataset Asli**: Dataset dapat diakses di [Kaggle Book Recommendation Dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset).
- **Dataset Siap Digunakan untuk Model Collaborative Filtering**: [Dataset Collaborative Filtering](https://drive.google.com/file/d/1ctcN847pFHwG1MOg8oVyLOXunt-4cV6Q/view?usp=sharing).

### **3. Uraian Variabel**

Berikut adalah penjelasan variabel dalam dataset gabungan yang digunakan untuk analisis dan pemodelan:

| **Variabel**           | **Penjelasan**                                                                                   |
|-------------------------|-------------------------------------------------------------------------------------------------|
| `User-ID`              | ID unik pengguna yang memberikan rating pada buku tertentu.                                     |
| `ISBN`                 | Nomor unik identifikasi buku.                                                                   |
| `Book-Title`           | Judul buku yang dirating oleh pengguna.                                                         |
| `Book-Author`          | Nama penulis buku.                                                                              |
| `Book-Rating`          | Rating (0-10) yang diberikan oleh pengguna untuk buku tertentu.                                 |
| `Publisher`            | Nama penerbit buku.                                                                             |
| `Year-Of-Publication`  | Tahun publikasi buku.                                                                           |
| `Location`             | Lokasi pengguna yang memberikan rating.                                                        |
| `Age`                  | Umur pengguna. (Dihilangkan pada model setelah preprocessing karena banyak nilai kosong).       |

### **4. Visualisasi dan Insight**

#### **4.1 Top 10 Pengguna Paling Aktif**

Grafik ini menunjukkan 10 pengguna yang paling sering memberikan rating.


**Insight**:
- Terdapat beberapa pengguna yang sangat aktif, memberikan ribuan rating, yang dapat menjadi acuan kuat untuk membangun model berbasis *collaborative filtering*.

---

### **5. Exploratory Data Analysis (EDA)**

#### **5.1 Statistik Deskriptif**

**Hasil**:
- `Book-Rating`: Memiliki rata-rata sekitar 5,5, menunjukkan bahwa pengguna cenderung memberikan rating menengah.
- `Year-Of-Publication`: Berkisar dari tahun 1800-an hingga 2000-an, dengan mayoritas buku diterbitkan setelah tahun 1980.

#### **5.2 Missing Value Handling**
- Kolom `Age` memiliki banyak nilai kosong dan akhirnya dihapus dalam proses *preprocessing*.
- Nilai kosong pada kolom `Book-Author` dan `Publisher` dihapus untuk menjaga integritas data.

#### **5.3 Data Sparsity**

**Hasil**:
- Dataset sangat jarang (*sparse*), dengan sebagian besar pengguna tidak memberikan rating pada sebagian besar buku. Hal ini menjadi tantangan untuk model *collaborative filtering*.

---

### **Kesimpulan**

- Dataset memberikan informasi kaya tentang buku, pengguna, dan rating, yang sangat mendukung pengembangan sistem rekomendasi.
- Visualisasi menunjukkan pola penting, seperti pengguna aktif dan buku populer, yang dapat dimanfaatkan untuk membangun model yang lebih efektif.
- Tantangan utama adalah menangani data yang jarang (*sparse*) dan meminimalkan bias terhadap buku-buku populer. 

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
