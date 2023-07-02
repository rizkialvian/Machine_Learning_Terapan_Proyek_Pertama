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
Teknik Data Preparation yang Dilakukan adalah sebagai berikut:
* Memeriksa tipe data, tahapan ini perlu dilakukan untuk memeriksa apakah data merupakan object atau berbentuk kategorikal. Setelah diperiksa ternyata tipe data penutupan saham merupakan data numerik dengan tipe float64, yang berarti skip langkah OHE / Label Encoder.
* memeriksa apakah ada data yang kosong, tahapan ini perlu dilakukan untuk memastikan tidak ada data yang dapat mempengaruhi perolehan hasil model. setelah diperiksa ternyata tidak ada data yang kosong sehingga tahapan ini dapat terlewati.
* Mengambil kolom Close, ini dilakukan karena yang akan digunakan dalam proses prediksi harga adalah data penutupan saham, sehingga yang dipilih adalah kolom Close saja.
* Melakukan MinMaxScaller(), ini merupakan proses scalling dengan mengubah data numeric menjadi data numeric yang memiliki rentang 0 - 1.
* Mengubah data menjadi tipe array.
* Membagi data menjadi data training dan data testing dengan perbandingan 80:20. Dari pembagian ini diperoleh data training sebanyak 992 data.

## Modeling
### Membentuk Model
Pada tahapan ini akan dilakukan pemodelan data menggunakan algoritma Long Short Term Memmory (LSTM) yaitu merupakan pengembangan lebih lanjut dari arsitektur RNN. LSTM diperkenalkan oleh Hochreiter dan Schamidhuber pada tahun 1997 dan muncul karena kurangnya gradien di RNN. Fitur utama jaringan LSTM adalah lapisan tersembunyi, yang terdiri dari sel-sel memori. Setiap sel memori memiliki tiga gerbang atau gate: forgate gate, input gate, dan output gate.

Secara sederhana, cara kerja algoritma LSTM dapat dijabarkan dalam langkah-langkah berikut:
* LSTM memutuskan informasi mana yang akan disimpan dan mana yang akan dihapus dari status sel. Lapisan sigmoid bertanggung jawab atas keputusan ini.
* LSTM memutuskan informasi baru apa yang akan disimpan dan menggantikan informasi yang tidak relevan yang diidentifikasi pada langkah sebelumnya. Fungsi Tanh dan fungsi sigmoid memainkan peran penting dalam mengidentifikasi informasi yang relevan.
* Keluaran yang diperoleh dengan menggunakan status sel adalah versi yang difilter dengan fungsi sigmoid dan tan yang diterapkan.

Adapun langkah-langkah yang penulis lakukan adalah sebagai berikut:
* Pertama-tama penulis menggunakan library keras.models untuk memanggil fungsi Sequential(), pada tahapan ini digunakan untuk menyiapkan basis model LSTM yang disimpan pada variabel model.
* Kemudian penulis menggunakan library keras.layer untuk mengkonfigurasikan layer pada model LSTM, disini kita gunakan konfigurasi 3 layer dengan jumlah neuron 50, 50, dan 25.
* Setelah model selesai dibangun, model akan di-compile dan ditambahkan fungsi optimizer adam, dan loss function yang digunakan adalah mean_square_error (MSE).
* Pada model, dilakukan proses training dengan hyperparameter disetel batch_size = 1 dan epoch = 5.

Berikut adalah hasil yang diperoleh:

![Hasil running model](https://github.com/rizkialvian/Machine_Learning_Terapan_Proyek_Pertama/blob/57347294b818e57ff6cb89dc9234b04edd727a46/assets/Running%20model.PNG?raw=true)

### Melakukan Prediksi
Membuat Variabel X Test, Y Test, dan Fungsi Pembagi Data
* Disini kita akan medefinisikan variabel kosong bernama x_test dan y_test, yang akan diisi oleh pembagian data yang akan dilakukan menggunakan data yang sudah dibagi dan di-scaling sebelumnya.
* Kemudian data akan dibagi menjadi 60 data x_test yang dimulai dari data dengan index 0 hingga 59 (data_testing) dan 1 data y_test (data_testing) yang diambil dari indeks ke 60.
* Data dengan indeks 60 tersebut merupakan target dari prediksi setiap 60 data awal didefinisikan pada fungsi for di baris kode ke 9.
* Pembagian selanjutnya adalah data dengan indeks 1 hingga 60 dan data dengan indeks 61, dan begitu seterusnya.

Proses Prediksi
* Input dari model LSTM mengaruskan untuk array 3 dimensi berupa (number of samples, number of time steps, number of features).
* Data yang dimiliki masih berbentuk 2 dimensi, jadi harus dilakukan reshaping kemudian data akan dilakukan prediksi. Setelah hasil prediksi didapatkan akan diterapkan fungsi inverse untuk membalikkan harga seperti semula.

### Visualisasi Hasil
Berikut adalah visualisasi dari hasil prediksi yang dilakukan menggunakan algoritma LSTM.

![Visuaisasi Hasil](https://github.com/rizkialvian/Machine_Learning_Terapan_Proyek_Pertama/blob/690eeea4581f1b1976dee708873a9e91f978c9c8/assets/Visualisasi%20Hasil.png?raw=true)

## Evaluation
Model yang digunakan adalah model regressi, metric yang digunakan untuk evaluasi disini adalah Mean Squared Error (MSE), yaitu rata-rata Kesalahan kuadrat diantara nilai aktual dan nilai prediksi. Metode Mean Squared Error secara umum digunakan untuk mengecek estimasi berapa nilai kesalahan pada prediksi. Nilai Mean Squared Error yang rendah atau nilai mean squared error mendekati nol menunjukkan bahwa hasil prediksi sesuai dengan data aktual dan bisa dijadikan untuk perhitungan prediksi di periode mendatang. Metode Mean Squared Error biasanya digunakan untuk mengevaluasi metode pengukuran dengan model regressi.

Kelebihan MSE yaitu sederhana dalam perhitungan. Sedangkan kelemahan yang dimiliki MSE adalah akurasi hasil prediksi sangat kecil karena tidak memperhatikan apakah hasil prediksi lebih besar atau lebih kecil dibandingkan kenyataannya

![MSE](https://github.com/rizkialvian/Machine_Learning_Terapan_Proyek_Pertama/blob/4d424e9d3abe57d591b244cc581cd911c826433a/assets/MSE.PNG?raw=true)

Keterangan:
* n = Jumlah Data
* yi = Actual Value / Nilai Sebenarnya
* ŷi = Predicted Value / Nilai Prediksi

Dari hasil pengolahan data yang sudah dilakukan, hasil MSE yang diperloleh sangat kecil, sehingga nilai yang keluar adalah NaN.

## Daftar Referensi

[1] [Undang-Undang RI Nomor 10 Tahun 1998 Perubahan Atas Undang-Undang Nomor 7 Tahun 1992 Tentang Perbankan.](https://www.dpr.go.id/jdih/index/id/468)

[2] [Yu, Q., Wang, K., Strandhagen, J. O., & Wang, Y. (2018). Application of long short-term memory neural network to sales forecasting in retail—a case study. In Advanced Manufacturing and Automation VII 7 (pp. 11-17). Springer Singapore.](https://link.springer.com/chapter/10.1007/978-981-10-5768-7_2)

[3] [Suyudi, M. A. D., Djamal, E. C., & Maspupah, A. (2019, August). Prediksi Harga Saham menggunakan Metode Recurrent Neural Network. In Seminar Nasional Aplikasi Teknologi Informasi (SNATI).](https://journal.uii.ac.id/Snati/article/download/13398/9494)

[4] [Arfan, A., & Lussiana, E. T. P. (2020). Perbandingan algoritma long short-term memory dengan SVR pada prediksi harga saham di Indonesia.](http://jurnal.itpln.ac.id/petir/article/view/858)

[5] [ALAWIYAH, S. N. (2021). PEMODELAN MENGGUNAKAN PENDEKATAN RECURRENT NEURAL NETWORK LONG SHORT TERM MEMORY (RNNLSTM) PADA HARGA EMAS DUNIA (Doctoral dissertation, Muhammadiyah University, Semarang).](http://repository.unimus.ac.id/id/eprint/4855)
