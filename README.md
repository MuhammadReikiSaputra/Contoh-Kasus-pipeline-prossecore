# Tahapan instruksi dan Contoh Kasus Pipeline Prossecore

### Pengertian Pipeline
  _Pipeline_ adalah suatu cara yang digunakan untuk melakukan sejumlah kerja secara bersama tetapi dalam tahap yang berbeda yang dialirkan secara kontinu pada unit pemrosesor. Dengan cara ini, maka unit pemrosesan selalu bekerja.

Teknik pipeline ini dapat diterapkan pada berbagai tingkatan dalam sistem komputer. Bisa pada level yang tinggi, misalnya program aplikasi, sampai pada tingkat yang rendah, seperti pada instruksi yang dijaankan oleh _microprocessor_.

 Pada microprocessor yang tidak menggunakan  pipeline , satu instruksi dilakukan sampai selesai, baru instruksi berikutnya dapat dilaksanakan. Sedangkan dalam microprocessor yang menggunakan teknik pipeline, ketika satu instruksi sedangkan diproses, maka instruksi yang berikutnya juga dapat diproses dalam waktu yang bersamaan. Tetapi, instruksi yang diproses secara bersamaan ini, ada dalam tahap proses yang berbeda. Jadi, ada sejumlah tahapan yang akan dilewati oleh sebuah instruksi.

   Dengan penerapan  pipeline  ini pada microprocessor akan didapatkan peningkatan kinerja microprocessor. Hal ini terjadi karena beberapa instruksi dapat dilakukan secara parallel dalam waktu yang bersamaan. Secara kasarnya diharapkan akan didapatkan peningkatan sebesar K kali dibandingkan dengan microprocessor yang tidak menggunakan  pipeline , apabila tahapan yang ada dalam satu kali pemrosesan instruksi adalah K tahap.

  Teknik  pipeline  ini menyebabkan ada sejumlah hal yang harus diperhatikan sehingga ketika diterapkan dapat berjalan dengan baik.

Tiga kesulitan yang sering dihadapi ketika menggunakan teknik  pipeline  ini adalah :
 1. Terjadinya penggunaan resource yang bersamaan
 2. Ketergantungan terhadap data, dan
 3. Pengaturan Jump ke suatu lokasi memori.

### Instruksi pada pipeline
_Tahapan pipeline_
  - Mengambil instruksi dan membuffferkannya
  - Ketika tahapan kedua bebas tahapan pertama mengirimkan instruksi yang dibufferkan tersebut
  - Pada saat tahapan kedua sedang mengeksekusi instruksi ,tahapan pertama memanfaatkan siklus       memori yang tidak dipakai untuk mengambil dan membuffferkan instruksi berikutnya

### Berikut ini adalah gambar tentang Instuksi pipeline

![th](https://github.com/user-attachments/assets/2512b8c7-9b1b-469f-becc-97b19ebb82ea)

Karena untuk setiap tahap pengerjaan instruksi, komponen yang bekerja berbeda, maka dimungkinkan untuk mengisi kekosongan kerja di komponen tersebut. Sebagai contoh :

_Instruksi  1 _: ADD  AX, AX Instruksi 2: ADD EX, CX

Setelah CU menjemput instruksi 1 dari memori (IF), CU akan menerjemahkan instruksi tersebut(ID). Pada menerjemahkan instruksi  1 tersebut, komponen IF tidak bekerja. Adanya teknologi pipeline menyebabkan IF akan menjemput instruksi 2 pada saat ID menerjemahkan instruksi 1. Demikian seterusnya pada saat CU menjalankan instruksi 1 (EX), instruksi 2 diterjemahkan (ID).
### Contoh pengerjaan instruksi tanpa pipeline

![Screenshot 2025-04-20 201034](https://github.com/user-attachments/assets/baea252b-7265-4aea-a4b7-f4abf8cf1891)

### Contoh pengerjaan instruksi dengan pipeline

![Screenshot 2025-04-20 201151](https://github.com/user-attachments/assets/14b8b622-0b45-40bf-af4b-344c942e9f98)
  Dengan adanya  pipeline  dua instruksi selesai dilaksanakan padadetik keenam (sedangkan pada kasus tanpa pipeline baru selesai pada detik kesepuluh). Dengan demikian telah terjadi percepatan sebanyak 1,67x dari 10T menjadi hanya 6T. Sedangkan untuk pengerjaan 3 buah instruksi terjadi percepatan sebanyak 2, 14x dari 15T menjadi hanya 7T.

  Untuk kasus  pipeline  sendiri, 2 instruksi dapat dikerjakan dalam 6T (CPI = 3) dan instruksi dapat dikerjakan dalam 7T (CPT = 2,3) dan untuk 4 instruksi dapat dikerjakan dalam  8T (CPI =2). Ini berarti untuk 100 instruksi akan dapat dikerjakan dalam 104T (CPI = 1,04). Pada kondisi  ideal CPI akan harga 1.

### Masalah-masalah pada Pipeline
   Dengan adanya persyaratan bahwa setiap instuksi yang berdekatan harus tidak saling bergantung, maka ada kemungkinan terjadinya situasi dimana pipeline gagal dilaksanakan (instruksi berikutnya tidak bisa dilaksanakan). Situasi ini disebut Hazards. Hazards mengurangi performansi dari CPU dimana percepatan ideal tidak dapat dicapai.

Ada 3 kelompok Hazards :
 1. **Structural Hazards** muncul dari konflik resource sistem yaitu ketika hardware tidak dapat mensuport semua kemungkinan kombinasi pelaksanaan instruksi. 
 2. **Data Hazards** muncul ketika data untuk suatu instruksi tergantung pada hasil instruksi sebelumnya. 
 3. **Control Hazards** muncul pada pelaksanaan instruksi yang mengubah PC (_contoh_ : branch).
        Adanya _**Hazards**_ menyebabkan pipeline terhambat (_stalled_). Tidak ada instruksi baru yang dijemput sampai hambatan itu selesai. Ini berarti instruksi-instruksi selanjutnya akan ditunda pula penjemputannya.

### Keuntungan dari Pipeline
 1. Waktu siklus prosesor berkurang, sehingga meningkatkan tingkat instruksi-isu dalam kebanyakan kasus.
 2. Beberapa combinational sirkuit seperti penambah atau pengganda dapat dibuat lebih cepat dengan menambahkan lebih banyak sirkuit.
Jika  pipeline  digunakan sebagai pengganti, hal itu dapat menghemat sirkuit vs combinational yang lebih kompleks sirkuit.

### Kerugian dari Pipeline
 1. Prossesor  non-pipeline hanya menjalankan satu instruksi pada satu waktu. Hal ini untuk mencegah 
    penundaan cabang (yang berlaku, setiap cabang tertunda) dan masalah dengan serial instruksi dieksekusi 
    secara bersamaan. Akibatnya desain lebih sederhana dan lebih murah untuk diproduksi.
 2. Instruksi latency di prossesor non-pipeline sedikit lebih rendah daripada dalam pipeline setara. Hal ini 
    disebabkan oleh fakta bahwa sandal jepit ekstra harus ditambahkan ke jalur data dari prossesor pipeline.
 3. Prossesor non-pipeline akan memiliki instruksi bandwidth yang stabil. Kinerja prossesor yang pipeline 
    jauh lebih sulit untuk meramalkan dan dapat bervariasi lebih luas di antara program yang berbeda.
