# Tugas Analisis Statistik: Deskriptif, Korelasi, dan Regresi

## 1. Informasi Penyusun

- **Nama:** `[ZETRO SIMANGUNSONG]`
- **NIM:** `[2515091057]`
- **Program Studi:** `[SISTEM INFORMASI ]`
- **Mata Kuliah:** Statistika dan Probabilitas

---

## 2. Deskripsi Proyek

Pada bagian ini, jelaskan secara singkat dataset yang Anda gunakan. Apa saja variabel di dalamnya? Apa tujuan dari analisis yang Anda lakukan?

*Contoh:*
> Dataset yang digunakan adalah data `data_startup_saas.csv` yang berisi informasi tentang `Dataset startup SaaS ini berisi data umum mengenai perusahaan, termasuk nama dan jenis layanan yang menggambarkan bidang bisnisnya. Di dalamnya juga terdapat informasi keuangan seperti pendapatan tahunan dan biaya berlangganan untuk melihat skala serta penetapan harga. Selain itu, data nilai pelanggan dan tingkat churn dapat digunakan untuk menilai loyalitas pengguna dan kestabilan bisnis. Namun, karena masih terdapat data yang tidak lengkap dan struktur yang kurang rapi, dataset ini lebih sesuai untuk analisis awal atau eksploratif daripada untuk penarikan kesimpulan yang mendalam`. Variabel kunci dalam dataset ini meliputi `Pendapatan_Tahunan_Miliar_IDR`, `Biaya_Akuisisi_Pelanggan_Juta_IDR`, dan `Nilai_Pelanggan_Juta_IDR`. Tujuan dari proyek ini adalah untuk memahami karakteristik data melalui statistik deskriptif, menguji hubungan antara `Pendapatan_Tahunan_Miliar_IDR` dan `Biaya_Akuisisi_Pelanggan_Juta_IDR` melalui analisis korelasi, serta memprediksi `Nilai_Pelanggan_Juta_IDR` menggunakan `Pendapatan_Tahunan_Miliar_IDR` sebagai prediktor melalui analisis regresi.
## 3. Struktur Proyek

Proyek ini diorganisir ke dalam beberapa folder:
- `/data`: Berisi dataset mentah yang digunakan untuk analisis.
- `/scripts`: Berisi semua skrip R yang digunakan dalam analisis, diurutkan berdasarkan alur kerja.
- `/results`: Berisi output dari analisis, seperti plot, gambar, atau tabel ringkasan.

---

## 4. Cara Menjalankan Analisis

Untuk mereproduksi hasil analisis ini, ikuti langkah-langkah berikut:
1. Pastikan Anda memiliki R dan RStudio terinstal.
2. Buka proyek R ini di RStudio.
3. Instal paket yang diperlukan dengan menjalankan perintah berikut di konsol R:
   ```R
   # install.packages(c("tidyverse", "corrplot", "knitr"))
   ```
4. Jalankan skrip di dalam folder `/scripts` secara berurutan, mulai dari `01_data_preparation.R` hingga `05_analisis_regresi.R`.

---

## 5. Hasil dan Interpretasi

Di bagian ini, mahasiswa diharapkan untuk menyajikan dan menginterpretasikan hasil dari setiap tahap analisis.

### 5.1. Statistik Deskriptif
- **Ukuran Pemusatan (Mean, Median, Modus):**
  - *Tabel atau ringkasan...*
  - Mean = 31,88
  - Median = 31,3
  - Modus = 1,87
  - *Interpretasi:* Jelaskan apa arti dari nilai-nilai tersebut terkait dengan data Anda.
  - Nilai mean 31,88 menunjukkan rata-rata data, namun bisa dipengaruhi oleh nilai yang sangat besar. Median 31,3 yang hampir sama dengan mean menandakan sebagian besar data berada di sekitar nilai tersebut. Sebaliknya, modus 1,87 yang jauh lebih kecil menunjukkan bahwa nilai yang paling sering muncul berada pada kisaran rendah. Perbedaan ini mengindikasikan distribusi data tidak merata (condong ke satu sisi), sehingga median lebih tepat digunakan untuk mewakili nilai tengah data dibandingkan mean
- **Ukuran Sebaran (Standar Deviasi, Range, Kuartil):**
  - *Tabel atau ringkasan...*
  - Standar deviasi = 19,79
  - Range = 1 - 66,89
  - Kuartil =   Min. 1st Qu.  Median  Mean   3rd Qu.  Max. 
               1.00   14.31   31.30   31.88   49.04   66.89 
  - *Interpretasi:* Jelaskan seberapa menyebar data Anda berdasarkan nilai-nilai ini.
Nilai standar deviasi sebesar 19,79 menunjukkan bahwa data memiliki tingkat penyebaran yang cukup besar dari nilai rata-ratanya. Range yang lebar, yaitu dari 1 hingga 66,89, mengindikasikan adanya perbedaan yang signifikan antara nilai terendah dan tertinggi. Berdasarkan kuartil, sebanyak 50% data berada di rentang 14,31 hingga 49,04 dengan median 31,30, yang menandakan bahwa data terkonsentrasi di sekitar nilai tengah namun tetap menyebar cukup luas. Secara keseluruhan, hasil ini menunjukkan bahwa data tidak rapat dan memiliki variasi yang tinggi, sehingga penyebaran data tergolong besar.
- **Visualisasi (Histogram/Boxplot):**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text](https://github.com/zetro-arch/UAS_SDP_SEMESTER1/blob/main/results/boxplot_Pendapatan_Tahunan_Miliar_IDR.png)
  - *Interpretasi:* Jelaskan wawasan apa yang Anda dapatkan dari bentuk distribusi data.
  - Dari boxplot tersebut dapat dilihat bahwa pendapatan tahunan antar startup memiliki perbedaan yang cukup besar. Sebagian besar data berada di kisaran menengah, namun jarak antara nilai terendah dan tertinggi terlihat cukup jauh. Garis median yang berada di sekitar tengah kotak menunjukkan bahwa nilai tengah pendapatan cukup mewakili kondisi umum data, meskipun masih terdapat variasi yang lebar. Tidak terlihat adanya nilai ekstrem yang menyimpang jauh, sehingga perbedaan pendapatan yang ada masih tergolong wajar. Secara keseluruhan, visualisasi ini menunjukkan bahwa pendapatan startup cukup beragam, dengan tingkat sebaran yang tinggi antar perusahaan

### 5.2. Uji Normalitas
- **Hasil Uji Shapiro-Wilk:**
  - *Nilai p-value...*
  - p-value = 1.497e-14
  - *Interpretasi:* Apakah data Anda terdistribusi normal berdasarkan hasil uji? Apa implikasinya?
  - Nilai p-value yang sangat kecil, yaitu 1,497 × 10⁻¹⁴, menunjukkan bahwa data tidak mengikuti distribusi normal. Artinya, pola sebaran data cenderung tidak simetris dan memiliki variasi yang tidak sesuai dengan asumsi normalitas. Dampaknya, analisis yang bergantung pada asumsi data normal sebaiknya tidak digunakan secara langsung. Sebagai gantinya, pendekatan nonparametrik serta penggunaan median dan visualisasi seperti boxplot lebih tepat untuk menggambarkan kondisi data secara nyata.
- **Plot Q-Q:**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text](https://github.com/zetro-arch/UAS_SDP_SEMESTER1/blob/main/results/qqplot_Pendapatan_Tahunan_Miliar_IDR.png)
  - *Interpretasi:* Apakah titik-titik data mengikuti garis lurus? Apa artinya?
  - Titik-titik pada Q-Q plot terlihat tidak membentuk garis lurus, melainkan melengkung dan menyimpang dari garis acuan. Di bagian nilai rendah dan tinggi, titik-titik menjauh dari garis, sementara di bagian tengah hanya sebagian yang mendekati. Hal ini menunjukkan bahwa sebaran data tidak mengikuti pola distribusi normal. Dengan kata lain, data memiliki ketidaksimetrian atau variasi yang cukup besar, sehingga asumsi normalitas tidak terpenuhi dan analisis perlu menggunakan pendekatan yang tidak bergantung pada distribusi normal

### 5.3. Analisis Korelasi
- **Nilai Koefisien Korelasi:**
  - *Nilai r...*
  - "Koefisien Korelasi (r) = 0.996"
  - *Interpretasi:* Seberapa kuat dan apa arah hubungan antara dua variabel yang Anda uji? (misalnya, korelasi positif kuat, negatif lemah, atau tidak ada korelasi).
  - Nilai koefisien korelasi r = 0,996 menunjukkan adanya hubungan yang sangat kuat dan bersifat positif antara dua variabel yang diuji. Ini berarti bahwa ketika salah satu variabel mengalami peningkatan, variabel lainnya hampir selalu ikut meningkat dengan pola yang searah dan konsisten. Kekuatan korelasi yang mendekati angka 1 menandakan bahwa hubungan antar variabel ini sangat erat dan perubahan pada satu variabel berkaitan erat dengan perubahan pada variabel lainnya. Meski demikian, hasil ini hanya menunjukkan adanya keterkaitan yang kuat, bukan hubungan sebab–akibat, sehingga tetap diperlukan analisis lanjutan untuk memahami hubungan tersebut secara lebih mendalam.
- **Visualisasi (Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text](https://github.com/zetro-arch/UAS_SDP_SEMESTER1/blob/main/results/scatterplot_Pendapatan_Tahunan_Miliar_IDR_vs_Biaya_Akuisisi_Pelanggan_Juta_IDR.png)
  - *Interpretasi:* Apakah pola pada scatter plot mendukung hasil koefisien korelasi?
  - Ya, pola pada scatter plot jelas mendukung hasil koefisien korelasi. Titik-titik data membentuk pola yang sangat rapat dan mengikuti garis lurus dengan arah naik, sesuai dengan nilai korelasi yang sangat tinggi dan positif (r mendekati 1). Garis tren linear yang ditampilkan juga memperkuat bahwa hubungan antara pendapatan tahunan dan biaya akuisisi pelanggan bersifat linier dan konsisten. Artinya, semakin besar pendapatan tahunan, semakin tinggi pula biaya akuisisi pelanggan, dengan variasi yang relatif kecil di sekitar garis tren. Pola visual ini selaras dengan hasil perhitungan korelasi dan menunjukkan bahwa hubungan kedua variabel tersebut bukan kebetulan, melainkan hubungan yang sangat kuat secara statistik.

### 5.4. Analisis Regresi
- **Model Regresi:**
  - *Persamaan regresi: Y = b0 + b1*X*
  - (b0) = 1.37
  - (b1) = 1.01
  - Y = 1.37 + 1.01X
  - *Interpretasi:* Jelaskan arti dari koefisien intercept (b0) dan slope (b1) dalam konteks data Anda.
  - Model regresi Y = 1,37 + 1,01X menggambarkan adanya hubungan linier antara variabel X dan Y. Nilai intercept (b0) sebesar 1,37 menunjukkan perkiraan nilai Y saat X berada pada nilai nol, yang dapat dipahami sebagai nilai awal Y tanpa pengaruh dari X. Sementara itu, koefisien slope (b1) sebesar 1,01 berarti bahwa setiap peningkatan satu satuan pada X akan menyebabkan Y meningkat sekitar 1,01 satuan. Koefisien ini menunjukkan bahwa perubahan X dan Y terjadi hampir sebanding, sehingga kenaikan X diikuti oleh kenaikan Y dengan besaran yang hampir sama.
- **Evaluasi Model (R-squared):**
  - *Nilai R-squared...*
  - R-squared = 0.991 atau 99.1 %"
  - *Interpretasi:* Berapa persen variasi dari variabel dependen yang dapat dijelaskan oleh model regresi Anda?
  - Nilai R-squared sebesar 0,991 atau 99,1% menunjukkan bahwa model regresi memiliki kemampuan yang sangat kuat dalam menjelaskan variasi pada variabel dependen. Artinya, sekitar 99,1% perubahan pada variabel terikat dapat dijelaskan oleh variabel independen yang digunakan dalam model regresi tersebut. Sementara itu, hanya sekitar 0,9% variasi sisanya yang dipengaruhi oleh faktor lain di luar model atau oleh kesalahan acak. Hasil ini mengindikasikan bahwa hubungan antara variabel-variabel dalam model sangat erat dan model yang dibangun memiliki tingkat kecocokan yang sangat baik terhadap data yang dianalisis, sehingga dapat digunakan untuk menggambarkan hubungan antar variabel secara cukup akurat.
- **Visualisasi (Garis Regresi pada Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text](https://github.com/zetro-arch/UAS_SDP_SEMESTER1/blob/main/results/plot_regresi_Pendapatan_Tahunan_Miliar_IDR_vs_Biaya_Akuisisi_Pelanggan_Juta_IDR.png)
  - *Interpretasi:* Jelaskan bagaimana garis regresi merepresentasikan hubungan antara variabel.
  - Garis regresi pada grafik menggambarkan hubungan linear positif yang sangat kuat antara pendapatan tahunan dan biaya akuisisi pelanggan. Arah garis yang menanjak menunjukkan bahwa peningkatan pendapatan tahunan diikuti oleh peningkatan biaya yang dikeluarkan untuk memperoleh pelanggan. Garis ini mencerminkan nilai rata-rata biaya akuisisi pelanggan yang diprediksi pada setiap tingkat pendapatan, sedangkan titik-titik di sekitarnya merepresentasikan data aktual. Nilai Adjusted R-squared sebesar 0,991 menandakan bahwa sebagian besar variasi biaya akuisisi pelanggan dapat dijelaskan oleh pendapatan tahunan, sehingga model memiliki tingkat ketepatan yang sangat tinggi. Dari sudut pandang bisnis, temuan ini menunjukkan bahwa pertumbuhan pendapatan perusahaan sejalan dengan meningkatnya investasi dalam upaya pemasaran dan akuisisi pelanggan.

---

## 6. Kesimpulan

Rangkum temuan utama dari analisis Anda dalam beberapa kalimat. Apa wawasan paling penting yang Anda peroleh?
Berdasarkan hasil analisis yang telah dilakukan, dapat disimpulkan bahwa data startup SaaS yang digunakan memiliki tingkat variasi yang cukup tinggi dan tidak mengikuti distribusi normal. Dari statistik deskriptif terlihat bahwa nilai pendapatan tahunan antar startup sangat beragam, sehingga median lebih tepat digunakan untuk menggambarkan kondisi data dibandingkan nilai rata-rata. Uji normalitas melalui Shapiro-Wilk dan Q-Q plot juga menguatkan bahwa data tidak berdistribusi normal, sehingga analisis tidak dapat sepenuhnya mengandalkan asumsi statistik klasik. Hasil analisis korelasi menunjukkan hubungan yang sangat kuat dan searah antara pendapatan tahunan dan biaya akuisisi pelanggan, yang juga terlihat jelas dari pola titik pada scatter plot. Analisis regresi kemudian memperlihatkan bahwa pendapatan tahunan memiliki peran yang sangat besar dalam menjelaskan perubahan biaya akuisisi pelanggan. Secara keseluruhan, wawasan penting dari analisis ini adalah bahwa pertumbuhan pendapatan startup berjalan seiring dengan meningkatnya biaya untuk memperoleh pelanggan, sehingga perusahaan perlu mengelola strategi pemasaran dan pertumbuhan bisnis secara lebih cermat agar tetap efisien dan berkelanjutan.

