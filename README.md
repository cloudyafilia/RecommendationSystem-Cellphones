# Laporan Proyek Machine Learning - Cloudya Filia Putri

## Project Overview
### Latar Belakang Proyek
Industri ponsel pintar merupakan salah satu sektor teknologi konsumen yang mengalami pertumbuhan pesat dan memiliki dampak besar terhadap perilaku pasar global maupun regional. Dalam ekosistem yang sangat kompetitif dan dinamis seperti saat ini, konsumen menghadapi tantangan dalam memilih produk yang paling sesuai dengan kebutuhan dan preferensi mereka. Faktor-faktor seperti merek, spesifikasi teknis, harga, dan sistem operasi menjadi variabel penting yang memengaruhi keputusan pembelian. Namun, kompleksitas informasi dan variasi produk sering kali menyulitkan konsumen, terutama mereka yang kurang memahami spesifikasi teknis secara mendalam. Menurut Wening (2024), penggunaan sistem rekomendasi berbasis machine learning dapat membantu konsumen dalam proses seleksi produk teknologi dengan meningkatkan relevansi dan personalisasi rekomendasi.

Berbagai penelitian telah membuktikan efektivitas penerapan sistem rekomendasi dalam membantu pengguna menemukan produk yang tepat. Kim et al. (2021) menunjukkan bahwa kombinasi pendekatan Content-Based Filtering dan Collaborative Filtering mampu meningkatkan akurasi rekomendasi pada platform e-commerce elektronik. Studi oleh Bączkiewicz et al. (2021) mengungkapkan pentingnya pemrosesan data yang akurat dan pemilihan fitur yang relevan dalam membangun sistem rekomendasi ponsel, sehingga sistem dapat memberikan saran yang sesuai dengan preferensi pengguna dan karakteristik produk. Selain itu, penelitian dari Singh et al. (2021) menyoroti peran sistem rekomendasi dalam meningkatkan pengalaman pengguna dan efisiensi pencarian produk pada pasar smartphone.

Berdasarkan temuan tersebut, pendekatan hybrid yang menggabungkan Content-Based Filtering dan Collaborative Filtering semakin relevan dalam pengembangan sistem rekomendasi ponsel pintar. Pendekatan ini tidak hanya memungkinkan personalisasi berdasarkan data pengguna dan fitur produk, tetapi juga mengatasi kendala cold start yang sering muncul pada sistem rekomendasi konvensional. Selaras dengan konsep data-driven decision making yang dijelaskan oleh Khusna et al. (2021), proyek ini bertujuan untuk merancang, mengimplementasikan, dan mengevaluasi sistem rekomendasi ponsel yang dapat memberikan rekomendasi yang tepat dan relevan bagi pengguna, sehingga membantu proses pengambilan keputusan pembelian yang lebih efisien dan efektif.

### Pentingnya Proyek
Proyek ini penting dilakukan karena:
1. Meningkatkan Pengalaman Pengguna: Mempermudah pengguna dalam menemukan ponsel yang sesuai dengan preferensi mereka sehingga meningkatkan kepuasan dan kualitas pengalaman berbelanja.
2. Efisiensi Waktu dan Usaha: Mengurangi beban waktu dan tenaga yang diperlukan pengguna saat mencari serta membandingkan berbagai pilihan model ponsel.
3. Rekomendasi yang Dipersonalisasi: Menyediakan saran produk yang disesuaikan dengan preferensi individu berdasarkan data rating pengguna, sehingga hasil rekomendasi lebih relevan dan akurat.

## Business Understanding
### Problem Statements
Adapun rumusan masalah dalam analisis ini adalah sebagai berikut.
1. Bagaimana pengguna dapat dipermudah untuk menemukan ponsel yang paling sesuai dengan kebutuhan dan preferensi mereka?
2. Bagaimana pengguna dapat menemukan ponsel yang mirip dengan ponsel lama mereka meskipun tidak memahami spesifikasi teknis ponsel tersebut?

### Goals
Berdasarkan rumusan masalah yang telah dipaparkan, maka diperoleh tujuan sebagai berikut.
1. Mengembangkan sistem rekomendasi yang memberikan daftar ponsel terbaik berdasarkan preferensi pengguna.
2. Membangun sistem rekomendasi yang memberikan daftar ponsel terbaik berdasarkan model ponsel lama.

### Solution Statements
Berdasarkan masalah dan tujuan di atas, maka dapat diterapkan solusi sebagai berikut:
1. Content-Based Filtering: Menggunakan fitur deskriptif ponsel (brand, model, OS) untuk merekomendasikan produk serupa.
2. Collaborative Filtering: Menggunakan data rating pengguna untuk rekomendasi berdasarkan pola preferensi pengguna lain.

## Data Understanding

Dataset yang digunakan adalah dataset [Cellphones Recommendations](https://www.kaggle.com/datasets/meirnizri/cellphones-recommendations) yang diambil dari platform penyedia data Kaggle. File yang digunakan berekstensi `.csv`. Dataset terdiri dari tiga file:
1. **Cellphones Data**: 33 baris dengan 32 kolom, berisi spesifikasi ponsel yang dapat dijelaskan sebagai berikut.

    | index | cellphone_id | brand | model            | operating system | internal memory | RAM | performance | main camera | selfie camera | battery size | screen size | weight | price | release date |
    |-------|--------------|-------|------------------|------------------|-----------------|-----|-------------|-------------|---------------|--------------|-------------|--------|-------|--------------|
    | 0     | 0            | Apple | iPhone SE (2022) | iOS              | 128             | 4   | 7.23        | 12          | 7             | 2018         | 4.7         | 144    | 429   | 18/03/2022   |
    | 1     | 1            | Apple | iPhone 13 Mini   | iOS              | 128             | 4   | 7.72        | 12          | 12            | 2438         | 5.4         | 141    | 699   | 24/09/2021   |
    | 2     | 2            | Apple | iPhone 13        | iOS              | 128             | 4   | 7.75        | 12          | 12            | 3240         | 6.1         | 174    | 699   | 24/09/2021   |
    | 3     | 3            | Apple | iPhone 13 Pro    | iOS              | 256             | 6   | 7.94        | 12          | 12            | 3065         | 6.1         | 204    | 999   | 24/09/2021   |
    | 4     | 4            | Apple | iPhone 13 Pro Max| iOS              | 256             | 6   | 8.01        | 12          | 12            | 4352         | 6.7         | 240    | 1199  | 24/09/2021   |
    
      - `cellphone_id`: ID unik untuk setiap model ponsel.
      - `brand`: Merek ponsel (misalnya, Apple, Samsung, dll).
      - `model`: Nama model ponsel.
      - `operating system`: Sistem operasi ponsel yang digunakan (misalnya, iOS, Android).
      - `internal memory`: Kapasitas penyimpanan internal dalam GB.
      - `RAM`: Kapasitas RAM dalam GB.
      - `performance`: Skor performa kinerja ponsel.
      - `main camera`: Resolusi kamera utama dalam megapiksel.
      - `selfie camera`: Resolusi kamera depan dalam megapiksel.
      - `battery size`: Kapasitas baterai dalam mAh.
      - `screen size`: Ukuran layar dalam inci.
      - `weight`: Berat ponsel dalam gram.
      - `price`: Harga ponsel dalam dolar AS.
      - `release date`: Tanggal rilis ponsel.

2. **Cellphones Rating**: 990 baris dengan 3 kolom, berisi rating pengguna terhadap ponsel yang dapat dijelaskan sebagai berikut.

    | index | user_id | cellphone_id | rating |
    |-------|---------|--------------|--------|
    | 0     | 0       | 30           | 1      |
    | 1     | 0       | 5            | 3      |
    | 2     | 0       | 10           | 9      |
    | 3     | 0       | 9            | 3      |
    | 4     | 0       | 23           | 2      |
    
      - `user_id`: ID unik untuk setiap pengguna.
      - `cellphone_id`: ID unik untuk setiap ponsel (mengacu pada cellphones_data).
      - `rating`: Nilai rating yang diberikan pengguna untuk ponsel tertentu (skala 1-10).

3. **Cellphones Users**: 99 baris dengan 4 kolom, berisi data demografi pengguna yang dapat dijelaskan sebagai berikut.

    | index | user_id | age | gender | occupation       |
    |-------|---------|-----|--------|------------------|
    | 0     | 0       | 38  | Female | Data analyst     |
    | 1     | 1       | 40  | Female | team worker in it|
    | 2     | 6       | 55  | Female | IT               |
    | 3     | 8       | 25  | Female | Manager          |
    | 4     | 10      | 23  | Male   | worker           |
    
      - `user_id`: ID unik untuk setiap pengguna.
      - `age`: Usia pengguna.
      - `gender`: Jenis kelamin pengguna.
      - `occupation`: Pekerjaan pengguna.

## Exploratory Data Analysis (EDA)
Analisis eksploratif dilakukan untuk memahami distribusi data dan hubungan antar fitur. Terdiri dari:

### Dataset "data"

1. **Distribusi fitur `brand`**

    ![image](https://github.com/user-attachments/assets/bb2a503c-b153-4ed2-8bb1-a30b63d3b174)
    
    Visualisasi frekuensi brand ponsel menunjukkan bahwa dari total 10 merek ponsel dalam dataset, Samsung menjadi yang paling dominan dengan 8 model, diikuti oleh Apple (6), Motorola, OnePlus, dan Xiaomi (masing-masing 4). Merek lain seperti Google, Asus, Oppo, Vivo, dan Sony hanya memiliki 1–3 model. 

2. **Distribusi fitur `model`**

    ![image](https://github.com/user-attachments/assets/0ef19dca-cc02-4ede-ac5c-ddc5879c46ab)
    
    Dataset ini mencakup 33 model ponsel yang beragam, mulai dari berbagai seri iPhone (seperti iPhone SE 2022, iPhone 13 series), seri Galaxy dari Samsung (termasuk Galaxy A, S, dan Z), serta model dari merek lain seperti Pixel, Nord, Redmi, Poco, Xperia, dan Moto. Keberagaman model ini menunjukkan cakupan yang luas pada berbagai segmen pasar dan brand, memberikan peluang analisis yang komprehensif terkait performa dan preferensi pengguna terhadap tiap model.

3. **Distribusi `operating system`**

    ![image](https://github.com/user-attachments/assets/7c23cde6-76ef-4aa0-97d4-c6da918951e3)
    
    Berdasarkan visualisasi fitur sistem operasi, mayoritas pengguna dalam data menggunakan Android (81,8%), sementara sisanya menggunakan iOS (18,2%). Hal ini menunjukkan bahwa Android lebih banyak diminati atau lebih mudah diakses oleh pengguna dalam data yang dianalisis. Perbedaan ini juga bisa mencerminkan preferensi pasar, ketersediaan perangkat, atau faktor ekonomi yang memengaruhi pilihan sistem operasi.

4. **Distribusi `internal memory`**

    ![image](https://github.com/user-attachments/assets/96beddc2-2307-4ab4-8478-fa1716e4c745)
    
    Berdasarkan visualisasi distribusi kapasitas memori internal, terlihat bahwa varian 128 GB merupakan yang paling banyak digunakan oleh pengguna dengan jumlah 20 unit. Selanjutnya, memori internal 256 GB digunakan oleh 6 pengguna, sementara varian lainnya seperti 64 GB, 32 GB, dan 256 GB masing-masing digunakan oleh 3 pengguna. Varian dengan kapasitas terbesar, yaitu 512 GB, hanya digunakan oleh 1 pengguna. Pola ini menunjukkan bahwa memori internal 128 GB menjadi pilihan yang paling umum, kemungkinan karena menawarkan keseimbangan antara kapasitas yang cukup besar dan harga yang masih terjangkau.

5. **Distribusi `RAM`**

    ![image](https://github.com/user-attachments/assets/55237d06-0c33-4e10-8f6c-12e3292f2162)
    
    Berdaasarkan visualisasi distribusi jumlah RAM yang digunakan, dengan puncak penggunaan mencapai 8 GB, diikuti oleh 6 GB dan 12 GB yang memiliki jumlah yang sama. Penggunaan RAM yang paling rendah terjadi pada 4 GB dan 13 GB. Hal ini mengindikasikan bahwa sebagian besar kebutuhan memori berkisar di antara 6 hingga 8 GB, sedangkan penggunaan di luar rentang ini lebih jarang, mungkin menunjukkan preferensi terhadap kapasitas memori tertentu sesuai kebutuhan pengguna. Pemahaman pola ini penting untuk mengoptimalkan pengelolaan sumber daya yang sesuai dengan kebutuhan pengguna.

6. **Distribusi `performance`**

    ![image](https://github.com/user-attachments/assets/77ae015a-c70a-4537-afd8-7b2afbb120b6)
    
    Berdasarkan visualisasi fitur performance, terlihat bahwa sebagian besar data (63,6%) memiliki nilai performa lebih tinggi dari rata-rata (6,22), sementara sisanya (36,4%) memiliki performa yang sama atau lebih rendah dari rata-rata tersebut. Hal ini mengindikasikan bahwa performa secara umum cenderung berada di atas nilai rata-rata, menunjukkan keberhasilan dalam mencapai tingkat performa yang lebih baik. Pola ini penting untuk dipahami agar dapat menargetkan peningkatan performa di area yang kurang dari rata-rata dan memaksimalkan potensi dari pengguna atau sistem yang dianalisis.

7. **Distribusi `main camera`**

    ![image](https://github.com/user-attachments/assets/ab19ca64-6cad-49b8-9f41-6430ca43c880)
    
    Berdasarkan visualisasi distribusi main camera, jumlah penggunaan utama kamera berkisar di angka 12 hingga 64, dengan frekuensi tertinggi tercatat pada 50 dan 64. Terdapat juga kategori dengan jumlah penggunaan yang lebih rendah, seperti 13 dan 108, yang menunjukkan variability dalam preferensi pengguna terhadap jumlah kamera utama. Pola ini mengindikasikan bahwa sebagian besar pengguna cenderung menggunakan sekitar 12 hingga 64 kamera utama, namun ada juga yang memiliki jumlah yang lebih rendah maupun lebih tinggi, menandakan adanya berbagai kebutuhan dan tingkat penggunaannya.

8. **Distribusi `battery size`**

    ![image](https://github.com/user-attachments/assets/734d4a04-31e7-46cb-a79b-7f243f77aba6)
    
    Berdasarkan visualisasi distribusi battery size, sebagian besar data menunjukkan ukuran baterai di kisaran 5000, yang mencerminkan preferensi pengguna terhadap kapasitas baterai yang lebih besar. Terdapat juga beberapa nilai yang lebih rendah, seperti 2018 hingga 4800, namun frekuensi tertinggi berada pada ukuran 5000. Pola ini mengindikasikan bahwa kapasitas baterai besar menjadi pilihan utama, kemungkinan karena kebutuhan penggunaan yang lebih lama dan tahan lama.

9. **Distribusi `screen size`**

    ![image](https://github.com/user-attachments/assets/37db94ae-2dc2-4593-b0ce-f215a5a94567)
    
    Berdasarkan visualisasi distribusi screen size, mayoritas data menunjukkan ukuran layar antara 6.6 hingga 6.7 inci, dengan frekuensi tertinggi pada 6.7 inci. Terdapat pula beberapa data pada ukuran yang sedikit lebih kecil dan lebih besar dari rentang tersebut, namun secara umum pengguna cenderung memilih layar berukuran sekitar 6.6 hingga 6.7 inci. Pola ini mengindikasikan preferensi terhadap ukuran layar yang sedang, yang mungkin dianggap optimal untuk kenyamanan dan portabilitas perangkat.

10. **Distribusi `weight`**

    ![image](https://github.com/user-attachments/assets/7b1d68ef-7a27-4e61-a010-7dad55492c0f)
    
    Berdasarkan visualisasi distribusi weight, sebagian besar data menunjukkan berat handphone sekitar 195 gram dan 204 gram, dengan frekuensi tertinggi pada 204 gram. Rentang berat handphone lainnya menunjukkan nilai yang relatif seragam di sekitar angka ini, menandakan bahwa bobot perangkat biasanya berkisar di kisaran tersebut. Pola ini mengindikasikan preferensi terhadap perangkat yang memiliki berat sedang, yang kemungkinan dianggap seimbang antara portabilitas dan kenyamanan pengguna.

11. **Distribusi `realease date`**

    ![image](https://github.com/user-attachments/assets/78d2ad7d-b2ad-401e-aee1-53f6ba38b3fd)
    
    Berdasarkan visualisasi fitur release year, hampir setengah dari jumlah penjualan terjadi pada tahun 2021 dan 2022, keduanya dengan porsi sekitar 48,5%. Sementara itu, penjualan pada tahun 2018 hanya sekitar 3%, menunjukkan bahwa volume penjualan jauh lebih kecil dibandingkan dua tahun terakhir tersebut. Pola ini mengindikasikan bahwa pertumbuhan penjualan pesat terjadi setelah 2018, dengan puncaknya sekitar 2021 dan 2022, kemungkinan menandakan peningkatan popularitas atau adopsi produk di periode tersebut.

### Dataset "rating"

1. **Distribusi `userID`**

    ![image](https://github.com/user-attachments/assets/77522076-3061-4ef6-aa62-b042aabfe63a)
    
    Distribusi jumlah review untuk setiap pengguna menunjukkan bahwa mayoritas pengguna memberikan jumlah review yang konsisten sebanyak 10 kali. Pola ini mengindikasikan bahwa sebagian besar pengguna aktif dalam memberikan review secara reguler dan konsisten, sementara ada sedikit pengguna yang aktivitas reviewnya berbeda.

2. **Distribusi `cellphoneID`**

    ![image](https://github.com/user-attachments/assets/0956d4c3-aa06-4e92-a9ee-cd5f2459b676)
    
    Distribusi jumlah review per `cellphone_id` menunjukkan variasi aktivitas pengguna dalam memberikan review. Sebagian besar `cellphone_id` memberikan antara 20 sampai 35 review, dengan puncak di sekitar 8 dan 14, yang menunjukkan bahwa sejumlah pengguna cukup aktif. Ada juga beberapa `cellphone_id` yang memiliki jumlah review lebih tinggi, mendekati 40, menandakan pengguna yang sangat aktif. Data ini mengindikasikan adanya variasi tingkat partisipasi pengguna dalam memberikan review, dengan sebagian besar menunjukkan tingkat aktivitas sedang hingga tinggi.

3. **Distribusi `rating`**

    ![image](https://github.com/user-attachments/assets/8cc9a1cf-9bbe-469c-b1a4-078adaa98636)
    
    Berdasarkan visualisasi distribusi rating, sebagian besar pengguna memberikan rating tinggi, terutama pada angka 8 dan 9, dengan frekuensi tertinggi di sekitar rating 8. Ini menunjukkan bahwa mayoritas pengguna cenderung memberikan penilaian positif terhadap produk atau layanan tersebut. Rating di bawah 5 sangat jarang, menandakan tingkat ketidakpuasan yang rendah. Namun, ada satu angka yang tidak relevan dan tampak sebagai outlier, yaitu angka 18. Rating 18 ini tidak sesuai dengan skala rating yang umum digunakan, sehingga kemungkinan merupakan data yang tidak valid atau kesalahan input dan perlu penanganan lebih lanjut.

### Dataset "users"

1. **Distribusi `age`**

    ![image](https://github.com/user-attachments/assets/76ad9299-0648-486b-a6be-0a131d9795ab)
    
    Berdasarkan visualisasi distribusi usia, menunjukkan bahwa sebagian besar responden berusia antara 21 dan 61 tahun, dengan puncak pada usia sekitar 23 dan 32 tahun. Frekuensi tertinggi terdapat pada usia 23 tahun, yang menunjukkan bahwa kelompok usia ini paling aktif dalam memberikan data atau respons. Selain itu, terdapat variasi yang cukup luas di seluruh rentang usia, mengindikasikan beragam peserta dari berbagai kelompok usia. Data ini menggambarkan bahwa berbagai kelompok usia berpartisipasi, dengan kecenderungan utama di kalangan muda dewasa.

2. **Distribusi `gender`**

    ![image](https://github.com/user-attachments/assets/6c33d9b0-cb67-4429-a033-af105999c30a)
    
    Visualisasi distribusi gender menunjukkan bahwa jumlah pengguna pria (Male) jauh lebih tinggi dibandingkan pengguna perempuan (Female). Jumlah pengguna pria mencapai sekitar 50, sementara pengguna perempuan sekitar 45, dan data yang tidak relevan muncul pada kategori "-Select Gender" sebanyak sekitar 4. Kehadiran kategori "-Select Gender" menandakan adanya data yang tidak lengkap atau tidak terklasifikasi dengan baik, sehingga sebaiknya dihapus atau diperiksa lebih lanjut agar analisis menjadi lebih akurat. Secara keseluruhan, mayoritas pengguna teridentifikasi sebagai pria, dengan jumlah yang jauh lebih banyak dibandingkan wanita.

5. **Distribusi `occupation`**

    ![image](https://github.com/user-attachments/assets/c32d6593-e1db-43cd-9d7d-b56756418959)
    
    Data occupation pada pengguna menunjukkan keberagaman yang tinggi dengan total 45 jenis pekerjaan unik, mulai dari profesional teknis seperti 'software developer' dan 'technical engineer', hingga peran administratif dan layanan seperti 'team leader', 'accountant', dan 'sales'. Variasi ini menggambarkan profil pengguna yang beragam, mencakup berbagai sektor industri dan tingkat jabatan, yang dapat memengaruhi preferensi dan kebutuhan dalam memilih ponsel. 

## Data Preparation

### Teknik Data Preparation

1. **Penggabungan Dataset**
    Data dari tiga sumber utama—data spesifikasi ponsel (cellphones data), data rating pengguna (cellphones rating), dan data demografi pengguna (cellphones users)—digabungkan menjadi satu dataframe terpadu untuk memudahkan analisis dan pemodelan.
2. **Handling Missing Values**
    Nilai yang hilang (missing values) pada kolom-kolom penting, seperti kolom occupation, diidentifikasi dan dihapus agar tidak mempengaruhi kualitas model dan analisis.
3. **Removing Outliers**
    Data dengan nilai tidak wajar atau ekstrem (outliers) pada kolom tertentu, misalnya rating dengan nilai 18 (di luar skala normal) dan gender dengan nilai '-Select Gender-' yang tidak valid, dihapus untuk menjaga konsistensi dan meningkatkan akurasi model.
4. **Mengubah Format Penulisan**
    Penulisan teks pada kolom kategorikal diubah menjadi format konsisten, seperti mengubah semua nilai pada kolom occupation menjadi huruf kecil (lowercase), agar data yang seharusnya sama tidak dianggap berbeda karena perbedaan format penulisan.
5. **Mereplace Nilai yang Salah atau Tidak Konsisten**
    Beberapa nilai pada kolom occupation yang mengalami kesalahan penulisan atau inkonsistensi diperbaiki. Contohnya, 'Healthare' diperbaiki menjadi 'healthcare', dan singkatan 'it' diganti menjadi bentuk lengkap 'information technology'.
6. **Pembagian Dataset (Train-Test Split)**
    Dataset dibagi menjadi dua bagian: data training sebanyak 80% dan data testing sebanyak 20% untuk melatih model dan menguji performanya secara adil dan valid.

### Proses Data Preparation

1. Menggabungkan dataset cellphones data, cellphones rating, dan cellphones users menjadi satu dataframe komprehensif.
2. Menghapus semua baris yang memiliki nilai null pada kolom occupation untuk menjaga kualitas data pengguna.
3. Menghapus baris yang mengandung nilai outlier, seperti rating yang bernilai 18 (di luar skala penilaian yang valid) dan nilai gender '-Select Gender-' yang merupakan placeholder, bukan data valid.
4. Menstandardisasi nilai pada kolom occupation dengan mengubah seluruh teks menjadi lowercase agar nilai-nilai yang serupa tidak terduplikasi karena perbedaan kapitalisasi.
5. Memperbaiki kesalahan penulisan dalam kolom occupation seperti mengubah 'Healthare' menjadi 'healthcare' dan mengganti singkatan 'it' menjadi 'information technology'.
6. Melakukan pembagian data menjadi data train sebanyak 791 baris (80%) dan data test sebanyak 198 baris (20%).

### Alasan Melakukan Data Preparation

1. Handling Missing Values: Nilai yang hilang dapat menyebabkan bias atau error dalam analisis dan model, sehingga perlu diatasi agar data yang digunakan lengkap dan konsisten.
2. Removing Outliers: Data ekstrim atau tidak valid dapat merusak akurasi model dan menghasilkan prediksi yang tidak realistis, sehingga penghapusan outlier membantu meningkatkan performa dan kestabilan model.
3. Mengubah Format Penulisan: Konsistensi penulisan data kategorikal penting agar nilai yang sama tidak terpisah menjadi kategori berbeda, yang dapat memengaruhi analisis dan hasil pemodelan.
4. Mereplace Value yang Salah: Memperbaiki kesalahan penulisan mencegah duplikasi kategori dan memastikan interpretasi data yang benar dan valid.
5. Pembagian Dataset: Memisahkan data untuk pelatihan dan pengujian memungkinkan evaluasi model secara objektif terhadap data yang belum pernah dilihat, sehingga mengukur kemampuan generalisasi model.

### Hasil Splitting Data

    | Kategori        | Jumlah Data |
    |-----------------|-------------|
    | Seluruh Dataset | 989         |
    | Data Training   | 791         |
    | Data Testing    | 198         |

## Modeling

Pada tahap ini, dua pendekatan utama yang digunakan untuk membangun sistem rekomendasi ponsel dibahas secara mendalam, yaitu Content-Based Filtering dan Collaborative Filtering. Kedua metode ini dipilih karena masing-masing memiliki kekuatan dan kelemahan yang berbeda sehingga dapat memberikan rekomendasi yang relevan dari sisi konten produk maupun interaksi pengguna.

### Content-Based Filtering (CBF)
Content-Based Filtering berfokus pada atribut atau fitur dari item itu sendiri, dalam hal ini fitur ponsel seperti merek (brand), model, dan sistem operasi. Metode ini membangun profil item dengan mengubah data teks menjadi representasi numerik menggunakan teknik TF-IDF Vectorizer, yang mengukur pentingnya sebuah kata atau fitur dalam konteks data. Setelah itu, dilakukan perhitungan cosine similarity antar item untuk menentukan tingkat kemiripan setiap ponsel dengan ponsel yang sudah disukai pengguna. Hasilnya adalah daftar rekomendasi ponsel yang paling mirip dengan ponsel yang telah digunakan atau disukai oleh pengguna.

-  **Parameter dan teknik utama pada CBF**:
1. TF-IDF Vectorizer: Digunakan untuk mengubah data teks (misalnya kolom brand) menjadi representasi numerik dalam bentuk matriks sparse, di mana setiap fitur diberi bobot berdasarkan frekuensi dan pentingnya dalam data. Ini memungkinkan penghitungan kesamaan antar item.
2. Cosine Similarity: Metode yang digunakan untuk mengukur kemiripan antar vektor fitur. Nilai cosine similarity berkisar antara 0 sampai 1, di mana 1 berarti dua item sangat mirip.

- **Tahapan proses CBF**:
1. Pemilihan Pemilihan Fitur
   Karena TF-IDF bekerja optimal pada data teks, hanya kolom bertipe object seperti brand, model, dan operating_system yang dipilih.
2. Pembuatan DataFrame
   Membuat DataFrame baru yang berisi kolom-kolom tersebut untuk diproses.
       
       ```python
       phone_new = pd.DataFrame({
        'cellphone_id': cellphone_id,
        'brand': brand,
        'model': model,
        'operating_system': operating_system,
        })
       ```
   
3. Transformasi Data dengan TF-IDF
   Membangun TF-IDF matrix dari kolom brand (atau fitur lain yang relevan):
        
        ```python
        tfidf_matrix = tf.fit_transform(phone_new['brand'])
        ```
        
   Output berupa matriks ukuran (33,10) yaitu `jumlah_data` dan `jumlah_unique_brand`.

4.  Menghitung Kemiripan
    Menggunakan cosine similarity untuk menghitung derajat kemiripan antar ponsel berdasarkan matriks TF-IDF tersebut.
5.  Evaluasi dan membangun Fungsi Rekomendasi
    Membuat fungsi yang menerima nama model ponsel dan mengembalikan 4 rekomendasi teratas yang paling mirip, beserta detail brand dan operating system.

- **Cara kerja algoritma CBF**:

Algoritma CBF mengubah fitur deskriptif setiap ponsel menjadi representasi numerik yang memudahkan penghitungan kemiripan antar produk. Saat pengguna memasukkan nama model ponsel, sistem menghitung kemiripan cosine antara ponsel tersebut dengan semua ponsel lain di dataset, kemudian merekomendasikan produk yang memiliki similarity tertinggi.

- **Contoh Interaksi**:

Jika pengguna memilih ponsel "Galaxy A13", algoritma akan:
1. Mengambil profil teks "Galaxy A13".
2. Mengubah profil tersebut ke dalam vektor TF-IDF.
3. Menghitung cosine similarity dengan seluruh ponsel lain.
4. Mengembalikan daftar ponsel dengan similarity tertinggi seperti "Galaxy Z Flip 3", "Galaxy S22 Plus", dan lain-lain.

- **Contoh Output Top-N Recommendation untuk CBF**:

    ```python
    model_recommendations('Galaxy A13')
    ```
    
    |   | model          | brand   | operating_system |
    |---|----------------|---------|------------------|
    | 0 | Galaxy Z Flip 3| Samsung | Android          |
    | 1 | Galaxy S22 Plus| Samsung | Android          |
    | 2 | Galaxy Z Fold 3| Samsung | Android          |
    | 3 | Galaxy A32     | Samsung | Android          |


### Collaborative Filtering (CF)

Pendekatan Collaborative Filtering memanfaatkan data interaksi pengguna dengan item, seperti rating yang diberikan pengguna terhadap ponsel. Metode ini tidak bergantung pada fitur produk, melainkan mencari pola kesamaan preferensi antar pengguna atau antar item berdasarkan data interaksi. Pada proyek ini, digunakan model neural network dengan arsitektur embedding untuk mempelajari representasi laten pengguna dan item. Model dilatih dengan loss function Binary Crossentropy dan optimizer Adam, serta dimonitor menggunakan metrik Root Mean Squared Error (RMSE).

- **Parameter dan teknik utama pada CF**:
1. Model Neural Network dengan Embedding
   Dibangun menggunakan kelas RecommenderNet berbasis Keras Model.
   a) Embedding layer untuk user dan item dengan dimensi embedding 50.
   b) Output layer memprediksi rating menggunakan sigmoid activation.
2. Loss Function: Binary Crossentropy
   Meminimalkan perbedaan prediksi rating dengan rating asli.
3. Optimizer: Adam dengan learning rate 0.001
   Optimasi parameter model selama training.
4. Metrics: Root Mean Squared Error (RMSE)
   Sebagai metrik untuk memantau performa model.

- **Tahapan proses CF**:
1. Persiapan Data
   Menggunakan dataframe rating yang berisi user_id, cellphone_id, dan rating.
2. Membangun Model
   Membuat kelas model dengan embedding untuk user dan item.
3. Training Model
   Melatih model dengan batch size 8 selama 100 epoch.
4. Evaluasi dan Prediksi
   Menggunakan model terlatih untuk memprediksi rating ponsel yang belum diulas oleh pengguna.

- **Cara kerja algoritma CF**:

Model mempelajari pola rating antar pengguna dan item, sehingga dapat memprediksi rating untuk item baru bagi pengguna tertentu. Ini memungkinkan rekomendasi produk yang sesuai dengan preferensi pengguna meskipun produk tersebut tidak mirip secara fitur dengan yang sudah pernah dipilih.

- **Contoh Interaksi**:

Misalnya, pengguna dengan ID 106 ingin rekomendasi:
1. Model mencari pengguna lain dengan pola rating serupa.
2. Memperkirakan rating pengguna 106 terhadap ponsel yang belum diulas.
3. Mengembalikan daftar ponsel dengan prediksi rating tertinggi sebagai rekomendasi. 

- **Contoh Output Top-N Recommendation untuk CBF**:

![image](https://github.com/user-attachments/assets/9be5f808-d8ed-4be3-a225-f5856885719d)
  

### Perbandingan masing-masing pendekatan:

Kedua pendekatan menghasilkan rekomendasi dalam bentuk Top-N rekomendasi, yaitu daftar N ponsel terbaik yang dipersonalisasi untuk setiap pengguna berdasarkan metode masing-masing. Output ini membantu pengguna dalam memilih ponsel yang sesuai dengan preferensi atau menemukan ponsel pengganti yang serupa dengan ponsel lamanya. Dengan menggabungkan kelebihan kedua metode ini, diharapkan sistem rekomendasi dapat memberikan hasil yang lebih robust, fleksibel, dan relevan bagi pengguna dalam berbagai situasi.


| Pendekatan             | Kelebihan                                                                                   | Kekurangan                               |
|-----------------------|---------------------------------------------------------------------------------------------|-----------------------------------------|
| Content-Based Filtering | - Independen dari data pengguna lain<br>- Dapat merekomendasikan produk baru yang belum pernah diulas | - Terbatas hanya pada fitur yang ada<br>- Risiko overfitting pada fitur tertentu |
| Collaborative Filtering | - Memanfaatkan pola interaksi pengguna untuk rekomendasi yang lebih personal<br>- Dapat menangani data dalam jumlah besar dan menemukan pola kompleks | - Mengalami masalah cold start untuk pengguna atau item baru<br>- Membutuhkan data interaksi yang cukup banyak |

## Evaluation

Bagian ini membahas evaluasi performa kedua model sistem rekomendasi yang telah dikembangkan, yaitu Content-Based Filtering (CBF) dan Collaborative Filtering (CF). Masing-masing menggunakan metrik evaluasi yang sesuai dengan karakteristik dan data yang dipakai.

### Evaluation Content-Based Filtering (CBF)

Content-Based Filtering menggunakan metrik evaluasi berbasis relevansi rekomendasi, seperti Precision@N, Recall@N, dan F1@N, karena model ini merekomendasikan item berdasarkan kemiripan fitur produk tanpa memprediksi nilai numerik.

1. Precision@N mengukur proporsi rekomendasi dalam top-N yang benar-benar relevan dengan preferensi pengguna.

$$
Precision@N = \frac{\text{Jumlah item relevan dalam rekomendasi top-N}}{N}
$$

    
2. Recall@N mengukur proporsi item relevan yang berhasil ditemukan dalam top-N rekomendasi.

$$
Recall@N = \frac{\text{Jumlah item relevan dalam rekomendasi top-N}}{\text{Jumlah total item relevan}}
$$
    
3. F1@N adalah harmonic mean dari precision dan recall, menggabungkan kedua aspek tersebut menjadi satu nilai evaluasi.

$$
F1@N = 2 \times \frac{Precision@N \times Recall@N}{Precision@N + Recall@N}
$$

**Hasil Evaluasi Model**:

Model Content-Based Filtering menunjukkan performa sempurna dengan nilai Precision@5, Recall@5, dan F1@5 sebesar 1.00. Hal ini menandakan bahwa semua rekomendasi dalam daftar top-5 benar-benar relevan dengan preferensi pengguna, serta seluruh item relevan berhasil tertangkap oleh sistem. Dengan kata lain, sistem mampu memberikan rekomendasi yang sangat akurat dan lengkap berdasarkan fitur produk.

### Evaluation Collaborative Filtering (CF)

Collaborative Filtering menggunakan metrik evaluasi numerik seperti Root Mean Squared Error (RMSE) untuk mengukur perbedaan antara rating prediksi dengan rating aktual dari pengguna. Metrik ini sesuai karena CF memprediksi nilai rating yang bersifat kontinu.

Root Mean Squared Error (RMSE) memberikan ukuran rata-rata deviasi kuadrat prediksi model terhadap rating aktual.

$$
RMSE = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}
$$
    
di mana:  
- $\( y_i \)$ adalah nilai aktual,  
- $\( \hat{y}_i \)$ adalah nilai prediksi,  
- $\( n \)$ adalah jumlah data.

**Hasil Evaluasi Model**:

![image](https://github.com/user-attachments/assets/ed83a841-f671-45f5-8b14-be790bebcec5)


| Dataset       | RMSE  |
|---------------|-------|
| Data Train    | 0.0126|
| Data Test     | 0.3110|

Grafik model metrics menunjukkan bahwa nilai root mean squared error (RMSE) pada data training menurun drastis hingga mencapai sekitar 0.013, menandakan model berhasil belajar dengan sangat baik pada data pelatihan. Namun, nilai RMSE pada data testing stabil di angka sekitar 0.31 dan cenderung meningkat sedikit setelah epoch ke-10, yang mengindikasikan adanya overfitting, di mana model terlalu menyesuaikan diri dengan data training sehingga kehilangan kemampuan generalisasi terhadap data baru. Meski demikian, nilai RMSE test sebesar 0.3110 masih tergolong rendah, menunjukkan bahwa model tetap mampu memberikan prediksi yang cukup akurat pada data testing meskipun performanya tidak sebaik pada data training.

### Evaluation terhadap Business Understanding

1. **Menjawab Problem Statement**
Model sistem rekomendasi yang dikembangkan berhasil menjawab problem statement utama proyek ini. Pendekatan Content-Based Filtering mampu memberikan rekomendasi ponsel yang relevan berdasarkan kemiripan fitur produk, seperti model, brand, dan sistem operasi, sehingga memudahkan pengguna dalam menemukan ponsel yang mirip dengan ponsel lama mereka. Di sisi lain, pendekatan Collaborative Filtering memanfaatkan data interaksi pengguna berupa rating untuk menemukan pola preferensi tersembunyi antar pengguna. Dengan demikian, model dapat memprediksi rating ponsel yang belum diulas oleh pengguna dan memberikan rekomendasi yang lebih personal sesuai dengan selera dan kebiasaan pengguna. Kedua metode ini secara komplementer menangani tantangan utama dalam membantu pengguna memilih ponsel yang paling sesuai dengan kebutuhan dan preferensi mereka.
    
2. **Mencapai Goals**
Model Content-Based Filtering menggunakan teknik cosine similarity yang mengukur kesamaan antara produk berdasarkan fitur deskriptifnya, sehingga mampu menyajikan rekomendasi ponsel yang mirip secara objektif dan terstruktur. Pendekatan ini berhasil mengakomodasi pengguna baru atau pengguna yang memiliki sedikit data interaksi karena fokusnya pada fitur produk. Sementara itu, model Collaborative Filtering yang menggunakan arsitektur neural network RecommenderNet dengan embedding layer berhasil mengidentifikasi pola rating dan preferensi pengguna secara lebih dinamis dan personal. Kedua pendekatan ini berhasil mencapai tujuan utama proyek, yaitu memberikan rekomendasi ponsel yang relevan dan personalisasi, serta meningkatkan pengalaman pengguna dalam proses pencarian produk.
    
3. **Dampak dari Solution Statement**
Implementasi kombinasi algoritma Content-Based dan Collaborative Filtering memberikan dampak positif yang signifikan terhadap kualitas rekomendasi. Content-Based Filtering memastikan bahwa rekomendasi yang diberikan secara langsung berhubungan dengan fitur-fitur utama ponsel yang sudah dikenal oleh pengguna, sehingga memberikan rasa kepercayaan dan kemudahan dalam memilih pengganti atau model serupa. Di sisi lain, Collaborative Filtering memperkaya rekomendasi dengan analisis pola interaksi dari banyak pengguna, memungkinkan sistem memahami preferensi yang tidak selalu terlihat dari fitur produk saja, seperti tren populer atau kecenderungan spesifik kelompok pengguna tertentu. Penggunaan teknik evaluasi seperti RMSE untuk Collaborative Filtering dan metrik Precision, Recall, serta F1-score untuk Content-Based Filtering juga menunjukkan pendekatan yang matang dalam memastikan performa model. Hasilnya adalah sistem rekomendasi yang adaptif, akurat, dan personal, yang secara langsung mendukung tujuan proyek dalam membantu pengguna menemukan ponsel yang sesuai dengan preferensi mereka dan mempercepat pengambilan keputusan pembelian.


## Conclusion

Dengan menggabungkan dua pendekatan utama, yaitu Content-Based Filtering dan Collaborative Filtering, sistem rekomendasi yang dibangun menjadi lebih robust dan fleksibel dalam memberikan rekomendasi ponsel. Content-Based Filtering sangat efektif dalam menyajikan rekomendasi berdasarkan kesamaan fitur produk, seperti model, brand, dan sistem operasi, sehingga cocok untuk pengguna baru atau produk baru tanpa data interaksi. Sementara itu, Collaborative Filtering unggul dalam mengidentifikasi pola preferensi pengguna berdasarkan data interaksi rating, memungkinkan sistem memberikan rekomendasi yang bersifat personal dan relevan secara dinamis. Memahami kelebihan dan keterbatasan masing-masing metode memungkinkan pemilihan dan pengembangan solusi yang paling tepat sesuai dengan kebutuhan dan konteks spesifik sistem rekomendasi. Pendekatan kombinasi ini meningkatkan kualitas rekomendasi, memperkaya pengalaman pengguna, dan mendukung pengambilan keputusan yang lebih tepat dalam memilih ponsel.

### Insight

Dengan memanfaatkan model sistem rekomendasi berbasis Content-Based Filtering dan Collaborative Filtering, proses pemilihan ponsel dapat dilakukan secara lebih akurat dan personal sesuai preferensi pengguna. Analisis fitur produk serta pola interaksi pengguna memungkinkan rekomendasi yang relevan dan tepat sasaran, membantu pengguna dalam menemukan ponsel yang sesuai dengan kebutuhan dan kebiasaan mereka. Penerapan pendekatan ini tidak hanya meningkatkan pengalaman pengguna, tetapi juga memberikan nilai strategis bagi pengembang dan pemasar dalam memahami preferensi konsumen dan menyesuaikan penawaran produk secara lebih efektif. Hasil ini menunjukkan bahwa teknologi kecerdasan buatan berperan penting dalam mengoptimalkan proses rekomendasi dan pengambilan keputusan di era digital.


## Referensi
- Dataset: [Cellphone Recommendations - Kaggle](https://www.kaggle.com/datasets/meirnizri/cellphones-recommendations)
-Bączkiewicz, A., Kizielewicz, B., Shekhovtsov, A., Wątróbski, J., & Sałabun, W. (2021). Methodical aspects of MCDM based E-commerce recommender system. Journal of Theoretical and Applied Electronic Commerce Research, 16(6), 2192-2229.
- Kim, T. Y., Ko, H., Kim, S. H., & Kim, H. D. (2021). Modeling of recommendation system based on emotional information and collaborative filtering. Sensors, 21(6), 1997.
- Khusna, A. N., Delasano, K. P., & Saputra, D. C. E. (2021). Penerapan User-Based Collaborative Filtering Algorithm. MATRIK: Jurnal Manajemen, Teknik Informatika dan Rekayasa Komputer, 20(2), 293-304.
- Singh, P., Gupta, M., Kumar, A., Sikdar, P., & Sinha, N. (2021). E-Grocery retailing mobile application: Discerning determinants of repatronage intentions in an emerging economy. International Journal of Human–Computer Interaction, 37(19), 1783-1798.
- Wening, Y. A. T. (2024). Sistem Rekomendasi Handphone Berbasis Spesifikasi dan Harga Menggunakan Algoritma Decision Tree.
