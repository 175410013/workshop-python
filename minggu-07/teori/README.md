9. Kelas 
Kelas menyediakan sarana bundling data dan fungsionalitas bersama. Membuat kelas baru akan membuat tipe objek baru, yang memungkinkan instance baru dari tipe tersebut dibuat. Setiap instance kelas dapat memiliki atribut yang melekat padanya untuk mempertahankan statusnya. Instance kelas juga dapat memiliki metode (ditentukan oleh kelasnya) untuk memodifikasi statusnya.

Dibandingkan dengan bahasa pemrograman lain, mekanisme kelas Python menambahkan kelas dengan sintaks dan semantik baru yang minimal. Ini adalah campuran dari mekanisme kelas yang ditemukan di C++ dan Modula-3. Kelas Python menyediakan semua fitur standar Pemrograman Berorientasi Objek: mekanisme pewarisan kelas memungkinkan banyak kelas dasar, kelas turunan dapat mengganti metode apa pun dari kelas atau kelas dasarnya, dan metode dapat memanggil metode kelas dasar dengan nama yang sama . Objek dapat berisi jumlah dan jenis data yang sewenang-wenang. Seperti halnya modul, kelas mengambil bagian dari sifat dinamis Python: mereka dibuat saat runtime, dan dapat dimodifikasi lebih lanjut setelah dibuat.

Dalam terminologi C++, biasanya anggota kelas (termasuk anggota data) bersifat publik (kecuali lihat di bawah Private Variables ), dan semua fungsi anggota bersifat virtual . Seperti di Modula-3, tidak ada singkatan untuk mereferensikan anggota objek dari metodenya: fungsi metode dideklarasikan dengan argumen pertama yang eksplisit yang mewakili objek, yang disediakan secara implisit oleh panggilan. Seperti di Smalltalk, kelas itu sendiri adalah objek. Ini menyediakan semantik untuk mengimpor dan mengganti nama. Tidak seperti C++ dan Modula-3, tipe bawaan dapat digunakan sebagai kelas dasar untuk ekstensi oleh pengguna. Juga, seperti di C++, sebagian besar operator bawaan dengan sintaks khusus (operator aritmatika, subskrip, dll.) dapat didefinisikan ulang untuk instance kelas.

(Kurangnya terminologi yang diterima secara universal untuk berbicara tentang kelas, saya akan sesekali menggunakan istilah Smalltalk dan C++. Saya akan menggunakan istilah Modula-3, karena semantik berorientasi objeknya lebih dekat dengan Python daripada C++, tetapi saya berharap bahwa beberapa pembaca pernah mendengarnya.)

9.1. Sepatah Kata Tentang Nama dan Objek 
Objek memiliki individualitas, dan banyak nama (dalam berbagai cakupan) dapat terikat ke objek yang sama. Ini dikenal sebagai aliasing dalam bahasa lain. Ini biasanya tidak dihargai pada pandangan pertama di Python, dan dapat diabaikan dengan aman ketika berhadapan dengan tipe dasar yang tidak dapat diubah (angka, string, tupel). Namun, aliasing mungkin memiliki efek yang mengejutkan pada semantik kode Python yang melibatkan objek yang dapat diubah seperti daftar, kamus, dan sebagian besar jenis lainnya. Ini biasanya digunakan untuk kepentingan program, karena alias berperilaku seperti penunjuk dalam beberapa hal. Misalnya, melewatkan objek itu murah karena hanya sebuah pointer yang dilewatkan oleh implementasi; dan jika sebuah fungsi memodifikasi objek yang diteruskan sebagai argumen, pemanggil akan melihat perubahannya — ini menghilangkan kebutuhan akan dua mekanisme penerusan argumen yang berbeda seperti di Pascal.

9.2. Lingkup dan Ruang Nama Python 
Sebelum memperkenalkan kelas, pertama-tama saya harus memberi tahu Anda sesuatu tentang aturan ruang lingkup Python. Definisi kelas memainkan beberapa trik rapi dengan ruang nama, dan Anda perlu mengetahui cara kerja ruang lingkup dan ruang nama untuk memahami sepenuhnya apa yang terjadi. Kebetulan, pengetahuan tentang subjek ini berguna untuk semua programmer Python tingkat lanjut.

Mari kita mulai dengan beberapa definisi.

Namespace adalah pemetaan dari nama ke objek . Sebagian besar ruang nama saat ini diimplementasikan sebagai kamus Python, tetapi biasanya tidak terlihat dengan cara apa pun (kecuali untuk kinerja), dan mungkin berubah di masa mendatang. Contoh ruang nama adalah: kumpulan nama bawaan (berisi fungsi seperti abs(), dan nama pengecualian bawaan); nama global dalam modul; dan nama lokal dalam pemanggilan fungsi. Dalam arti himpunan atribut suatu objek juga membentuk namespace. Hal penting yang harus diketahui tentang ruang nama adalah sama sekali tidak ada hubungan antara nama di ruang nama yang berbeda; misalnya, dua modul berbeda dapat mendefinisikan fungsi maximizetanpa kebingungan — pengguna modul harus mengawalinya dengan nama modul.

Omong-omong, saya menggunakan atribut kata untuk nama apa pun yang mengikuti titik — misalnya, dalam ekspresi z.real, realadalah atribut dari objek z. Sebenarnya, referensi ke nama dalam modul adalah referensi atribut: dalam ekspresi modname.funcname, modnameadalah objek modul dan funcnamemerupakan atributnya. Dalam hal ini terjadi pemetaan langsung antara atribut modul dan nama global yang ditentukan dalam modul: mereka berbagi namespace yang sama! 1

Atribut dapat berupa read-only atau writable. Dalam kasus terakhir, penugasan ke atribut dimungkinkan. Atribut modul dapat ditulis: Anda dapat menulis . Atribut yang dapat ditulis juga dapat dihapus dengan pernyataan tersebut. Misalnya, akan menghapus atribut dari objek bernama .modname.the_answer = 42deldel modname.the_answerthe_answermodname

Ruang nama dibuat pada momen yang berbeda dan memiliki masa hidup yang berbeda. Ruang nama yang berisi nama bawaan dibuat saat juru bahasa Python dijalankan, dan tidak pernah dihapus. Ruang nama global untuk modul dibuat saat definisi modul dibaca; biasanya, ruang nama modul juga bertahan hingga juru bahasa berhenti. Pernyataan yang dieksekusi oleh pemanggilan tingkat atas dari juru bahasa, baik dibaca dari file skrip atau secara interaktif, dianggap sebagai bagian dari modul bernama __main__, sehingga mereka memiliki ruang nama globalnya sendiri. (Nama bawaan sebenarnya juga ada di modul; ini disebut builtins.)

Ruang nama lokal untuk suatu fungsi dibuat saat fungsi dipanggil, dan dihapus saat fungsi mengembalikan atau memunculkan pengecualian yang tidak ditangani dalam fungsi. (Sebenarnya, melupakan akan menjadi cara yang lebih baik untuk menggambarkan apa yang sebenarnya terjadi.) Tentu saja, pemanggilan rekursif masing-masing memiliki namespace lokalnya sendiri.

Lingkup adalah wilayah tekstual dari program Python di mana namespace dapat diakses secara langsung . “Dapat diakses langsung” di sini berarti referensi yang tidak memenuhi syarat ke sebuah nama mencoba menemukan nama tersebut di namespace.

Meskipun cakupan ditentukan secara statis, cakupan digunakan secara dinamis. Setiap saat selama eksekusi, ada 3 atau 4 cakupan bersarang yang ruang namanya dapat diakses secara langsung:

lingkup terdalam, yang dicari terlebih dahulu, berisi nama-nama lokal

lingkup dari setiap fungsi terlampir, yang dicari dimulai dengan lingkup terlampir terdekat, berisi nama non-lokal, tetapi juga non-global

cakupan berikutnya hingga terakhir berisi nama global modul saat ini

lingkup terluar (dicari terakhir) adalah ruang nama yang berisi nama bawaan

Jika sebuah nama dideklarasikan secara global, maka semua referensi dan penetapan langsung menuju ke lingkup berikutnya hingga terakhir yang berisi nama global modul. Untuk mengikat ulang variabel yang ditemukan di luar lingkup terdalam, nonlocalpernyataan tersebut dapat digunakan; jika tidak dideklarasikan nonlocal, variabel-variabel tersebut bersifat read-only (upaya untuk menulis ke variabel semacam itu hanya akan membuat variabel lokal baru dalam lingkup terdalam, membiarkan variabel luar yang bernama identik tidak berubah).

Biasanya, cakupan lokal mereferensikan nama lokal dari fungsi (secara tekstual) saat ini. Di luar fungsi, cakupan lokal mereferensikan ruang nama yang sama dengan ruang lingkup global: ruang nama modul. Definisi kelas menempatkan namespace lain dalam lingkup lokal.

Penting untuk disadari bahwa cakupan ditentukan secara tekstual: cakupan global dari suatu fungsi yang didefinisikan dalam modul adalah ruang nama modul itu, tidak peduli dari mana atau dengan alias apa fungsi itu dipanggil. Di sisi lain, pencarian nama sebenarnya dilakukan secara dinamis, pada saat dijalankan — namun, definisi bahasa berkembang menuju resolusi nama statis, pada waktu "kompilasi", jadi jangan bergantung pada resolusi nama dinamis! (Faktanya, variabel lokal sudah ditentukan secara statis.)

Keunikan khusus Python adalah - jika tidak ada globalatau nonlocal pernyataan berlaku - penugasan ke nama selalu masuk ke ruang lingkup terdalam. Tugas tidak menyalin data — tugas hanya mengikat nama ke objek. Hal yang sama berlaku untuk penghapusan: pernyataan menghapus pengikatan dari namespace yang direferensikan oleh lingkup lokal. Faktanya, semua operasi yang memperkenalkan nama baru menggunakan lingkup lokal: khususnya, pernyataan dan definisi fungsi mengikat nama modul atau fungsi dalam lingkup lokal.del xximport

Pernyataan tersebut globaldapat digunakan untuk menunjukkan bahwa variabel tertentu hidup dalam lingkup global dan harus dipantulkan kembali ke sana; pernyataan tersebut nonlocalmenunjukkan bahwa variabel tertentu hidup dalam lingkup yang melingkupi dan harus dikembalikan ke sana.
