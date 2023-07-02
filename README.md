# Laporan Proyek Machine Learning - Rizki Alvian

![Logo BRI](https://github.com/rizkialvian/Machine_Learning_Terapan_Proyek_Pertama/blob/ad462764904d860778e783fe29d30c8d1b6a56c2/assets/BRI.PNG?raw=true)

## Domain proyek
### Latar Belakang
Pasar modal menawarkan berbagai macam kegiatan, termasuk investasi. Berinvestasi adalah tindakan menunda konsumsi saat ini untuk menarik konsumsi masa depan dalam menghadapi faktor risiko yang tidak pasti. Produk investasi terpenting di pasar modal adalah saham, obligasi, dan dana investasi. Saham adalah tanda bahwa seseorang menerima dana untuk bisnis atau perseroan terbatas. Harga saham digunakan untuk investasi saham. Harga saham adalah harga yang ditetapkan perusahaan sehubungan dengan perusahaan lain dan digunakan untuk memantau kualitas sahamnya dari waktu ke waktu.

Tren investasi saham terus tercermin di pasar modal, termasuk perbankan yang merupakan lembaga jasa keuangan yang berperan penting dalam perekonomian nasional, di mana harga saham juga memegang peranan penting. Berdasarkan pada Undang-Undang RI Nomor 10 Tahun 1998 [1], Bank adalah badan usaha yang menghimpun dana dari masyarakat dalam bentuk simpanan dan menyalurkannya kepada masyarakat dalam bentuk kredit dan bentuk-bentuk lainnya dalam rangka meningkatkan taraf hidup rakyat banyak.

Bank Rakyat Indonesia (Bank BRI) merupakan salah satu perbankan nasional terbaik yang mampu bersaing dalam industri perbankan nasional. Oleh karena itu, penentuan prediksi atau proyeksi harga saham jangka pendek, khususnya perubahan harga saham harian, memerlukan metode, model, atau pendekatan yang harus diuji keakuratannya. Semakin divalidasi keakuratan model peramalan jangka pendek, semakin diinginkan penggunaannya oleh pelaku pasar.

Beberapa metode dapat digunakan untuk melakukan prediksi, salah satu metode yang dapat digunakan adalah Long Short Term Memory (LSTM). Menurut Wang [2], LSTM adalah teknik untuk mengembangkan Recurent Naural network (RNN) yang diciptakan oleh Hochreiter dan Schmidhuber pada 1997 yang mengurangi ketergantungan pada peramalan jangka panjang, terutama pada data deret waktu. Seperti yang dilaporkan dalam penelitian sebelumnya oleh Sayudi [3] LSTM memiliki Oblivion Gates yang digunakan untuk mengawetkan informasi dari pola data dengan melihat data mana yang dipertahankan dan mana yang dihilangkan.

Penelitian sebelumya tentang penggunaan metode LSTM sudah banyak dilakukan, diantaranya oleh Arfan dan Lusiana [4] tentang prediksi harga saham di Indonesia menggunakan algoritma LSTM dengan SVR, dan diperoleh hasil bahwa model mampu memprediksi harga saham pada tahun 2017-2019 dengan performa yang baik dan tingkat kesalahan yang relatif kecil. Maka dapart dikatakan bahwa LSTM mampu menanggulangi ketergantungan jangka panjang dan mampu memprediksi harga saham dengan hasil yang akurat. Penelitian selanjutnya oleh Alawiyah [5] dengan judul pemodelan menggunakan pendekatan Recuerent Naural Network Long Short Term Memory (RNN-LSTM) pada harga emas, dijelaskan bahwa dalam prosesnya LSTM memerlukan parameter yang tepat untuk memperoleh hasil akurasi yang kuat. Parameter analisis yang dilakukan yaitu menentukan nilai neuron hiden layer dan max epoch dengan komposisi data latih dan data uji yang tepat untuk memperoleh model terbaik. Hasil analisis yang dilakukan dengan data training 80% dan testing 20% , dengan nilai neuron 30 dan max epoch 500 dan optimasi Adam dapat melakukan prediksi harga emas dengan baik, dilihat dari nilai error MAPE 1,09%.

## Business Understanding
### Problem Statements
Adapun problem statement dari pernyataan masalah latar belakang adalah sebagai berikut:
* Bagaimana gambaran umum harga saham PT Bank Rakyat Indonesia Tbk?
* Bagaimana cara preprocessing pada data PT Bank Rakyat Indonesia Tbk yang akan digunakan untuk membuat model yang baik?
* Bagaimana struktur terbaik pembentukan model dalam prediksi harga saham PT BRI Tbk menggunakan algoritma Long Short Term Memory?
* Bagaimana tingkat keakurasian model dengan Long Short Trem Memory?

### Goals
Adapun goals adalah sebagai berikut:
* Dapat mengetahui gambaran umum harga saham PT Bank Rakyat Indonesia Tbk.
* Melakukan preprocessing data sehingga data tersebut siap untuk di latih oleh model Machine Learning.
* Untuk preprocessing data dapat dilakukan beberapa teknik, diantaranya:
  * Melakukan drop kolom pada kolom yang tidak penting / yang tidak berpengaruh pada prediksi harga.
  * Handling null value, jika ada.
  * Melakukan Encoding terhadap kolom yang bertipe object atau categorical, jika ada.
  * Melakukan pembagian data menjadi dua bagian dengan rasio 80% untuk train dan 20% untuk test.
  * Melakukan MinMax Scaler.
* Mendapatkan struktur terbaik pembentukan model dalam prediksi harga saham PT Bank Rakyat Indonesia Tbk menggunakan algoritma Long Short Term Memory (LSTM).
* Mendapatkan tingkat keakurasian model dengan Long Short Term Memmory (LSTM).

## Data Understanding
### Sumber Data
Data yang digunakan pada proyek pertama predictive analytics adalah data harga saham PT Bank Rakyat Indonesia Tbk periode 2 Juli 2018 sampai 28 Juni 2023, yang diperoleh dari Yahoo Finance pada tautan berikut https://finance.yahoo.com/quote/BBRI.JK/ .

Data harga saham PT Bank Rakyat Indonesia Tbk periode 2 Juli 2018 sampai 28 Juni 2023 mempunyai 1239 data, dimana pada setiap tangal perekaman data terdiri dari 7 kolom yaitu Date, Open, High, Low, Close, Adj Close, dan Volume.

### Variabel-variabel pada data harga saham PT Bank Rakyat Indonesia Tbk
| Kolom | Keterangan |
| ----- | ---------- |
| Date | Tanggal pencatatan harga saham |
| Open | Harga pembukaan saham |
| Hight | Harga tertinggi saham |
| Low | Harga terendah saham |
| Close | Harga penutupan saham |
| Adj Close | Harga penutupan yang telah disesuaikan, maksudnya adalah harga saham penutupan yang sudah disesuaikan ketika terjadi aksi korporasi perusahaan, dalam hal ini adalah dividen dan stock split |
| Volume | Jumlah saham yang diperdagangkan dalam suatu periode |

### Overview data harga saham PT Bank Rakyat Indonesia Tbk
Berikut adalah 5 data harga saham PT Bank Rakyat Indonesia Tbk periode 2 Juli 2018 sampai 28 Juni 2023 yang mempunyai total 1239 data. Data dapat dilihat pada tabel berikut:
| Date | Open | High | Low | Close | Adj Close | Volume |
| ---- | ---- | ---- | --- | ----- | --------- | ------ |
| 2018-07-02 | 2890.0 | 2910.0 | 2820.0 | 2850.0 | 2362.062744 | 151334600.0 |
| 2018-07-03 | 2850.0 | 2860.0 | 2770.0 | 2830.0 | 2345.487061 | 88835200.0 |
| 2018-07-04 | 2830.0 | 2950.0 | 2790.0 | 2930.0 | 2428.366211 | 128906900.0 |
| 2018-07-05 | 2890.0 | 2920.0 | 2860.0 | 2910.0 | 2411.790527 | 63494300.0 |
| 2018-07-06 | 2910.0 | 2910.0 | 2840.0 | 2840.0 | 2353.774902 | 76368500.0 |

### Visualisasi data
Berikut adalah harga penutupan saham PT Bank Rakyat Indonesia Tbk periode 2 Juli 2018 sampai 28 Juni 2023. untuk pergerakannya dapat dilihat pada gambar dibawah ini.
![Harga Saham PT Bank Rakyat Indonesia Tbk periode 2 Juli 2018 sampai 28 Juni 2023](https://github.com/rizkialvian/Machine_Learning_Terapan_Proyek_Pertama/blob/9ffa7391a1083edecf291bdd77d1928ddfc9c81a/assets/PT%20Bank%20Rakyat%20Indonesia%20Tbk%20(2%20Jul%202018%20-%2028%20Jun%202023).png?raw=true)
Dari gambar diatas dapat kita lihat bahwa harga saham terkadang naik, terkadang turun. Namun apabila diamati lebih dalam, harga saham menunjukan pola tren naik.

## Data Preparation

## Modeling

## Evaluation

## Daftar Referensi

[1] Undang-Undang RI Nomor 10 Tahun 1998 Perubahan Atas Undang-Undang Nomor 7 Tahun 1992 Tentang Perbankan.

[2] Wang ,Yu, Q , K. Strandhagep, J & Wang Y. (2017). Aplication of Long Short Term Memory Neural Network to sales Forecesting in Retail. A case Study, Internasional Workshop of Advanced Manufacturing and Automation.

[3] Sayudi, MAD., Djamal,EC. Dan Asri Maspupah. (2019). Prediksi Harga Saham Menggunkan Metode Recurrent Neural Network. Maklah disajikan dalam Seminar Nasional Aplikasi Teknologi Inormasi, Yogyakarta. 

[4] Arfan, A dan Lussiana ETP. (2020). Perbandingan Algoritma Long Short Term Memory dengan SVR pada Prediksi Harga Saham di Indonesia. Jurnal Pengkajian dan Penerapan Teknik Informatika.

[5] Alwiyah, Silvie N. (2020). Pemodelan Menggunakan Pendekatan Recurrent Neural Network Long Short Term Memory (RNN-LSTM) pada Harga Emas Dunia. Universitas Muhammadiyah Semarang.
