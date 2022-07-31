# **Laporan Proyek Machine Learning - Abdul Azis**

## **Project Overview**
### **Latar Belakang**
Menurut Mohammad Irfan, Andharini Dwi Cahyani dan Fika Hastarita R (2014) didalam jurnal yang mereka tulis berjudul [Sistem Rekomendasi: Buku Online dengan metode Collaborative Filtering](https://ejournal.akprind.ac.id/index.php/technoscientia/article/view/612) menyatakan bahwa buku merupakan informasi segala kebutuhan yang diperlukan, dimulai dari iptek, seni budaya, ekonomi, politik, sosial dan pertahanan keamanan dan lain-lain. Upaya membaca buku membuka wawasan dunia intelek sehingga dapat mengubah masa depan serta mencerdaskan akal, pikiran dan iman.Dengan membaca buku, selain pengetahuan akan semakin bertambah, pribadi akan  semakin kaya, yang kesemuannya jelas akan menurunkan efek negatif terhadap anak-anak, yakni kenakalan. Sedangkan anak yang tidak terbina minat bacanya sejak dini akan menghadapi peluang yang semakin kecil untuk mengembangkan pengetahuan setinggi-tingginya. Namun berdasarkan laporan Bank Dunia, Indonesia merupakan negara yang memiliki minatbaca sangat rendah. Hal tersebut sungguh disayangkan, mengingat sebagai negara besar, Indonesia memiliki potensi besar untuk menjadi negarayang unggul.

Rendahnya minat baca dikalangan masyarakat menjadi persoalan penting didunia pendidikan saat ini. Untuk itu diperlukan sebuah sistem yang dapat membantu merekomendasikan para pembaca agar lebih mudah mendapatkan informasi buku-buku yang akan dibaca selanjutnya. Banyaknya jumlah buku akan membuat pembaca terkadang kesulitan dalam menentukan buku yang hendak mereka baca selanjutnya.Terkadang dijumpai pembaca yang hanya ingin membaca buku-buku yang dengan reputasi penjualan terbaik. Ada pula pembaca yang hanya ingin membaca buku yang mirip dengan buku-buku yang pernah dibaca sebelumnya. Tidak jarang juga ditemui pembaca yang menentukan buku-buku yang akan dibaca selanjutnya berdasarkan rating dari buku-buku yang telah dilihatnya. Semakin tinggi rating dari buku tersebut, semakin tertarik pula pembaca untuk membacanya. Semakin rendah rating dari buku tersebut, maka pembaca cenderung enggan untuk membacanya. Tinggi rendahnya rating tersebut mempengaruhi buku-buku yang akan direkomendasikan. Nilai kemiripan antar buku dan rating buku dapat dijadikan landasan untuk memberikan rekomendasi buku kepada pembaca.

Berdasarkan latar belakang yang telah dijelaskan di atas, topik proyek ini diambil dengan tujuan sebagai domain proyek machine learning yang akan dibuat. Selain itu, proyek ini dibuat untuk dapat melengkapi fitur yang dapat digunakan pada proyek aplikasi yang akan dibuat oleh penulis. Diharapkan sistem rekomendasi ini dapat digunakan pada sebuah aplikasi dan memberikan rekomendasi yang relevan sesuai dengan preferensi pengguna dan dapat meningkatkan kenyamanan pengguna saat menggunakan aplikasi.

## **Business Understanding**
### **Problem Statement**
Berdasarkan pada latar belakang di atas, permasalahan yang dapat diselesaikan pada proyek ini adalah sebagai berikut:

* Bagaimana cara melakukan pengelolahan data sehingga dapat menghasilkan rekomendasi yang baik dan relevan?
* Bagaimana cara membangun sistem untuk merekomendasikan buku yang yang sesuai dengan preferensi pengguna?
### **Goals**
Tujuan dibuatnya proyek ini adalah sebagai berikut:

* Dapat Melakukan pengolahan data yang baik agar dapat digunakan dalam membangun sistem rekomendasi yang baik.
* Membangun model machine learning untuk merekomendasikan sebuah buku yang sesuai dengan preferensi pengguna.
### **Solution Approach**
Solusi yang dapat diterapkan agar goals diatas terpenuhi adalah sebagai berikut:

* Melakukan analisa pada data untuk dapat memahami data yang ada seperti: Memeriksa missing value dan duplikasi data.
* Melakukan pemrosesan pada data seperti Normalisasi data rating.
* Membangung sistem rekomendasi menggunakan 2 teknik yang umum digunakan yaitu: Content-Based Filtering dan Collaborative Filtering. 

## **Data Understanding**
Dataset yang di gunakan pada proyek machine learning ini merupakan dataset buku lengkap dengan rating, pengarang dan penerbit-nya. Dataset tersebut dapat di unduh di website kaggle: [Book Recommendation Dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset).

Terdapat 3 file pada dataset, antara lain:
* Books.csv
* Ratings.csv
* Users.csv

Pada proyek ini hanya menggunakan 2 file data, yaitu:
* Books.csv</br>
    File ini memiliki total jumlah 271360 data buku dan dan memiliki 8 kolom variabel data. Berikut penjelasan untuk masing-masing variabel:</br>
    * `ISBN`: Kode pengidentifikasian buku yang bersifat unik.
    * `Book-Title`: Judul Buku.
    * `Book-Author`: Nama pengarang buku.
    * `Year-Of-Publication`: Tahun penerbitan buku.
    * `Publisher`: Pihak penerbit buku.
    * `Image-URL-S`: URL yang menautkan ke gambar sampul berukuran kecil.
    * `Image-URL-M`: URL yang menautkan ke gambar sampul berukuran normal.
    * `Image-URL-L`: URL yang menautkan ke gambar sampul berukuran besar.

* Ratings.csv</br>
    File ini memiliki total jumlah 1149780 data rating dan dan memiliki 3 kolom variabel data. Berikut penjelasan untuk masing-masing variabel:</br>
    * `User-ID`: Nomer unik user yang memberikan rating.
    * `ISBN`: Kode pengidentifikasian buku yang bersifat unik.
    * `Book-Rating`: Skor dari rating yang diberikan.

Untuk dapat lebih memahami data perlu dilakukan eksplorasi pada data, eksplorasi yang di lakukan antara lain: 

* Memeriksa informasi pada data</br>
    * Books</br>
    <image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/info_books.png' width=70% /></br>
    Berdasarkan output di atas, dapat diketahui bahwa file Books.csv memiliki 271360 entri. Kemudian, semua kolom data memiliki type data object, sedangkan untuk kolom data `Year-Of-Publication` memiliki tipe data object yang mana seharusnya data tersebut memiliki tipe data number, tetapi hal ini tidak menjadi masalah sebab data ini tidak diperlukan untuk membuat sistem rekomendasi.</br>
    <image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/book_count.png' width=70% /></br>
    <image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/authors_count.png' width=70% /></br>
    Kemudian terdapat jumlah 242135 buku dan 102023 author (pengarang) pada data.
    
    * Ratings</br>
    <image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/info_ratings.png' width=70% /></br>
    Untuk data ratings, memiliki 1149780 entri dan terdapat 2 tipe pada data yaitu number (int64) dan object.
    <image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/ratings_count.png' width=70% /></br>
    dapat dilihat pada gambar di atas, nilai maksimum rating adalah 10 dan nilai minimumnya adalah 0. Artinya, skala rating berkisar antara 0 hingga 10. Lalu mayoritas buku memiliki rating=0 yaitu sebanyak 716109 buku.

* Memeriksa Missing Value</br>
    <image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/books_missing_value.png' width=70% /></br>
    <image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/ratings_missing_value.png' width=70% /></br>
    Jika dilihat dari output di atas. Terdapat sedikit missing value pada data buku, sedangkan pada data rating tidak memiliki missing value.

* Memeriksa duplikasi data</br>
    <image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/book_duplicates.png' width=70% /></br>
    Dapat dilihat pada output diatas. Tidak terdapat duplikat pada data `ISBN` tetapi terdapat banyak duplikat pada kolom data lainnya. Ini tidak wajar sebab `ISBN` merupakan identitas unik untuk masing-masing judul buku yang seharusnya jika `ISBN` tidak memiliki duplikat maka begitupun untuk data `Book-Title`.</br>
    <image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/rating_duplicates.png' width=70% /></br>
    Begitupun pada data rating, terdapat banyak duplikat pada data. Tetapi ini hal yang wajar sebab tiap user dapat memberikan rating pada tiap buku yang berbeda dan buku yang berbeda dapat menerima rating dari user yang berbeda pula.

## **Data Preparation**
Data preparation diperlukan untuk mempersiapkan data agar ketika dilakukan proses pengembangan model atau sistem dapat menghasilkan rekomendasi dengan baik. Berikut ini merupakan tahapan-tahapan dalam melakukan persiapan data:

* Menghapus data yang tidak diperlukan</br>
Sistem rekomendasi ini hanya memerlukan data author dan rating sebagai fitur untuk model. Beberapa kolom data seperti `'Year-Of-Publication', 'Publisher', 'Image-URL-M', 'Image-URL-L'` tidak akan digunakan untuk sistem rekomendasi ini. Jadi data tersebut bisa dihapus.

* Melakukan penggabungan data</br>
Menggabungkan data buku dan rating menjadi satu sehingga data akan lebih mudah digunakan untuk pelatihan nantinya.

* Menghapus duplikasi data</br>
Penghapusan duplikasi daya yang dilakukan pada proyek ini yaitu penghapusan data yang memiliki judul buku yang sama tetapi memiliki `ISBN` yang berbeda. Sehingga 1 judul buku hanya akan memiliki 1 `ISBN` yang mana akan mempermudah dalam proses mendapatkan rekomendasi.

* Menangani Missing Value<br/>
Salah satu cara untuk menangani missing value pada data yaitu dengan melakukan drop baris data yang memiliki value kosong. Sebab adanya missing value pada data dapat memperburuk performa pelatihan pada model.

* Menyeleksi data</br>
Penyeleksian data pada proyek ini yaitu dengan hanya mengambil data buku dengan total jumlah skor rating pada masing-masing buku di atas 50. Karena sistem rekomendasi ini hanya merekomendasikan buku dengan rating yang tinggi.

* Melakukan normalisasi data rating</br>
Melakukan transformasi pada data fitur fitur yang akan dipelajari oleh model menggunakan library MinMaxScaler. MinMaxScaler mentransformasikan fitur dengan menskalakan setiap fitur ke rentang tertentu. Library ini menskalakan dan mentransformasikan setiap fitur secara individual sehingga berada dalam rentang yang diberikan pada set pelatihan, pada library ini memiliki range default antara 0 dan 1. Dengan merenapkan teknik normalisasi data, model akan dengan lebih mudah mengenali pola-pola yang terdapat pada data sehingga akan menghasilkan keluaran sesuai dengan yang diharapkan.

* Split dataset</br>
Membagi dataset menjadi data latih (train) dan data uji (test) merupakan hal yang harus kita lakukan sebelum membuat model.Data latih adalah sekumpulan data yang akan digunakan oleh model untuk melakukan pelatihan. Sedangkan, data uji adalah sekumpulan data yang akan digunakan untuk memvalidasi kinerja pada model yang telah dilatih. Karena data uji berperan sebagai data baru yang belum pernah dilihat oleh model, maka cara ini efektif untuk memeriksa performa model setelah proses pelatihan dilakukan. Proporsi pembagian dataset pada proyek ini menggunakan proporsi pembagian 90:10 yang berarti sebanyak 90% merupakan data latih dan 10% persen merupakan data uji.

## **Modelling**
Pembuatan sistem rekomendasi pada proyek ini menggunakan teknik Content-Based Filtering dan Collaborative Filtering. Untuk Content-Based Filtering menggunakan metode Cosine Similarity, sedangkan Collaborative Filtering menggunakan metode model based yaitu model Deep Learning. Berikut merupakan penjelasan dari tiap tahapan proses modelling:

### **Content-Based Filtering**
Pada metode ini pertama yang dilakukan yaitu melakukan feature engineering menggunakan library TfidfVectorizer dari library scikit-learn. Proses yang dilakukan menggunakan library TfidfVectorizer adalah tokenisasi fitur `Book-Author` sebab fitur tersebut yang akan menjadi acuan utama sistem rekomendasi menggunakan teknik ini. Output yang dihasilkan oleh library tersebut adalah matrix categorical. Kemudian, setelah itu dilakukan penghitungan derajat kesetaraan (similarity degree) antar buku menggunakan Cosine Similarity. Berikut merupakan formula untuk metode Cosine Similarity:

<image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/cs_formula.png' width=70% />

Kemudian, untuk mendapatkan top-N recommendation harus mengambil nilai k tertinggi. Pada proyek ini menggunakan fungsi argpartition dari library numpy untuk mendapatkan top k tertinggi pada similarity data. Lalu setelah itu sistem dapat menampilkan buku yang direkomendasikan berdasarkan author yang sama dari buku yang telah dibaca sebelumnya. Teknik Content-Based Filtering ini juga memiliki kelebihan dan kekurangan-nya.

* Kelebihan:</br>
    * Semakin banyak informasi yang diberikan pengguna, semakin baik akurasi sistem rekomendasi.
    Kekurangan

* Kekurangan:</br>
    * Hanya dapat digunakan untuk fitur yang sesuai, seperti film, dan buku.
    * Tidak mampu menentukan profil dari user baru.

Berikut merupakan judul konten yang akan dijadikan acuan untuk menentukan top 10 rekomendasi buku yang memiliki author yang sama:</br>

<image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/content_acuan.png' width=70% />

Dapat terlihat sistem rekomendasi dengan teknik Content-Based Filtering menghasilkan rekomendasi yang cukup bagus yaitu dengan menampilkan 6 buku dengan author yang sama dengan buku `First Test (Protector of the Small)`

<image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/content_based_result.png' width=70% />

### **Collaborative Filtering**
Pada teknik ini proses pembuatan rekomendasi menggunakan model Deep Learning. Langkah yang pertama yaitu dengan menggabungkan data buku dan rating. Setelah itu melakukan penyandian terhadap data `User-ID` dan `ISBN` dan memisahkan data latih dan data validasi dengan ratio 80:20. Kemudian membuat model untuk melakukan pelatihan pada data. Model ini menggunakan operasi perkalian dot product antara embedding user dan book. Skor kecocokan ditetapkan dalam skala [0,1] dengan fungsi aktivasi sigmoid. Untuk mendapatkan hasil rekomendasi, dipilih `User-ID` secara acak dan akan dilakukan penyaringan daftar buku yang belum pernah dibaca oleh user. Tentunya teknik ini memiliki kelebihan dan kekurangannya sendiri, yaitu: 
* Kelebihan
    * Tidak memerlukan atribut untuk setiap itemnya.
    * Dapat membuat rekomendasi tanpa harus selalu menggunakan dataset yang lengkap.
    * Unggul dari segi kecepatan dan skalabilitas.
    * Rekomendasi tetap akan berkerja dalam keadaan dimana konten sulit dianalisi sekalipun.

* Kekurangan
    * Membutuhkan parameter rating, sehingga jika ada item baru sistem tidak akan merekomendasikan item tersebut.

Berikut merupakan hasil rekomendasi buku kepada user dengan ID: 241204</br>

<image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/collaborative_result.png' width=70% />

## **Evaluation**
Evaluasi yang akan dilakukan diproyek ini yaitu evaluasi dengan Precision Content untuk Content-Based Filtering dan Root Mean Squared Error (RMSE) untuk Collaborative Filtering.

### **Content-Based Filtering**
Evaluasi pada teknik ini menggunakan metrik precision content untuk menghitung tingkat presisi sistem dari rekomendasi yang dibuat. Berikut hasilnya:

Formula metrik Precision:</br>
<image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/precision_metric.png' width=70% /></br>

Hasil metric Presision:</br>
<image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/content_acuan.png' width=70% />
<image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/content_based_result.png' width=70% /><Br>

Untuk menentukan hasil dari metrik precision adalah dengan melakukan analisa pada buku yang akan dijadikan sebagai acuan. Dapat dilihat dari gambar di atas bahwa buku yang akan dijadikan sebagai acuan memiliki author dengan nama `Tamora Pierce`. Lalu dari hasil 10 rekomendasi buku yang diberikan oleh sistem terdapat 6 buku dengan nama author `Tamora Pierce`. Jadi dapat disimpulkan bahwa tingkat presisi pada sistem ini yaitu 6/10 atau sebesar 60%. Hasil didapatkan seperti ini dikarenakan buku dengan author `Tamora Pierce` yang terdapat di dalam data hanya berjumlah 6.

### **Collaborative Filtering**
Metrik evaluasi yang digunakan untuk mengukur performa dari model ini yaitu dengan menggunakan metrik Root Mean Squared Error (RMSE). Cara Menghitung Root Mean Square Error (RMSE) adalah dengan mengurangi nilai aktual dengan nilai peramalan kemudian dikuadratkan dan dijumlahkan keseluruhan hasilnya kemudian dibagi dengan banyaknya data. Hasil perhitungan tersebut selanjutnya dihitung kembali untuk mencari nilai dari akar kuadrat. Semakin rendah nilai root mean square error juga menandakan semakin baik model tersebut dalam melakukan prediksi.</br>

<image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/rmse_formula.png' width=70% /></br>

<image src='https://raw.githubusercontent.com/ziszz/book-recommendation/master/visualizations/collaborative_metrics.png' width=70% /></br>

Dari hasil pelatihan yang dilakukan. Dapat dilihat bahwa nilai konvergen metrik RMSE berada di sekitar 0.28 untuk training dan disekitar 0.35 untuk validasi.

## **Conslusion**
Dari hasil pembuatan proyek sistem rekomendasi buku diatas. Dapat disimpulkan bahwa model memiliki performa yang sangat baik dalam memberikan rekomendasi baik pada model yang menggunakan teknik Content-Based Filtering maupun Collaborative Filtering. Hal ini didukung dengan hasil rekomendasi yang diberikan dari kedua model memberikan hasil rekomendasi yang cukup relevan dengan preferensi pengguna.

## **Reference**
Irfan, M., Cahyani, A. D., & R, F. H. (2014). SISTEM REKOMENDASI: BUKU ONLINE DENGAN METODE COLLABORATIVE FILTERING. JURNAL TEKNOLOGI TECHNOSCIENTIA, 7(1), 076–84.
