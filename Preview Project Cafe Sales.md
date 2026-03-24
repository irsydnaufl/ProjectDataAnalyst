# Project Cafe Sales

## Dataset
Dataset ini memuat 10.000 baris data penjualan yang merepresentasikan transaksi harian di sebuah kafe. Data ini sengaja dirancang dalam kondisi "kotor" (dirty data) untuk memberikan skenario dunia nyata dalam melatih kemampuan pembersihan data (data cleaning) dan analisis data eksploratif (Exploratory Data Analysis atau EDA).

Dataset diambil dari <a href="https://www.kaggle.com/datasets/ahmedmohamed2003/cafe-sales-dirty-data-for-cleaning-training">Kaggle</a> yang bersifat open source. Dataset mengandung 10.000 transaksi dan 8 feature(kolom), yaitu:
1. **Transaction ID**, nomer ID unik untuk setiap transaksi penjualan.
2. **Item**, nama menu yang dipesan.
3. **Quantity**, jumlah item/produk yang dibeli.
4. **Price Per Unit**, harga satuan per item.
5. **Total Spent**, total biaya konsumen pada satu transaksi.
6. **Payment Method**, metode pembayaran.
7. **Location**, jenis layanan tempat pemesanan.
8. **Transaction Date**, tanggal transaksi dilakukan.

### Karakteristik Dataset
Dataset yang ada masih membutuhkan pengolahan lebih lanjut seperti data cleaning dari beberapa kasus seperti:
1. **Missing Values**, beberapa kolom memiliki missing values yang ditampilkan seperti "nan" atau sel kosong.
2. **Invalid Values**, beberapa kolom berisi data yang tidak valid seperti "UNKNWON" dan "ERROR".
3. **Type Data**, beberapa kolom memiliki type data yang tidak sesuai.
Dari beberapa karakteristik di atas perlu pengolahan lebih lanjut pada tahap 'Data Cleaning & Missing Values' untuk mengisi missing values, mengganti invalid values dan mengubah type data.

## Business Analyst
### Objektif
Analisis terhadap data penjualan dari Cafe ini bertujuan untuk bisa membantu menemukan strategi pemasaran di masa depan hingga meningkatkan penjualan secara optimal.
Dari data yang ada didapatkan beberapa pertanyaan bisnis yang diantaranya:
1. Bagaimana trend penjualan setiap bulannya sepanjang tahun 2023?
2. Bagaimana tren volume item sales yang berhasil terjual dalam kurun waktu setahun dan apakah lonjakannya sejalan dengan grafik pendapatan?
3. Berapa profit dari masing-masing Item?
4. Kuantitas Item mana yang paling laku terjual di antara semua item menu di Cafe?
5. Mengapa persentase data 'Unknown' pada metode pembayaran dan lokasi mencapai lebih dari 30%?

### Goals
Berdasarkan objektif analisis yang telah disebutkan, berikut goals/tujuan yang diharapkan:
1. Memetakan fluktuasi naik-turunnya performa omzet tahunan, serta untuk menemukan bulan-bulan sibuk (peak seasons) dan low seasons untuk mengidentifikasi pola penjualan sepanjang waktu.
2. Membandingkan keterkaitan antara jumlah unit keluar dengan pergerakan grafik pendapatan bersih sehingga dapat menilai apakah arus kafe lebih bertumpu pada volume transaksi massal bernilai murah atau transaksi rendah yang bernilai tinggi.
3. Mengukur pendapatan bersih dari masing-masing Item guna memanfaatkan tingginya margin Item tinggi untuk menggerakkan produk lainnya, seperti Item bundling.
4. Mengenali produk dengan tingginya volume penjualan serta mengevaluasi produk/item dengan kuantitas paling sedikit, untuk pertimbangan lebih lanjut.
5. Melakukan pembaruan sistem untuk mandatory fields sehingga data berlabel yang tidak sesuai tidak terjadi kembali sehingga keputusan bisnis ke depannya tidak bias.

## Exploratory Data Analysis (EDA)
Proses EDA menggunakan <a href="https://github.com/irsydnaufl/ProjectCafeSales/blob/main/Pyhton/CoffeAnalyst.ipynb">**Python di JupyterLab**</a> dengan memuat dataset menggunakan pustaka Pandas untuk membedah struktur dan distribusi data awal. Untuk membersihkan dataset, langkah yang perlu dilakukan yaitu:
1. **Remove Duplicate** untuk mengeliminasi baris ganda yang berpotensi mendistorsi hasil agregasi.
2. **Data Cleaning**, untuk mengidentifikasi dan menangani nilai kosong (missing values) agar kalkulasi statistik tidak bias.
3. **Change Data Type**, perlu penyesuaian type data agar feature sesuai dengan data yang ada, misalnya mengubah tipe data teks (string) pada kolom tanggal menjadi format datetime atau merapikan angka numerik.
4. **Make New Feature** , untuk menggali insight bisnis yang lebih tajam dilakukan rekayasa fitur (feature engineering) seperti menghitung margin keuntungan atau memetakan total pengeluaran yang mempermudah visualisasi tren performa secara menyeluruh.

## Visualization
Setelah proses Data Cleaning kemudian data disimpan dalam format <a href="https://github.com/irsydnaufl/ProjectCafeSales/blob/main/csv/Clean_Cafe_Sales.csv">CSV</a> menjadi sebuah dataset yang bersih, tahapan analisis bergeser menjadi **visualisasi menggunakan Power BI** untuk mengkomunikasikan insight secara efektif. File CSV yang sudah bersih diimpor ke dalam Power BI untuk ditransformasikan menjadi **Dashbor interaktif** yang berisi visualisasi grafis, tren, dan metrik performa. Pada fase ini, fokus utama bukan lagi mencari missing values dan data cleaning, melainkan merangkai narasi data (storytelling) dan menyajikan kesimpulan visual yang intuitif guna mendukung pengambilan keputusan bisnis yang cepat serta akurat.

![Uploading Page 1.jpg…](https://github.com/irsydnaufl/ProjectCafeSales/blob/main/Power%20BI/Page%201.jpg)
Halaman pertama menunjukkan total net revenue sebesar $49.51K dengan kontribusi terbesar berasal dari produk seperti salad, sandwich, dan smoothie. Kategori “Main Dish” dan “Food” mendominasi pendapatan, sementara tren revenue bulanan relatif stabil di kisaran $3.8K–$4.4K, dengan puncak pada Oktober dan penurunan di bulan Februari.

![Uploading Page 2.jpg…](https://github.com/irsydnaufl/ProjectCafeSales/blob/main/Power%20BI/Page%202.jpg)
Halaman kedua menampilkan total penjualan 25.93K item dengan tren bulanan yang konsisten pada pertengahan tahun(±2.0K–2.3K). Produk terlaris adalah coffee, juice, dan salad, sementara metode pembayaran dan lokasi transaksi menunjukkan distribusi yang cukup seimbang, meskipun masih terdapat data “unknown” yang perlu diperbaiki.
