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

---

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

![Top 10 Pengguna Paling Aktif](https://raw.githubusercontent.com/rakhaalmasah/RecomenderSystem/main/download.png)

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

---

## Data Preparation

Tahapan ini menjelaskan langkah-langkah untuk mempersiapkan dataset sebelum digunakan dalam model *machine learning*. Data preparation bertujuan untuk memastikan data siap digunakan, bersih, dan dalam format yang sesuai dengan kebutuhan algoritma. Berikut adalah tahapan yang dilakukan:

---

### **1. Identifikasi Masalah Data**

Dataset mentah yang digunakan mencakup tiga file: `Books.csv`, `Ratings.csv`, dan `Users.csv`. Masalah utama yang ditemukan pada dataset adalah:
- **Missing Values**: Kolom seperti `Book-Author` dan `Image-URL-L` di `Books.csv` mengandung nilai kosong.
- **Redundansi Kolom**: Kolom yang tidak relevan seperti `Image-URL-S`, `Image-URL-M`, dan `Image-URL-L` tidak diperlukan untuk membangun model.
- **Outliers pada Umur Pengguna**: Kolom `Age` pada `Users.csv` mengandung nilai tidak realistis, seperti `0` dan nilai yang sangat besar.
- **Duplikasi Data**: Beberapa baris mungkin redundan dan perlu dihapus.

---

### **2. Langkah-Langkah Data Preparation**

#### **2.1. Penanganan Missing Values**
- **Langkah:**
  - Missing values dihapus menggunakan fungsi `dropna()` pada dataset `Books.csv`.
- **Alasan:**
  - Data yang hilang dapat menyebabkan kesalahan dalam model, terutama jika kolom seperti `Book-Author` yang penting untuk *content-based filtering* mengandung nilai kosong.

#### **2.2. Penghapusan Kolom Tidak Relevan**
- **Langkah:**
  - Kolom `Image-URL-S`, `Image-URL-M`, dan `Image-URL-L` dihapus karena tidak relevan untuk rekomendasi buku.
- **Alasan:**
  - Kolom ini hanya menyimpan URL gambar sampul buku dan tidak berkontribusi pada analisis atau model.

#### **2.3. Normalisasi Rating**
- **Langkah:**
  - Kolom `Book-Rating` dinormalisasi ke skala 0-1 dengan membagi nilai rating dengan 10.
- **Alasan:**
  - Normalisasi memudahkan model untuk belajar secara konsisten, terutama untuk algoritma seperti *collaborative filtering* yang mengasumsikan input numerik berada dalam skala yang seragam.

#### **2.4. Encoding Data**
- **Langkah:**
  - Kolom `User-ID` dan `ISBN` dienkode menjadi indeks integer menggunakan `astype('category').cat.codes`.
- **Alasan:**
  - Algoritma seperti *collaborative filtering* membutuhkan representasi data dalam format numerik agar dapat diproses dengan cepat.

#### **2.5. Penggabungan Dataset**
- **Langkah:**
  - Dataset `Books.csv`, `Ratings.csv`, dan `Users.csv` digabungkan menggunakan `merge()` pada kolom `ISBN` dan `User-ID`.
- **Alasan:**
  - Model rekomendasi membutuhkan informasi pengguna, buku, dan rating dalam satu dataset agar dapat digunakan secara efektif.

#### **2.6. Pembuatan Metadata**
- **Langkah:**
  - Untuk *content-based filtering*, kolom `metadata` dibuat dengan menggabungkan `Book-Title`, `Book-Author`, dan `Publisher`.
- **Alasan:**
  - Metadata digunakan untuk merepresentasikan setiap buku sebagai teks yang dapat dianalisis menggunakan teknik seperti *TF-IDF vectorization*.

---

### **3. Penerapan Teknik Data Preparation**

#### **Langkah-Langkah yang Dilakukan:**

1. **Handling Missing Values**

```python
# Menghapus baris yang memiliki nilai NaN
books_cleaned = books.dropna()
users_cleaned = users.drop(columns=['Age'])  # Menghapus kolom Age dengan banyak nilai kosong
```

2. **Penghapusan Kolom Tidak Relevan**

```python
# Menghapus kolom yang tidak diperlukan
books_cleaned = books_cleaned.drop(columns=['Image-URL-S', 'Image-URL-M', 'Image-URL-L'])
```

3. **Normalisasi Rating**

```python
# Normalisasi nilai rating
data['Book-Rating'] = data['Book-Rating'] / 10.0
```

4. **Encoding Data**

```python
# Encoding User-ID dan ISBN menjadi indeks numerik
data['user_idx'] = data['User-ID'].astype('category').cat.codes.values
data['book_idx'] = data['ISBN'].astype('category').cat.codes.values
```

5. **Penggabungan Dataset**

```python
# Menggabungkan dataset
ratings_books = ratings.merge(books_cleaned, on='ISBN', how='inner')
ratings_books_users = ratings_books.merge(users_cleaned, on='User-ID', how='inner')
```

6. **Pembuatan Metadata**

```python
# Membuat metadata untuk content-based filtering
data['metadata'] = data['Book-Title'] + ' ' + data['Book-Author'] + ' ' + data['Publisher']
data['metadata'] = data['metadata'].fillna('')  # Handle NaN values
```

---

### **4. Hasil Data Preparation**

#### **Dataset Hasil Data Preparation**

- Dataset setelah pembersihan terdiri dari:
  - **1031128 baris**.
  - **8 kolom**, yaitu `User-ID`, `ISBN`, `Book-Rating`, `Book-Title`, `Book-Author`, `Year-Of-Publication`, `Publisher`, dan `Location`.

#### **Tautan Dataset yang Siap Digunakan**
- Dataset setelah data preparation: [Google Drive](https://drive.google.com/file/d/1ctcN847pFHwG1MOg8oVyLOXunt-4cV6Q/view?usp=sharing)

---

### **5. Alasan Data Preparation Diperlukan**

1. **Konsistensi Data**
   - Data yang bersih dan lengkap memudahkan model untuk belajar dengan lebih baik.
2. **Efisiensi Proses**
   - Normalisasi dan encoding data membantu dalam mempercepat waktu komputasi.
3. **Mengatasi *Cold Start Problem***
   - Metadata yang dibuat memungkinkan rekomendasi untuk pengguna baru dengan data rating yang terbatas.
4. **Meningkatkan Akurasi Model**
   - Data yang relevan dan bebas dari noise meningkatkan performa model dalam memberikan rekomendasi.

---

## Modeling

Pada bab ini, dua pendekatan utama digunakan untuk membangun sistem rekomendasi, yaitu *collaborative filtering* dan *content-based filtering*. Setiap pendekatan memiliki algoritma, hasil, serta kelebihan dan kekurangan yang akan dijelaskan secara terpisah.

---

### **1. Collaborative Filtering**

#### **Penjelasan Algoritma**
*Collaborative filtering* menggunakan data interaksi pengguna dan item (buku) untuk memberikan rekomendasi berdasarkan pola yang ditemukan dari data tersebut.

1. **Input Data:**
   - Dataset berisi informasi *user-item* (pengguna-buku) dan nilai rating yang diberikan pengguna.
   - Data dienkode menjadi representasi numerik (`user_idx` dan `book_idx`) untuk diproses oleh model.

2. **Arsitektur Model:**
   - **Embedding Layer:** Representasi numerik pengguna dan buku diubah menjadi vektor berdimensi tinggi untuk menangkap hubungan laten antar entitas.
   - **Fully Connected Layers:** Vektor embedding diproses melalui beberapa lapisan tersembunyi untuk menghasilkan prediksi rating.
   - **Loss Function:** *Weighted Mean Squared Error (WMSE)* digunakan untuk memberikan bobot lebih pada rating yang lebih tinggi.
   - **Optimizer:** *Adam optimizer* dipilih untuk mempercepat proses konvergensi.

3. **Hasil Training:**
   - Model dilatih selama 7 epoch sebelum mekanisme *early stopping* menghentikan pelatihan untuk menghindari overfitting.
   - Grafik *training loss* dan *validation loss* menunjukkan performa model selama proses pelatihan.

#### **Hasil Model**

1. **Top-N Recommendation**
   - Model menghasilkan rekomendasi buku untuk pengguna tertentu. Berikut adalah hasil rekomendasi untuk dua pengguna:
     - **User-ID: 11676**
       ![Recommendation for User-ID 11676](https://raw.githubusercontent.com/rakhaalmasah/RecomenderSystem/e53ad572ad130d9bb053926a12fe8d0eb1638b41/Rekomendasi_11676.png)
     - **User-ID: 198711**
       ![Recommendation for User-ID 198711](https://raw.githubusercontent.com/rakhaalmasah/RecomenderSystem/e53ad572ad130d9bb053926a12fe8d0eb1638b41/Rekomendasi_198711.png)

#### **Kelebihan dan Kekurangan Collaborative Filtering**

| **Kelebihan**                                     | **Kekurangan**                                                 |
|---------------------------------------------------|----------------------------------------------------------------|
| Memberikan rekomendasi yang dipersonalisasi.      | Membutuhkan data interaksi yang cukup besar.                  |
| Menggunakan hubungan laten untuk mengungkap pola. | Rentan terhadap *cold start problem* untuk pengguna atau item baru. |
| Cocok untuk dataset besar dengan banyak pengguna. | Membutuhkan waktu komputasi lebih lama untuk pelatihan model. |

---

### **2. Content-Based Filtering**

#### **Penjelasan Algoritma**
*Content-based filtering* memberikan rekomendasi berdasarkan kesamaan konten, seperti penulis buku atau atribut lain.

1. **Input Data:**
   - Metadata dari buku, seperti `Book-Title`, `Book-Author`, dan `Publisher`.
   - Metadata ini digabungkan menjadi satu kolom bernama `metadata`.

2. **Proses Algoritma:**
   - **TF-IDF Vectorization:** Metadata buku diubah menjadi representasi numerik berdasarkan bobot kata unik.
   - **Cosine Similarity:** Digunakan untuk menghitung kesamaan antar buku berdasarkan vektor TF-IDF.

3. **Fungsi Rekomendasi:**
   - Fungsi mencari buku dengan kesamaan tertinggi berdasarkan *cosine similarity* dan mengembalikan daftar buku yang mirip.

#### **Hasil Model**

1. **Top-N Recommendation**
   - Hasil rekomendasi untuk dua judul buku:
     - **Judul: "Harry Potter and the Order of the Phoenix"**
       ![Content-Based Recommendation for Harry Potter](https://raw.githubusercontent.com/rakhaalmasah/RecomenderSystem/e53ad572ad130d9bb053926a12fe8d0eb1638b41/Content%20Hary%20Potter.png)
     - **Judul: "Along Came a Spider (Alex Cross Novels)"**
       ![Content-Based Recommendation for Along Came a Spider](https://raw.githubusercontent.com/rakhaalmasah/RecomenderSystem/e53ad572ad130d9bb053926a12fe8d0eb1638b41/A%20long%20came_content.png)

#### **Kelebihan dan Kekurangan Content-Based Filtering**

| **Kelebihan**                                     | **Kekurangan**                                                 |
|---------------------------------------------------|----------------------------------------------------------------|
| Tidak memerlukan data interaksi antar pengguna.   | Rentan terhadap masalah *overspecialization* (rekomendasi terlalu serupa). |
| Cocok untuk pengguna baru dengan sedikit data.    | Tidak mempertimbangkan pola perilaku antar pengguna.          |
| Mudah diimplementasikan dengan metadata buku.     | Membutuhkan metadata yang lengkap dan akurat.                |

---

### **Kesimpulan**

1. **Collaborative Filtering**
   - Cocok untuk menghasilkan rekomendasi personalisasi tinggi berdasarkan interaksi pengguna.
   - Memiliki keterbatasan pada pengguna baru atau item dengan data interaksi minim (*cold start problem*).

2. **Content-Based Filtering**
   - Memberikan rekomendasi berdasarkan kemiripan konten, sehingga berguna untuk pengguna baru.
   - Terbatas pada kesamaan atribut tanpa memperhitungkan perilaku atau preferensi pengguna lain.

Pemilihan algoritma bergantung pada kebutuhan dan ketersediaan data. Kombinasi kedua metode (hybrid approach) dapat digunakan untuk memaksimalkan performa sistem rekomendasi.

---

## **Evaluation**

Evaluasi dilakukan untuk mengukur kinerja dua pendekatan sistem rekomendasi yang telah diterapkan, yaitu *collaborative filtering* dan *content-based filtering*. Setiap metode dievaluasi dengan cara yang sesuai untuk menunjukkan relevansi dan kualitas rekomendasi.

---

### **1. Evaluasi Collaborative Filtering**

#### **Metrik: Weighted Mean Squared Error (Weighted MSE)**

**Weighted MSE** digunakan untuk mengevaluasi prediksi rating yang dihasilkan oleh model *collaborative filtering*. Metrik ini memberikan bobot lebih tinggi pada rating non-nol, karena rating non-nol mencerminkan preferensi eksplisit pengguna, sehingga dianggap lebih penting.

#### **Formula Weighted MSE**
$$
\text{Weighted MSE} = \frac{1}{n} \sum_{i=1}^n w_i (y_i - \hat{y}_i)^2
$$

- **$y_i$**: Rating aktual.
- **$\hat{y}_i$**: Rating yang diprediksi oleh model.
- **$w_i$**: Bobot untuk setiap sampel:
  - **5.0** untuk rating non-nol (preferensi eksplisit pengguna).
  - **1.0** untuk rating nol.
- **$n$**: Jumlah data.

#### **Evaluasi dan Hasil**
- Model melatih embedding pengguna dan buku menggunakan data rating untuk memprediksi nilai rating.
- Perbedaan antara rating aktual dan prediksi dihitung dan diperhitungkan sesuai bobotnya.

**Hasil Evaluasi:**
- **Training Loss:** 0.0011
- **Validation Loss:** 0.0010

![Training vs Validation Loss](https://raw.githubusercontent.com/rakhaalmasah/RecomenderSystem/e53ad572ad130d9bb053926a12fe8d0eb1638b41/training%20val%20loss.png)

**Interpretasi:**
- **Training Loss** dan **Validation Loss** menunjukkan bahwa model dapat mempelajari data tanpa overfitting.
- Nilai Weighted MSE yang rendah menunjukkan prediksi model mendekati nilai aktual, terutama untuk rating non-nol.
---

### **2. Evaluasi Content-Based Filtering**

Pendekatan *content-based filtering* dievaluasi dengan cara mengamati hasil rekomendasi yang diberikan untuk buku tertentu, tanpa melibatkan data pengguna secara langsung. Evaluasi difokuskan pada kesesuaian atribut konten (penulis) antara buku input dan rekomendasi.

#### **Hasil Evaluasi**
Berikut adalah contoh hasil rekomendasi untuk buku input:

- **Judul Buku Input:** *"Harry Potter a l'ecole des sorciers"*

Hasil rekomendasi:
| **Book-Title**                                      | **Book-Author**  |
|-----------------------------------------------------|------------------|
| Harry Potter and the Sorcerer's Stone (Book 1)      | J. K. Rowling    |
| Harry Potter and the Prisoner of Azkaban (Book 3)   | J. K. Rowling    |
| Harry Potter y el cáliz de fuego                    | J. K. Rowling    |
| Harry Potter et la chambre des secrets              | J. K. Rowling    |
| Harry Potter a l'ecole des sorciers                 | J. K. Rowling    |

---

### **3. Perbandingan Dua Pendekatan**

| **Aspek**                | **Collaborative Filtering**                              | **Content-Based Filtering**                                   |
|--------------------------|--------------------------------------------------------|------------------------------------------------------------|
| **Evaluasi Utama**       | Weighted Mean Squared Error (Weighted MSE)              | Observasi Hasil Rekomendasi (Kesamaan Atribut Konten)       |
| **Relevansi Rekomendasi**| Berdasarkan pola rating pengguna dan interaksi historis | Berdasarkan kesamaan atribut konten (penulis atau metadata) |
| **Kelebihan**            | Personal dan memanfaatkan pola perilaku pengguna lainnya| Tidak memerlukan data pengguna lain (cocok untuk pengguna baru) |
| **Kelemahan**            | Tidak dapat merekomendasikan untuk item baru (*cold start*)| Rentan terhadap masalah *overspecialization*               |

---

### **Kesimpulan**
1. **Collaborative Filtering** menghasilkan rekomendasi yang sangat personal tetapi memerlukan data interaksi yang memadai.
2. **Content-Based Filtering** memberikan rekomendasi berdasarkan atribut konten, cocok untuk pengguna baru atau item baru.
3. Kombinasi kedua pendekatan dalam *hybrid recommendation system* dapat mengatasi kekurangan masing-masing metode untuk hasil yang lebih optimal.

---

## **Penutup**

Bab ini membahas dampak model yang telah dievaluasi terhadap *business understanding* berdasarkan analisis evaluasi. Selain itu, kesimpulan juga mencakup apakah pendekatan yang digunakan berhasil menjawab *problem statement*, mencapai *goals*, dan memberikan dampak positif sesuai dengan *solution statement* yang direncanakan.

---

### **1. Apakah Sudah Menjawab Problem Statement?**

**Problem Statement:**
- Bagaimana memberikan rekomendasi buku yang relevan bagi pengguna dengan memanfaatkan data rating dan metadata buku?

**Analisis:**
- **Collaborative Filtering:** Model ini menjawab *problem statement* dengan memberikan rekomendasi berdasarkan pola rating pengguna lain yang serupa. Hal ini memungkinkan sistem memberikan rekomendasi yang sangat personal.
  - Contoh hasil rekomendasi untuk pengguna ID tertentu menunjukkan bahwa model dapat mengidentifikasi buku yang sesuai dengan preferensi pengguna tersebut, berdasarkan interaksi historis.
- **Content-Based Filtering:** Model ini menjawab *problem statement* dengan merekomendasikan buku berdasarkan atribut konten (penulis). Hal ini memastikan bahwa rekomendasi relevan dengan karakteristik buku input.
  - Contoh hasil rekomendasi berdasarkan buku *"Harry Potter a l'ecole des sorciers"* menunjukkan bahwa sistem mampu menemukan buku dari penulis yang sama.

**Kesimpulan:**
- Kedua pendekatan telah menjawab *problem statement* dengan cara yang berbeda namun saling melengkapi.

---

### **2. Apakah Berhasil Mencapai Goals yang Diharapkan?**

**Goals:**
1. Memberikan rekomendasi buku yang relevan berdasarkan preferensi pengguna.
2. Meningkatkan pengalaman pengguna dalam menemukan buku yang sesuai dengan minatnya.

**Evaluasi Pencapaian Goals:**
- **Collaborative Filtering:**
  - Model berhasil memberikan rekomendasi yang relevan dengan preferensi pengguna, dengan nilai *validation loss* yang rendah (0.0010), menunjukkan akurasi prediksi yang baik.
  - Rekomendasi yang dihasilkan personal dan dapat membantu pengguna menemukan buku sesuai preferensinya.
- **Content-Based Filtering:**
  - Model memberikan rekomendasi yang sesuai dengan atribut konten buku (penulis), seperti rekomendasi buku karya *J. K. Rowling* untuk buku *Harry Potter*.
  - Pendekatan ini mendukung pengguna yang baru bergabung atau belum memberikan banyak data interaksi (*cold start problem*).

**Kesimpulan:**
- Kedua pendekatan berhasil mencapai *goals* yang direncanakan. Model membantu pengguna menemukan buku yang relevan dan meningkatkan pengalaman pencarian buku.

---

### **3. Apakah Solusi Statement Berdampak?**

**Solusi Statement:**
Menggunakan dua pendekatan (*collaborative filtering* dan *content-based filtering*) untuk memberikan rekomendasi buku yang relevan.

**Dampak Solusi Statement:**
- **Collaborative Filtering:**
  - **Dampak Positif:**
    - Model memberikan rekomendasi personal dengan memanfaatkan data interaksi historis pengguna.
    - Cocok untuk pengguna dengan riwayat interaksi yang cukup, meningkatkan loyalitas pengguna dengan rekomendasi yang akurat.
  - **Keterbatasan:**
    - Tidak mampu memberikan rekomendasi untuk item baru (*cold start problem*).
- **Content-Based Filtering:**
  - **Dampak Positif:**
    - Model dapat memberikan rekomendasi yang relevan tanpa memerlukan data pengguna lain, cocok untuk pengguna baru.
    - Menyediakan rekomendasi berdasarkan kesamaan atribut konten, membantu pengguna menemukan buku lain dari penulis favorit.
  - **Keterbatasan:**
    - Rentan terhadap masalah *overspecialization* (rekomendasi hanya dari penulis atau genre yang sama).
    - Tidak memperhitungkan preferensi pengguna lain, sehingga rekomendasi kurang personal.

**Kesimpulan:**
- Kombinasi kedua pendekatan ini memberikan solusi yang komprehensif:
  - **Collaborative filtering** memberikan rekomendasi personal untuk pengguna yang memiliki data interaksi yang cukup.
  - **Content-based filtering** melengkapi dengan memberikan rekomendasi berbasis konten untuk pengguna baru atau item baru.
- Pendekatan ini berdampak positif terhadap pengalaman pengguna dan relevansi rekomendasi, yang secara langsung mendukung *business goals*.

---

### **Kesimpulan Utama**
- **Problem Statement Terjawab:** Kedua pendekatan memberikan rekomendasi yang relevan dengan cara yang berbeda, sehingga menjawab kebutuhan sistem rekomendasi yang relevan.
- **Goals Tercapai:** Model telah memberikan hasil yang memenuhi tujuan proyek, yaitu rekomendasi yang relevan dan meningkatkan pengalaman pengguna.
- **Dampak Solusi:** Kombinasi kedua pendekatan memberikan dampak positif terhadap relevansi rekomendasi, dengan memanfaatkan kekuatan masing-masing metode untuk mengatasi keterbatasan.

### **Saran Pengembangan**
Untuk hasil yang lebih optimal, pendekatan *hybrid recommendation system* dapat diterapkan untuk menggabungkan kekuatan kedua metode, sehingga memberikan rekomendasi yang personal sekaligus relevan berdasarkan konten.
