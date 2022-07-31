# **Laporan Proyek Machine Learning - Abdul Azis**

## **Project Overview**
### **Latar Belakang**
Menurut Mohammad Irfan, Andharini Dwi Cahyani dan Fika Hastarita R (2014) didalam jurnal yang mereka tulis berjudul [Sistem Rekomendasi: Buku Online dengan metode _Collaborative Filtering_](https://ejournal.akprind.ac.id/index.php/technoscientia/article/view/612) menyatakan bahwa buku merupakan informasi segala kebutuhan yang diperlukan, dimulai dari iptek, seni budaya, ekonomi, politik, sosial dan pertahanan keamanan dan lain-lain. Upaya membaca buku membuka wawasan dunia intelek sehingga dapat mengubah masa depan serta mencerdaskan akal, pikiran dan iman.Dengan membaca buku, selain pengetahuan akan semakin bertambah, pribadi akan  semakin kaya, yang kesemuannya jelas akan menurunkan efek negatif terhadap anak-anak, yakni kenakalan. Sedangkan anak yang tidak terbina minat bacanya sejak dini akan menghadapi peluang yang semakin kecil untuk mengembangkan pengetahuan setinggi-tingginya. Namun berdasarkan laporan Bank Dunia, Indonesia merupakan negara yang memiliki minatbaca sangat rendah. Hal tersebut sungguh disayangkan, mengingat sebagai negara besar, Indonesia memiliki potensi besar untuk menjadi negarayang unggul.

Rendahnya minat baca dikalangan masyarakat menjadi persoalan penting didunia pendidikan saat ini. Untuk itu diperlukan sebuah sistem yang dapat membantu merekomendasikan para pembaca agar lebih mudah mendapatkan informasi buku-buku yang akan dibaca selanjutnya. Banyaknya jumlah buku akan membuat pembaca terkadang kesulitan dalam menentukan buku yang hendak mereka baca selanjutnya.Terkadang dijumpai pembaca yang hanya ingin membaca buku-buku yang dengan reputasi penjualan terbaik. Ada pula pembaca yang hanya ingin membaca buku yang mirip dengan buku-buku yang pernah dibaca sebelumnya. Tidak jarang juga ditemui pembaca yang menentukan buku-buku yang akan dibaca selanjutnya berdasarkan rating dari buku-buku yang telah dilihatnya. Semakin tinggi rating dari buku tersebut, semakin tertarik pula pembaca untuk membacanya. Semakin rendah rating dari buku tersebut, maka pembaca cenderung enggan untuk membacanya. Tinggi rendahnya rating tersebut mempengaruhi buku-buku yang akan direkomendasikan. Nilai kemiripan antar buku dan rating buku dapat dijadikan landasan untuk memberikan rekomendasi buku kepada pembaca.

Berdasarkan latar belakang yang telah dijelaskan di atas, topik proyek ini diambil dengan tujuan sebagai domain proyek machine learning yang akan dibuat. Selain itu, proyek ini dibuat untuk dapat melengkapi fitur yang dapat digunakan pada proyek aplikasi yang akan dibuat oleh penulis. Diharapkan sistem rekomendasi ini dapat digunakan pada sebuah aplikasi dan memberikan rekomendasi yang relevan sesuai dengan preferensi pengguna dan dapat meningkatkan kenyamanan pengguna saat menggunakan aplikasi.

## **Business Understanding**
### **Problem Statement**
Berdasarkan pada latar belakang di atas, permasalahan yang dapat diselesaikan pada proyek ini adalah sebagai berikut:
* Bagaimana cara melakukan pengelolahan data sehingga dapat menghasilkan rekomendasi yang baik dan relevan?
* Bagaimana cara membangun sistem untuk merekomendasikan buku yang yang sesuai dengan preferensi pengguna?
### **Goals**
Tujuan dibuatnya proyek ini adalah sebagai berikut:
* Melakukan pengolahan data yang baik agar dapat digunakan dalam membangun sistem rekomendasi yang baik.
* Membangun model machine learning untuk merekomendasikan sebuah buku yang sesuai dengan preferensi pengguna.
### **Solution**
Untuk menyelesaikan masalah ini, penulis akan menggunakan 2 solusi algoritma yaitu content-based filtering dan collaborative filtering. Berikut adalah penjelasan teknik-teknik yang akan digunakan untuk masalah ini:

Content-Based Filtering merupakan cara untuk memberi rekomendasi bedasarkan genre atau fitur pada item yang disukai oleh pengguna. Content-based filtering mempelajari profil minat pengguna baru berdasarkan data dari objek yang telah dinilai pengguna.
Collaborative Filtering merupakan cara untuk memberi rekomendasi bedasarkan penilaian komunitas pengguna atau biasa disebut dengan rating. Collaborative filtering tidak memerlukan atribut untuk setiap itemnya seperti pada sistem berbasis konten.