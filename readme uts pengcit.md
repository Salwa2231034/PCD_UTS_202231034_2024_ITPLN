
# A. Tahapan Cara menyelesaikan proyek

1. Deteksi warna pada citra
Deteksi warna pada citra melibatkan identifikasi area di dalam citra yang memiliki warna tertentu sesuai dengan rentang warna yang ditentukan. Dalam kode yang diberikan, terdapat beberapa langkah untuk melakukan deteksi warna, dimulai dengan pembacaan citra menggunakan fungsi img.imread(). Setelah citra dibaca, langkah pertama dalam proses deteksi warna adalah memvisualisasikan gambar asli menggunakan plt.imshow(). Ini memungkinkan pengguna untuk melihat citra secara keseluruhan dan memahami konten visualnya sebelum melakukan deteksi warna.

Setelah itu, citra dibagi menjadi saluran warna Merah (R), Hijau (G), dan Biru (B) menggunakan slicing array NumPy. Ini memungkinkan kita untuk melihat kontribusi masing-masing saluran warna terhadap citra secara terpisah. Selanjutnya, histogram untuk gambar asli dan ketiga saluran warna ditampilkan menggunakan plt.hist(). Histogram memberikan pemahaman tentang distribusi intensitas piksel dalam citra, sehingga kita dapat melihat sebaran warna dalam citra dan setiap saluran warna.

Setelah memahami distribusi warna dalam citra, langkah selanjutnya adalah melakukan konversi citra ke ruang warna HSV (Hue, Saturation, Value). Ini dilakukan karena ruang warna HSV lebih sesuai untuk deteksi warna daripada ruang warna RGB. Kemudian, masker warna dibuat dalam ruang warna HSV menggunakan cv2.inRange() dengan menentukan rentang warna yang diinginkan untuk setiap warna yang akan dideteksi.

Hasil deteksi warna kemudian ditampilkan dalam bentuk masker, di mana area yang sesuai dengan rentang warna yang ditentukan dipertahankan, sementara area lainnya dihapus. Ini memungkinkan kita untuk melihat dengan jelas area yang telah terdeteksi sebagai warna yang diinginkan dalam citra. Selanjutnya, hasil deteksi warna untuk setiap saluran warna diekstraksi secara terpisah dan ditampilkan untuk memungkinkan analisis lebih lanjut tentang efektivitas deteksi warna.

Selain itu, hasil deteksi warna untuk setiap saluran warna digabungkan menggunakan operasi bitwise OR untuk menghasilkan masker gabungan. Masker gabungan ini kemudian diterapkan pada citra asli untuk menghasilkan gambar dengan area yang sesuai dengan semua rentang warna yang ditentukan. Ini memungkinkan kita untuk melihat area yang terdeteksi sebagai warna biru, merah, dan hijau secara bersamaan dalam satu gambar. Dengan demikian, deteksi warna pada citra memungkinkan kita untuk mengidentifikasi dan mengekstraksi area berdasarkan warna yang diinginkan dalam citra dengan presisi yang tinggi.

2. Membuat HistogramHistogram adalah representasi visual dari distribusi intensitas piksel dalam sebuah gambar. Dalam konteks deteksi warna pada citra, histogram digunakan untuk memberikan pemahaman tentang sebaran intensitas warna dalam citra tersebut. Pada kode yang diberikan, histogram digunakan untuk mengevaluasi distribusi intensitas piksel dalam gambar asli dan masing-masing saluran warna (Merah, Hijau, Biru). Setiap saluran warna memiliki histogramnya sendiri yang menunjukkan sebaran intensitas warna dalam saluran warna tersebut.

Dalam histogram gambar asli, distribusi intensitas piksel dari seluruh saluran warna dievaluasi. Ini memberikan pemahaman tentang sebaran warna secara keseluruhan dalam citra. Histogram ini dapat digunakan untuk mendeteksi keberadaan bias warna atau kecenderungan warna tertentu dalam citra. Analisis histogram gambar asli dapat mengungkapkan informasi tentang komposisi warna dominan dalam citra, serta kontras dan kecerahan keseluruhan citra.

Selanjutnya, histogram untuk masing-masing saluran warna dievaluasi secara terpisah. Histogram Merah, Hijau, dan Biru menunjukkan sebaran intensitas piksel untuk masing-masing saluran warna. Analisis histogram saluran warna ini memungkinkan untuk mengetahui kontribusi setiap saluran warna terhadap warna keseluruhan dalam citra. Misalnya, jika histogram saluran Merah menunjukkan puncak intensitas pada nilai tertentu, itu menunjukkan dominasi warna merah dalam citra.

Distribusi intensitas piksel dalam histogram juga dapat mengungkapkan informasi tentang kontras gambar. Jarak antara puncak-puncak dan lembah dalam histogram mencerminkan kontras antara berbagai tingkat intensitas piksel dalam citra. Histogram yang lebih lebar menunjukkan gambar dengan kontras yang lebih tinggi, sementara histogram yang lebih sempit menunjukkan gambar dengan kontras yang lebih rendah. Analisis ini dapat membantu dalam mengevaluasi kejelasan dan detail citra.

Selain itu, melalui histogram, kita juga dapat melihat distribusi intensitas piksel yang terkandung dalam rentang nilai intensitas tertentu. Ini berguna untuk menilai kisaran intensitas yang dominan dalam citra. Misalnya, jika histogram memiliki puncak yang tinggi pada nilai intensitas tertentu, itu menunjukkan keberadaan area dalam citra dengan intensitas yang kuat dalam rentang tersebut. Analisis terperinci tentang histogram memungkinkan kita untuk mendapatkan wawasan yang mendalam tentang karakteristik warna dan kontras dalam citra.

3. Mencari dan mengurutkan ambang batas terkecil sampai dengan terbesar. 
Mencari dan mengurutkan ambang batas pada gambar dilakukan dalam konteks deteksi warna, terutama saat menggunakan ruang warna HSV. Dalam kode yang diberikan, terdapat definisi rentang warna untuk setiap saluran warna yang ingin dideteksi. Misalnya, untuk deteksi warna biru, rentang warna biru dalam ruang warna HSV ditentukan oleh nilai-nilai ambang batas untuk Hue, Saturation, dan Value (nilai Hue, Saturation, dan Value adalah representasi warna, kejenuhan, dan kecerahan).

Pada kode yang diberikan, rentang warna ditentukan secara empiris berdasarkan pengetahuan tentang representasi warna dalam ruang warna HSV dan pengamatan visual dari citra. Ambang batas terkecil dan terbesar untuk setiap saluran warna ditentukan berdasarkan nilai-nilai yang mencakup variasi warna yang ingin dideteksi. Misalnya, ambang batas terkecil untuk Saluran Hue mungkin mencakup nilai-nilai yang mewakili warna biru, sedangkan ambang batas terbesar mungkin mencakup variasi warna biru yang lebih luas.

Nilai-nilai ambang batas kemudian diuji dan disesuaikan empiris untuk mencapai hasil yang diinginkan dalam deteksi warna. Ini melibatkan serangkaian percobaan dan iterasi untuk menemukan nilai-nilai yang paling cocok dengan citra yang dianalisis. Proses ini memerlukan pengujian dan penyesuaian berulang terhadap rentang warna yang ditentukan hingga diperoleh hasil yang memuaskan dalam deteksi warna.

Alasan mendapatkan nilai ambang batas tertentu adalah untuk memastikan deteksi warna dilakukan dengan presisi yang tinggi, yaitu hanya menangkap area yang benar-benar sesuai dengan warna yang diinginkan tanpa termasuk area yang tidak relevan. Oleh karena itu, nilai-nilai ambang batas ditentukan agar mencakup variasi warna yang diinginkan dalam citra, sementara meminimalkan kemungkinan terdeteksinya warna yang tidak relevan.

Selain itu, dalam menentukan nilai ambang batas, perhatian khusus diberikan pada aspek kecerahan dan kejenuhan warna. Ini karena ambang batas yang tidak tepat dalam Saluran Value dan Saturation dapat menghasilkan deteksi yang kurang akurat atau tidak konsisten terhadap variasi kondisi pencahayaan atau kejenuhan warna dalam citra.

Proses penentuan nilai ambang batas membutuhkan pemahaman yang mendalam tentang karakteristik warna dalam citra dan cara mereka direpresentasikan dalam ruang warna HSV. Selain itu, ini juga memerlukan keterampilan interpretasi visual untuk memastikan bahwa nilai-nilai ambang batas yang dipilih mencakup variasi warna yang diinginkan dalam citra secara tepat. Dengan demikian, penentuan nilai ambang batas adalah langkah kunci dalam proses deteksi warna yang akurat dan andal.
Ambang Batas Warna Biru:

Ambang Bawah: Nilai HSV [100, 50, 50]
Ambang Atas: Nilai HSV [130, 255, 255]
Ambang batas ini mengidentifikasi rentang nilai Hue, Saturation, dan Value (Nilai) yang mencirikan warna biru dalam ruang warna HSV. Rentang ini mencakup nilai Hue antara 100 dan 130, serta nilai Saturation dan Value di atas 50.

Ambang Batas Warna Merah:

Ambang Bawah (Bagian 1): Nilai HSV [0, 50, 50]
Ambang Atas (Bagian 1): Nilai HSV [10, 255, 255]
Ambang Bawah (Bagian 2): Nilai HSV [170, 50, 50]
Ambang Atas (Bagian 2): Nilai HSV [180, 255, 255]
Ambang batas ini terdiri dari dua bagian untuk menangani variasi warna merah yang terletak di sekitar nol dan yang melintasi nilai maksimum. Bagian pertama mencakup rentang nilai Hue antara 0 dan 10, sedangkan bagian kedua mencakup nilai Hue yang melintasi 170 dan 180. Nilai Saturation dan Value-nya berada di atas 50.

Ambang Batas Warna Hijau:

Ambang Bawah: Nilai HSV [50, 50, 50]
Ambang Atas: Nilai HSV [80, 255, 255]
Ambang batas ini mengidentifikasi rentang nilai Hue, Saturation, dan Value yang mencirikan warna hijau dalam ruang warna HSV. Rentang ini mencakup nilai Hue antara 50 dan 80, serta nilai Saturation dan Value di atas 50.

# B. Penjelasan teori yang mendukung mengenai projek terkait
Teori Warna:
Teori warna merupakan pondasi utama dalam pemrosesan citra berwarna. Dalam konteks analisis citra, pemahaman yang baik tentang teori warna membantu dalam segmentasi objek berdasarkan karakteristik warnanya. Anda dapat memanfaatkan model warna seperti RGB (Red, Green, Blue) atau HSV (Hue, Saturation, Value) untuk mengidentifikasi dan memisahkan objek berdasarkan warna mereka.

Transformasi Citra:
Transformasi citra adalah teknik yang digunakan untuk mengubah representasi citra dari satu domain ke domain lain yang lebih sesuai untuk analisis tertentu. Misalnya, konversi citra ke ruang warna HSV memudahkan segmentasi warna karena memisahkan informasi warna dari kecerahan. Penggunaan transformasi Fourier atau transformasi wavelet juga berguna dalam menganalisis frekuensi atau tekstur dalam citra.

Segmentasi Citra:
Segmentasi citra adalah proses membagi citra menjadi bagian-bagian yang saling terpisah, biasanya berdasarkan karakteristik seperti warna, kecerahan, atau tekstur. Anda dapat menerapkan berbagai metode segmentasi, termasuk thresholding, clustering, atau pemrosesan morfologi, untuk mengidentifikasi dan memisahkan objek dari latar belakang.

Ekstraksi Fitur:
Ekstraksi fitur adalah proses mengidentifikasi dan mengekstraksi informasi penting dari citra yang relevan untuk analisis lebih lanjut. Ini dapat mencakup fitur-fitur seperti tekstur, pola, atau bentuk objek. Melalui ekstraksi fitur yang tepat, Anda dapat mengidentifikasi objek secara lebih spesifik dan membedakan antara objek yang berbeda dalam citra.

Klasifikasi dan Pengenalan Pola:
Setelah fitur-fitur diekstraksi, langkah selanjutnya adalah mengklasifikasikan objek ke dalam kategori-kategori yang telah ditentukan. Teori klasifikasi dan pengenalan pola memberikan landasan untuk memilih dan menerapkan algoritma klasifikasi yang sesuai, seperti Support Vector Machine (SVM), K-Nearest Neighbors (KNN), atau Convolutional Neural Networks (CNN), tergantung pada karakteristik data dan kompleksitas masalah.

Evaluasi dan Validasi:
Evaluasi dan validasi merupakan tahap penting dalam pengembangan sistem analisis citra. Ini melibatkan pengujian dan evaluasi kinerja sistem untuk memastikan keandalan dan akurasi hasilnya. Metrik evaluasi seperti akurasi, presisi, recall, dan F1-score digunakan untuk mengukur kualitas dan konsistensi hasil analisis.





