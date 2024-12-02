# Laporan Proyek Machine Learning - Ziyad Muhammad Adzin Azzufari

## Domain Proyek

Pada proyek ini, saya fokus pada **forecasting pergerakan indeks NASDAQ** menggunakan model machine learning. Tujuan utamanya adalah untuk memprediksi pergerakan harga indeks NASDAQ dengan mempertimbangkan variabel-variabel makroekonomi dan sentimen pasar yang mempengaruhinya. Dalam proyek ini, variabel yang digunakan meliputi **DXY Price (Dollar Index)**, **Fed Funds Rate**, dan **Sentimen berita** terkait dengan **Fed Rate**, serta **Volume** yang berhubungan dengan pergerakan harga indeks.

**Rubrik/Kriteria Tambahan**:
- Masalah yang diangkat adalah untuk menghubungkan faktor-faktor eksternal seperti suku bunga dan sentimen pasar dengan pergerakan harga NASDAQ, yang dapat membantu investor dalam pengambilan keputusan investasi.
- Berdasarkan riset terkini, pasar saham seringkali dipengaruhi oleh kebijakan moneter yang tercermin dalam **Fed Funds Rate** serta fluktuasi **Dollar Index**, sementara sentimen pasar memegang peranan penting dalam pergerakan harga jangka pendek. 

## Business Understanding

Pada bagian ini, saya mengklarifikasi permasalahan yang dihadapi dan tujuan dari proyek ini.

### Problem Statements

- Bagaimana **Fed Funds Rate** dan **Dollar Index** mempengaruhi pergerakan harga **NASDAQ**?
- Seberapa besar dampak sentimen berita terhadap pergerakan harga **NASDAQ**, terutama yang berkaitan dengan **Fed Rate**?
- Bagaimana cara memanfaatkan variabel-variabel tersebut untuk membangun model yang dapat memprediksi pergerakan harga **NASDAQ**?

### Goals

- Mengidentifikasi hubungan antara **Fed Funds Rate**, **Dollar Index**, dan **sentimen berita** terhadap pergerakan harga **NASDAQ**.
- Membangun model yang akurat untuk memprediksi harga **NASDAQ** berdasarkan variabel tersebut.
- Mengoptimalkan model dengan menggunakan **LSTM** untuk mengatasi masalah time series dan memberikan prediksi yang lebih tepat.

### Solution Statements

- Menggunakan **LSTM (Long Short-Term Memory)** untuk menangani data time series dan mengintegrasikan **sentimen berita** yang dilabelkan menggunakan **Gemma 2 9B Instruct**.
- Melakukan pengujian untuk membandingkan hasil model dan meningkatkan akurasi prediksi.

## Data Understanding

Dataset yang digunakan dalam proyek ini berisi data historis tentang harga **NASDAQ**, **Dollar Index**, **Fed Funds Rate**, dan **sentimen berita** terkait **Fed Rate**. Data berita digunakan untuk mengukur sentimen yang kemudian dipetakan menjadi kategori **positif**, **netral**, dan **negatif**.

### Variabel-variabel pada dataset adalah sebagai berikut:
- **DXY Price**: Nilai Dollar Index yang mencerminkan nilai dolar AS terhadap sekeranjang mata uang asing.
- **Fed Funds Rate**: Tingkat suku bunga yang ditetapkan oleh The Federal Reserve, yang mempengaruhi pasar saham dan obligasi.
- **Negative**: Sentimen berita yang dikategorikan sebagai negatif.
- **Neutral**: Sentimen berita yang dikategorikan sebagai netral.
- **Positive**: Sentimen berita yang dikategorikan sebagai positif.
- **Vol. (Volume)**: Volume perdagangan saham NASDAQ yang memberikan indikasi likuiditas pasar.
- **Price**: Harga indeks NASDAQ yang akan diprediksi.

## Data Preparation

Pada tahap persiapan data, dilakukan beberapa langkah penting sebagai berikut:
1. **Data Cleaning**: Menghapus data yang tidak lengkap dan menangani missing values pada dataset.
2. **Feature Engineering**: Menambahkan fitur yang relevan, seperti perhitungan pergerakan harga indeks NASDAQ, serta pembuatan variabel yang menggambarkan perubahan **Fed Funds Rate** dan **Dollar Index**.
3. **Sentiment Analysis**: Menggunakan **Gemma 2 9B Instruct** untuk melabelkan sentimen berita terkait **Fed Rate** sebagai **positif**, **netral**, atau **negatif**.
4. **Normalization**: Melakukan normalisasi pada fitur-fitur numerik untuk meningkatkan kinerja model, terutama pada **DXY Price**, **Fed Funds Rate**, dan **Volume**.

## Modeling

Model yang digunakan untuk prediksi adalah **LSTM (Long Short-Term Memory)**, yang efektif untuk data time series.

### Tahapan Model:
1. **Preprocessing**: Data dibagi menjadi set pelatihan dan pengujian, serta diubah menjadi format yang sesuai untuk input ke dalam model LSTM.
2. **Training**: Model LSTM dilatih menggunakan data pelatihan yang mencakup variabel independen seperti **DXY Price**, **Fed Funds Rate**, dan **sentimen berita**.
3. **Tuning**: Hyperparameter tuning dilakukan untuk menemukan konfigurasi terbaik untuk model LSTM.

## Evaluation

Metrik evaluasi yang digunakan untuk menilai kinerja model adalah **Mean Squared Error (MSE)**, **Mean Absolute Error (MAE)**, dan **Root Mean Squared Error (RMSE)**. Metrik-metrik ini dipilih karena memberikan gambaran yang jelas mengenai seberapa besar kesalahan antara nilai yang diprediksi dan nilai yang sebenarnya.

- **MSE (Mean Squared Error)**: Mengukur rata-rata kuadrat selisih antara nilai yang diprediksi dan nilai yang sebenarnya. MSE sensitif terhadap outlier, sehingga model dengan **MSE** rendah dianggap lebih baik dalam memprediksi harga.
- **MAE (Mean Absolute Error)**: Mengukur rata-rata perbedaan absolut antara nilai yang diprediksi dan nilai yang sebenarnya. MAE memberikan gambaran seberapa besar rata-rata kesalahan absolut yang terjadi, yang lebih mudah dipahami dibandingkan MSE.
- **RMSE (Root Mean Squared Error)**: Merupakan akar kuadrat dari MSE, yang memberikan gambaran lebih jelas mengenai besarnya kesalahan dalam unit yang sama dengan variabel yang diprediksi. RMSE memberikan bobot lebih pada kesalahan yang lebih besar.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Penjelasan formula metrik evaluasi:
  - $MAE = \frac{1}{n} \sum_{i=1}^{n} |y_i - \hat{y}_i|$

  - $MSE = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2$
    
  - $RMSE = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}$
