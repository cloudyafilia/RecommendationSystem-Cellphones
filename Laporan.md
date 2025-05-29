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

1. **Cellphones Data**: 33 baris dengan 14 kolom, mencakup merek, model, sistem operasi, kapasitas memori internal dan RAM, performa, kualitas kamera utama dan depan, ukuran baterai, ukuran layar, berat, harga, serta tanggal rilis. Mayoritas kolom bertipe numerik yang cocok untuk analisis kuantitatif seperti segmentasi pasar, prediksi harga, atau klasifikasi performa. Data ini sangat potensial untuk eksplorasi tren teknologi ponsel terbaru dan preferensi konsumen berdasarkan spesifikasi.


    | cellphone_id | brand | model             | operating system | internal memory | RAM | performance | main camera | selfie camera | battery size | screen size | weight | price | release date |
    |--------------|-------|-------------------|------------------|-----------------|-----|-------------|-------------|---------------|--------------|-------------|--------|-------|--------------|
    | 0            | Apple | iPhone SE (2022)  | iOS              | 128             | 4   | 7.23        | 12          | 7             | 2018         | 4.7         | 144    | 429   | 18/03/2022   |
    | 1            | Apple | iPhone 13 Mini    | iOS              | 128             | 4   | 7.72        | 12          | 12            | 2438         | 5.4         | 141    | 699   | 24/09/2021   |
    | 2            | Apple | iPhone 13         | iOS              | 128             | 4   | 7.75        | 12          | 12            | 3240         | 6.1         | 174    | 699   | 24/09/2021   |
    | 3            | Apple | iPhone 13 Pro     | iOS              | 256             | 6   | 7.94        | 12          | 12            | 3065         | 6.1         | 204    | 999   | 24/09/2021   |
    | 4            | Apple | iPhone 13 Pro Max | iOS              | 256             | 6   | 8.01        | 12          | 12            | 4352         | 6.7         | 240    | 1199  | 24/09/2021   |

    
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

3. **Cellphones Rating**: 990 baris dengan 3 kolom yang merepresentasikan interaksi antara pengguna dan ponsel, dengan kolom `user_id`, `cellphone_id`, dan `rating`. Struktur ini cocok untuk membangun sistem rekomendasi berbasis collaborative filtering, di mana rekomendasi dapat dihasilkan dengan menganalisis pola rating antar pengguna yang memiliki preferensi serupa terhadap ponsel tertentu.


    | user_id | cellphone_id | rating |
    |---------|--------------|--------|
    | 0       | 30           | 1      |
    | 0       | 5            | 3      |
    | 0       | 10           | 9      |
    | 0       | 9            | 3      |
    | 0       | 23           | 2      |

    
      - `user_id`: ID unik untuk setiap pengguna.
      - `cellphone_id`: ID unik untuk setiap ponsel (mengacu pada cellphones_data).
      - `rating`: Nilai rating yang diberikan pengguna untuk ponsel tertentu (skala 1-10).

4. **Cellphones Users**: 99 baris dengan 4 kolom, berisi data demografi pengguna yang mencakup `user_id`, `usia`, `jenis kelamin`, dan `pekerjaan`. Fitur-fitur ini dapat dimanfaatkan dalam sistem rekomendasi berbasis content-based atau hybrid filtering, untuk mempersonalisasi rekomendasi ponsel berdasarkan karakteristik pengguna..


    | user_id | age | gender | occupation       |
    |---------|-----|--------|------------------|
    | 0       | 38  | Female | Data analyst     |
    | 1       | 40  | Female | team worker in it|
    | 6       | 55  | Female | IT               |
    | 8       | 25  | Female | Manager          |
    | 10      | 23  | Male   | worker           |


      - `user_id`: ID unik untuk setiap pengguna.
      - `age`: Usia pengguna.
      - `gender`: Jenis kelamin pengguna.
      - `occupation`: Pekerjaan pengguna.

## Exploratory Data Analysis (EDA)
Tahapan EDA (Exploratory Data Analysis) bertujuan untuk memahami karakteristik dataset restoran, mengidentifikasi pola, hubungan antar variabel, serta memvisualisasikan data guna memperoleh insight awal.

### Dataset "data"

1. **Distribusi fitur `brand`**

    ![image](https://github.com/user-attachments/assets/bb2a503c-b153-4ed2-8bb1-a30b63d3b174)
    
    Visualisasi frekuensi brand ponsel menunjukkan bahwa dari total 10 merek ponsel dalam dataset, Samsung menjadi yang paling dominan dengan 8 model, diikuti oleh Apple (6), Motorola, OnePlus, dan Xiaomi (masing-masing 4). Merek lain seperti Google, Asus, Oppo, Vivo, dan Sony hanya memiliki 1–3 model. 

2. **Distribusi fitur `model`**

    ![image](https://github.com/user-attachments/assets/0ef19dca-cc02-4ede-ac5c-ddc5879c46ab)
    
    Dataset ini mencakup 33 model ponsel yang beragam, mulai dari berbagai seri iPhone (seperti iPhone SE 2022, iPhone 13 series), seri Galaxy dari Samsung (termasuk Galaxy A, S, dan Z), serta model dari merek lain seperti Pixel, Nord, Redmi, Poco, Xperia, dan Moto. Keberagaman model ini menunjukkan cakupan yang luas pada berbagai segmen pasar dan brand, memberikan peluang analisis yang komprehensif terkait performa dan preferensi pengguna terhadap tiap model.

3. **Distribusi `operating system`**

   ![image](https://github.com/user-attachments/assets/7934a57c-6f21-4f75-8d6a-10ca492b39db)

    
    Berdasarkan visualisasi fitur sistem operasi, mayoritas pengguna dalam data menggunakan Android (81,8%), sementara sisanya menggunakan iOS (18,2%). Hal ini menunjukkan bahwa Android lebih banyak diminati atau lebih mudah diakses oleh pengguna dalam data yang dianalisis. Perbedaan ini juga bisa mencerminkan preferensi pasar, ketersediaan perangkat, atau faktor ekonomi yang memengaruhi pilihan sistem operasi.

4. **Distribusi `internal memory`**

    ![image](https://github.com/user-attachments/assets/96beddc2-2307-4ab4-8478-fa1716e4c745)
    
    Berdasarkan visualisasi distribusi kapasitas memori internal, terlihat bahwa varian 128 GB merupakan yang paling banyak digunakan oleh pengguna dengan jumlah 20 unit. Selanjutnya, memori internal 256 GB digunakan oleh 6 pengguna, sementara varian lainnya seperti 64 GB, 32 GB, dan 256 GB masing-masing digunakan oleh 3 pengguna. Varian dengan kapasitas terbesar, yaitu 512 GB, hanya digunakan oleh 1 pengguna. Pola ini menunjukkan bahwa memori internal 128 GB menjadi pilihan yang paling umum, kemungkinan karena menawarkan keseimbangan antara kapasitas yang cukup besar dan harga yang masih terjangkau.

5. **Distribusi `RAM`**

    ![image](https://github.com/user-attachments/assets/55237d06-0c33-4e10-8f6c-12e3292f2162)
    
    Berdasarkan visualisasi distribusi jumlah RAM yang digunakan, dengan puncak penggunaan mencapai 8 GB, diikuti oleh 4 GB dan 6 GB yang memiliki jumlah yang sama. Penggunaan RAM yang paling rendah terjadi pada 3 GB dan 12 GB. Hal ini mengindikasikan bahwa sebagian besar kebutuhan memori berkisar di antara 6 hingga 8 GB, sedangkan penggunaan di luar rentang ini lebih jarang, mungkin menunjukkan preferensi terhadap kapasitas memori tertentu sesuai kebutuhan pengguna. Pemahaman pola ini penting untuk mengoptimalkan pengelolaan sumber daya yang sesuai dengan kebutuhan pengguna.

6. **Distribusi `performance`**

   ![image](https://github.com/user-attachments/assets/f885aefb-cb4b-4882-9b7c-504602982c0f)

    
    Berdasarkan visualisasi fitur performance, terlihat bahwa sebagian besar data (63,6%) memiliki nilai performa lebih tinggi dari rata-rata (6,22), sementara sisanya (36,4%) memiliki performa yang sama atau lebih rendah dari rata-rata tersebut. Hal ini mengindikasikan bahwa performa secara umum cenderung berada di atas nilai rata-rata, menunjukkan keberhasilan dalam mencapai tingkat performa yang lebih baik. Pola ini penting untuk dipahami agar dapat menargetkan peningkatan performa di area yang kurang dari rata-rata dan memaksimalkan potensi dari pengguna atau sistem yang dianalisis.

7. **Distribusi `main camera`**

    ![image](https://github.com/user-attachments/assets/ab19ca64-6cad-49b8-9f41-6430ca43c880)
    
    Berdasarkan visualisasi distribusi main camera, jumlah penggunaan utama kamera berkisar di angka 12 hingga 108, dengan frekuensi tertinggi tercatat pada 50 dan 64. Terdapat juga kategori dengan jumlah penggunaan yang lebih rendah, seperti 13, 48, dan 108, yang menunjukkan variability dalam preferensi pengguna terhadap jumlah kamera utama. Pola ini mengindikasikan bahwa sebagian besar pengguna cenderung menggunakan sekitar 12 hingga 108 kamera utama, namun ada juga yang memiliki jumlah yang lebih rendah maupun lebih tinggi, menandakan adanya berbagai kebutuhan dan tingkat penggunaannya.

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

    ![image](https://github.com/user-attachments/assets/2c88c83c-38ac-4b59-a10f-0228d5e2d58c)
    
    Berdasarkan visualisasi fitur release year, hampir setengah dari jumlah penjualan terjadi pada tahun 2021 dan 2022, keduanya dengan porsi sekitar 48,5%. Sementara itu, penjualan pada tahun 2018 hanya sekitar 3%, menunjukkan bahwa volume penjualan jauh lebih kecil dibandingkan dua tahun terakhir tersebut. Pola ini mengindikasikan bahwa pertumbuhan penjualan pesat terjadi setelah 2018, dengan puncaknya sekitar 2021 dan 2022, kemungkinan menandakan peningkatan popularitas atau adopsi produk di periode tersebut.

### Dataset "rating"

1. **Distribusi `userID`**

    ![image](https://github.com/user-attachments/assets/77522076-3061-4ef6-aa62-b042aabfe63a)
    
    Distribusi jumlah review untuk setiap pengguna menunjukkan bahwa mayoritas pengguna memberikan jumlah review yang konsisten sebanyak 10 kali. Pola ini mengindikasikan bahwa sebagian besar pengguna aktif dalam memberikan review secara reguler dan konsisten.

2. **Distribusi `cellphoneID`**

    ![image](https://github.com/user-attachments/assets/0956d4c3-aa06-4e92-a9ee-cd5f2459b676)
    
    Distribusi jumlah review per `cellphone_id` menunjukkan variasi aktivitas pengguna dalam memberikan review. Sebagian besar `cellphone_id` memberikan antara 20 sampai 35 review, dengan puncak di sekitar 8 dan 15, yang menunjukkan bahwa sejumlah pengguna cukup aktif. Ada juga beberapa `cellphone_id` yang memiliki jumlah review lebih tinggi, mendekati 33, menandakan pengguna yang sangat aktif. Data ini mengindikasikan adanya variasi tingkat partisipasi pengguna dalam memberikan review, dengan sebagian besar menunjukkan tingkat aktivitas sedang hingga tinggi.

3. **Distribusi `rating`**

    ![image](https://github.com/user-attachments/assets/8cc9a1cf-9bbe-469c-b1a4-078adaa98636)
    
    Berdasarkan visualisasi distribusi rating, sebagian besar pengguna memberikan rating tinggi, terutama pada angka 7 dan 8, dengan frekuensi tertinggi di sekitar rating 8. Ini menunjukkan bahwa mayoritas pengguna cenderung memberikan penilaian positif terhadap produk atau layanan tersebut. Rating di bawah 5 sangat jarang, menandakan tingkat ketidakpuasan yang rendah. Namun, ada satu angka yang tidak relevan dan tampak sebagai outlier, yaitu angka 18. Rating 18 ini tidak sesuai dengan skala rating yang umum digunakan, sehingga kemungkinan merupakan data yang tidak valid atau kesalahan input dan perlu penanganan lebih lanjut.

### Dataset "users"

1. **Distribusi `age`**

    ![image](https://github.com/user-attachments/assets/76ad9299-0648-486b-a6be-0a131d9795ab)
    
    Berdasarkan visualisasi distribusi usia, menunjukkan bahwa sebagian besar responden berusia antara 21 dan 61 tahun, dengan puncak pada usia sekitar 25 dan 32 tahun. Frekuensi tertinggi terdapat pada usia 25 tahun, yang menunjukkan bahwa kelompok usia ini paling aktif dalam memberikan data atau respons. Selain itu, terdapat variasi yang cukup luas di seluruh rentang usia, mengindikasikan beragam peserta dari berbagai kelompok usia. Data ini menggambarkan bahwa berbagai kelompok usia berpartisipasi, dengan kecenderungan utama di kalangan muda dewasa.

2. **Distribusi `gender`**

    ![image](https://github.com/user-attachments/assets/6c33d9b0-cb67-4429-a033-af105999c30a)
    
    Visualisasi distribusi gender menunjukkan bahwa jumlah pengguna pria (Male) jauh lebih tinggi dibandingkan pengguna perempuan (Female). Jumlah pengguna pria mencapai sekitar 50, sementara pengguna perempuan sekitar 45, dan data yang tidak relevan muncul pada kategori "-Select Gender" sebanyak sekitar 4. Kehadiran kategori "-Select Gender" menandakan adanya data yang tidak lengkap atau tidak terklasifikasi dengan baik, sehingga sebaiknya dihapus atau diperiksa lebih lanjut agar analisis menjadi lebih akurat. Secara keseluruhan, mayoritas pengguna teridentifikasi sebagai pria, dengan jumlah yang jauh lebih banyak dibandingkan wanita.

5. **Distribusi `occupation`**

    ![image](https://github.com/user-attachments/assets/c32d6593-e1db-43cd-9d7d-b56756418959)
    
    Data occupation pada pengguna menunjukkan keberagaman yang tinggi dengan total 45 jenis pekerjaan unik, mulai dari profesional teknis seperti 'software developer' dan 'technical engineer', hingga peran administratif dan layanan seperti 'team leader', 'accountant', dan 'sales'. Variasi ini menggambarkan profil pengguna yang beragam, mencakup berbagai sektor industri dan tingkat jabatan, yang dapat memengaruhi preferensi dan kebutuhan dalam memilih ponsel. 

## Data Preparation
Proses ini meliputi penggabungan berbagai dataset yang relevan, seperti menggabungkan data rating dengan data pengguna dan data lainnya, agar mendapatkan satu dataset lengkap. Selain itu, perlu juga dilakukan pengecekan dan penanganan missing value, duplikat data, serta validasi konsistensi data agar hasil analisis menjadi akurat dan dapat diandalkan.

### Teknik Data Preparation

1. **Penggabungan Dataset**
    Data dari tiga sumber utama, yaitu data spesifikasi ponsel (cellphones data), data rating pengguna (cellphones rating), dan data demografi pengguna (cellphones users) digabungkan menjadi satu dataframe terpadu untuk memudahkan analisis dan pemodelan.
2. **Menghapus duplicate data**
   Langkah penghapusan duplikat pada kolom cellphone_id dilakukan menggunakan fungsi drop_duplicates('cellphone_id') untuk memastikan hanya satu entri unik per produk digunakan dalam proses Content-Based Filtering. Hal ini penting agar perhitungan kemiripan antar item tidak terdistorsi oleh data duplikat.
3. **Handling Missing Values**
    Nilai yang hilang (missing values) pada kolom-kolom penting, seperti kolom occupation, diidentifikasi dan dihapus agar tidak mempengaruhi kualitas model dan analisis.
4. **Mengubah Format Penulisan**
    Penulisan teks pada kolom kategorikal diubah menjadi format konsisten, seperti mengubah semua nilai pada kolom occupation menjadi huruf kecil (lowercase), agar data yang seharusnya sama tidak dianggap berbeda karena perbedaan format penulisan.
5. **Mereplace Nilai yang Salah atau Tidak Konsisten**
    Beberapa nilai pada kolom occupation yang mengalami kesalahan penulisan atau inkonsistensi diperbaiki. Contohnya, 'Healthare' diperbaiki menjadi 'healthcare', dan singkatan 'it' diganti menjadi bentuk lengkap 'information technology'.

#### Proses Data Preparation | Content-Based Filtering

1. Menghapus data duplikat berdasarkan kolom `cellphone_id` untuk memastikan setiap item unik sebelum pemodelan Content-Based Filtering. Hal ini mencegah bias dan inkonsistensi data.
2. Melakukan konversi data menjadi format list agar memudahkan proses transformasi dan pemrosesan selanjutnya dalam pembuatan matriks fitur.
3. Membuat dictionary `phone_new` yang berisi fitur utama ponsel (`cellphone_id`, `brand`, `model`, `operating_system`) sebagai input untuk model Content-Based Filtering. Langkah ini memudahkan transformasi dan perhitungan kemiripan antar produk.

 ```python
   phone_new = pd.DataFrame({
   'cellphone_id': cellphone_id,
   'brand': brand,
   'model': model,
   'operating_system': operating_system,
   })
   ```

4. Melakukan TF-IDF lalu fit dan transformasi ke bentuk matriks, karena TF-IDF bekerja optimal pada data teks, hanya kolom bertipe object seperti brand, model, dan operating_system yang dipilih.
        
    ```python
    tfidf_matrix = tf.fit_transform(phone_new['brand'])
    ```  
   Output berupa matriks ukuran (33,10) yaitu `jumlah_data` dan `jumlah_unique_brand`.

#### Proses Data Preparation | Collaborative Filtering

1. Encoding menjadi format numerik dan mapping pada fitur `user_id` dan `cellphone_id` untuk keperluan model Collaborative Filtering berbasis embedding. Proses ini diperlukan agar model dapat mengolah data pengguna dan produk secara efisien.
2. Melakukan konversi tipe data pada kolom `rating` menjadi tipe data `float32` untuk memastikan bahwa data dapat diproses dengan tepat dalam model machine learning. Normalisasi rating tidak dilakukan karena model dapat menangani nilai asli rating dengan baik dan agar hasil prediksi tetap mudah diinterpretasi dalam skala asli.
3. Menghapus outlier pada kolom rating, seperti nilai di luar rentang valid, yaitu 18 agar data interaksi yang digunakan bersih dan valid.
4. Melakukan randomize dataset menggunakan fungsi sample(frac=1, random_state=42) untuk memastikan distribusi data yang merata dan menghindari bias saat proses pembagian data menjadi training dan testing.
5. Melakukan mapping data user dan cellphone menjadi satu value agar dapat diproses oleh model embedding dalam Collaborative Filtering dengan efisien.
6. Melakukan pembagian data menjadi data train sebanyak 791 baris (80%) dan data test sebanyak 198 baris (20%).

### Alasan Melakukan Data Preparation

1. Handling Missing Values: Nilai yang hilang dapat menyebabkan bias atau error dalam analisis dan model, sehingga perlu diatasi agar data yang digunakan lengkap dan konsisten.
2. Removing Outliers: Data ekstrim atau tidak valid dapat merusak akurasi model dan menghasilkan prediksi yang tidak realistis, sehingga penghapusan outlier membantu meningkatkan performa dan kestabilan model.
3. Mengubah Format Penulisan: Konsistensi penulisan data kategorikal penting agar nilai yang sama tidak terpisah menjadi kategori berbeda, yang dapat memengaruhi analisis dan hasil pemodelan.
4. Memperbaiki Value yang Salah: Memperbaiki kesalahan penulisan mencegah duplikasi kategori dan memastikan interpretasi data yang benar dan valid.
5. Pembagian Dataset: Memisahkan data untuk subset pelatihan dan pengujian memungkinkan evaluasi model secara objektif terhadap data yang belum pernah dilihat, sehingga mengukur kemampuan generalisasi model.
6. Encoding dan Transformasi Data: Mengubah data kategorikal menjadi format numerik dan mengonversi tipe data numerik agar sesuai dengan kebutuhan algoritma, sehingga model dapat belajar secara efektif dan efisien.

### Hasil Splitting Data

| Kategori        | Jumlah Data |
|-----------------|-------------|
| Seluruh Dataset | 989         |
| Data Training   | 791         |
| Data Testing    | 198         |

## Model Development

Pada tahap ini, dua pendekatan utama yang digunakan untuk membangun sistem rekomendasi ponsel dibahas secara mendalam, yaitu Content-Based Filtering dan Collaborative Filtering. Kedua metode ini dipilih karena masing-masing memiliki kekuatan dan kelemahan yang berbeda sehingga dapat memberikan rekomendasi yang relevan dari sisi konten produk maupun interaksi pengguna.

### Content-Based Filtering (CBF)
Content-Based Filtering berfokus pada atribut atau fitur dari item itu sendiri, dalam hal ini fitur ponsel seperti merek (brand), model, dan sistem operasi. Metode ini memanfaatkan teknik TF-IDF Vectorizer sebagai bagian dari data preparation, yang mengukur pentingnya sebuah kata atau fitur dalam konteks data. Setelah itu, dilakukan perhitungan cosine similarity antar item untuk menentukan tingkat kemiripan setiap ponsel dengan ponsel yang sudah disukai pengguna. Hasilnya adalah daftar rekomendasi ponsel yang paling mirip dengan ponsel yang telah digunakan atau disukai oleh pengguna dengan top-N recommendation yang dipersonalisasi berdasarkan preferensi konten pengguna.

**Parameter dan teknik utama pada CBF**:

1. TF-IDF Vectorizer: Metode ini dilakukan pada bagian Data Preparation untuk mengubah fitur teks menjadi matriks bobot numerik yang merefleksikan frekuensi dan kepentingan kata, memungkinkan penghitungan kemiripan antar item secara efektif.
2. Cosine Similarity: Metode ini digunakan untuk mengukur kemiripan antar vektor fitur. Nilai cosine similarity berkisar antara 0 sampai 1, di mana 1 berarti dua item sangat mirip.

**Tahapan proses CBF**:

1.  Membuat data frame fitur (phone_new) yang berisi kolom deskriptif yang digunakan (brand, model, operating system) pada bagian Data Preparation.
2.  Melakukan transformasi fitur teks menjadi representasi numerik dengan TF-IDF Vectorizer pada bagian Data Preparation.
3.  Menghitung kemiripan antar ponsel menggunakan cosine similarity.
4.  Membuat fungsi rekomendasi yang menerima nama model ponsel dan mengembalikan rekomendasi 4 ponsel teratas beserta detail brand dan sistem operasi.
5.  Melakukan evaluasi performa model dengan metrik precision, recall, dan F1-score.

**Cara kerja algoritma CBF**:

Algoritma CBF mengubah fitur deskriptif setiap ponsel menjadi representasi numerik yang memudahkan penghitungan kemiripan antar produk. Saat pengguna memasukkan nama model ponsel, sistem menghitung kemiripan cosine antara ponsel tersebut dengan semua ponsel lain di dataset, kemudian merekomendasikan produk yang memiliki similarity tertinggi.

**Contoh Interaksi CBF**:

Jika pengguna memilih ponsel "Galaxy A13", algoritma akan:
1. Mengambil profil teks "Galaxy A13".
2. Mengubah profil tersebut ke dalam vektor TF-IDF.
3. Menghitung cosine similarity dengan seluruh ponsel lain.
4. Mengembalikan daftar ponsel dengan similarity tertinggi seperti "Galaxy Z Flip 3", "Galaxy S22 Plus", dan lain-lain.

**Contoh Output Top-N Recommendation untuk CBF**:

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

Pendekatan Collaborative Filtering memanfaatkan data interaksi pengguna dengan item, seperti rating yang diberikan pengguna terhadap ponsel. Metode ini tidak bergantung pada fitur produk, melainkan mencari pola kesamaan preferensi antar pengguna atau antar item berdasarkan data interaksi. Dalam proyek ini, digunakan model neural network dengan embedding yang merepresentasikan pengguna dan item sebagai vektor berdimensi rendah, sehingga menangkap pola laten preferensi dengan efisien. Model dilatih dengan loss function Binary Crossentropy dan optimizer Adam, serta dimonitor menggunakan metrik Root Mean Squared Error (RMSE). Hasilnya adalah top-N recommendation yang memanfaatkan pola kolektif untuk menyarankan item yang relevan, terutama efektif jika data interaksi pengguna cukup banyak.

**Parameter dan teknik utama pada CF**:

1. Model Neural Network dengan Embedding
   Dibangun menggunakan kelas RecommenderNet berbasis Keras Model, dengan:
   
   - Embedding layer untuk user dan item dengan dimensi embedding 50: Dimensi 50 dipilih sebagai kompromi antara representasi fitur yang cukup kaya untuk menangkap pola preferensi dan efisiensi komputasi agar model tidak terlalu kompleks dan mudah dilatih.
   - Output layer memprediksi rating menggunakan sigmoid activation: Sigmoid dipilih karena rating diperlakukan sebagai probabilitas atau skor antara 0 dan 1 yang perlu diprediksi, sehingga fungsi aktivasi ini cocok untuk output bernilai terbatas.
     
2. Loss Function: Binary Crossentropy
   Binary Crossentropy dipilih untuk meminimalkan perbedaan antara rating aktual dan prediksi dalam bentuk probabilitas, sangat sesuai untuk tugas klasifikasi biner atau prediksi probabilistik dalam sistem rekomendasi.
   
3. Optimizer: Adam dengan learning rate 0.001
   Adam digunakan karena kemampuannya menggabungkan kelebihan metode adaptive learning rate dan momentum, sehingga mempercepat konvergensi dan stabil saat training dengan learning rate 0.001 yang merupakan nilai umum efektif untuk memulai training.
   
4. Metrics: Root Mean Squared Error (RMSE)
   RMSE dipilih sebagai metrik utama karena memberikan ukuran deviasi prediksi dalam satuan yang sama dengan rating asli, memudahkan interpretasi performa model dalam hal akurasi prediksi rating.

**Tahapan proses CF**:

1. Melakukan encoding user_id dan cellphone_id menjadi indeks numerik.
2. Membangun Model
   Membuat kelas model neural network dengan embedding untuk user dan item.
3. Training Model dengan batch size 8 selama 100 epoch. Batch size 8 dipilih untuk mempercepat pembaruan parameter dengan memori yang efisien, sedangkan 100 epoch memberikan cukup kesempatan model belajar pola data secara menyeluruh.
4. Mengevaluasi model menggunakan RMSE untuk mengukur selisih prediksi pada data training dan testing.
5. Menghasilkan rekomendasi top-N berdasarkan prediksi rating tertinggi untuk setiap pengguna.

**Cara kerja algoritma CF**:

Model mempelajari pola rating antar pengguna dan item, sehingga dapat memprediksi rating untuk item baru bagi pengguna tertentu. Ini memungkinkan rekomendasi produk yang sesuai dengan preferensi pengguna meskipun produk tersebut tidak mirip secara fitur dengan yang sudah pernah dipilih.

**Contoh Interaksi CF**:

Misalnya, pengguna dengan ID 37 ingin rekomendasi:
1. Model mencari pengguna lain dengan pola rating serupa.
2. Memperkirakan rating pengguna 37 terhadap ponsel yang belum diulas.
3. Mengembalikan daftar ponsel dengan prediksi rating tertinggi sebagai rekomendasi. 

**Contoh Output Top-N Recommendation untuk CF**:

![image](https://github.com/user-attachments/assets/02c93dc8-40cb-4011-a155-ae910317f0d7)


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

| Metrik     | Nilai |
|------------|--------|
| Precision@5| 1.00   |
| Recall@5   | 1.00   |
| F1@5       | 1.00   |

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

![image](https://github.com/user-attachments/assets/f6b88ab5-c075-4d8e-983f-78004a62aeb4)



| Dataset       | RMSE  |
|---------------|-------|
| Data Train    | 0.0125|
| Data Test     | 0.3169|

Grafik model metrics menunjukkan bahwa nilai root mean squared error (RMSE) pada data training menurun drastis hingga mencapai sekitar 0.0125, menandakan model berhasil belajar dengan sangat baik pada data pelatihan. Meski demikian, nilai RMSE test sebesar 0.3169 masih tergolong rendah, menunjukkan bahwa model tetap mampu memberikan prediksi yang cukup akurat pada data testing meskipun performanya tidak sebaik pada data training.

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

- Bączkiewicz, A., Kizielewicz, B., Shekhovtsov, A., Wątróbski, J., & Sałabun, W. (2021). Methodical aspects of MCDM based E-commerce recommender system. Journal of Theoretical and Applied Electronic Commerce Research, 16(6), 2192-2229.
- Kim, T. Y., Ko, H., Kim, S. H., & Kim, H. D. (2021). Modeling of recommendation system based on emotional information and collaborative filtering. Sensors, 21(6), 1997.
- Khusna, A. N., Delasano, K. P., & Saputra, D. C. E. (2021). Penerapan User-Based Collaborative Filtering Algorithm. MATRIK: Jurnal Manajemen, Teknik Informatika dan Rekayasa Komputer, 20(2), 293-304.
- Singh, P., Gupta, M., Kumar, A., Sikdar, P., & Sinha, N. (2021). E-Grocery retailing mobile application: Discerning determinants of repatronage intentions in an emerging economy. International Journal of Human–Computer Interaction, 37(19), 1783-1798.
- Wening, Y. A. T. (2024). Sistem Rekomendasi Handphone Berbasis Spesifikasi dan Harga Menggunakan Algoritma Decision Tree.
