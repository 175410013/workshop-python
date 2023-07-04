6. Modul 
Jika Anda keluar dari juru bahasa Python dan memasukkannya lagi, definisi yang Anda buat (fungsi dan variabel) akan hilang. Oleh karena itu, jika Anda ingin menulis program yang agak panjang, lebih baik Anda menggunakan editor teks untuk menyiapkan input untuk juru bahasa dan menjalankannya dengan file tersebut sebagai input. Ini dikenal sebagai membuat skrip . Saat program Anda semakin panjang, Anda mungkin ingin membaginya menjadi beberapa file untuk pemeliharaan yang lebih mudah. Anda mungkin juga ingin menggunakan fungsi praktis yang telah Anda tulis di beberapa program tanpa menyalin definisinya ke setiap program.

Untuk mendukung ini, Python memiliki cara untuk meletakkan definisi dalam file dan menggunakannya dalam skrip atau dalam contoh interaktif dari juru bahasa. File seperti itu disebut modul ; definisi dari modul dapat diimpor ke modul lain atau ke modul utama (kumpulan variabel yang dapat Anda akses dalam skrip yang dijalankan di tingkat atas dan dalam mode kalkulator).

Modul adalah file yang berisi definisi dan pernyataan Python. Nama file adalah nama modul dengan akhiran .pyditambahkan. Di dalam modul, nama modul (sebagai string) tersedia sebagai nilai dari variabel global __name__. Misalnya, gunakan editor teks favorit Anda untuk membuat file bernama fibo.

6.1. Lebih lanjut tentang Modul 
Modul dapat berisi pernyataan yang dapat dieksekusi serta definisi fungsi. Pernyataan ini dimaksudkan untuk menginisialisasi modul. Mereka dieksekusi hanya saat pertama kali nama modul ditemukan dalam pernyataan impor. 1 (Mereka juga dijalankan jika file dijalankan sebagai skrip.)

Setiap modul memiliki ruang nama pribadinya sendiri, yang digunakan sebagai ruang nama global oleh semua fungsi yang ditentukan dalam modul. Dengan demikian, pembuat modul dapat menggunakan variabel global di dalam modul tanpa khawatir tentang bentrok yang tidak disengaja dengan variabel global pengguna. Di sisi lain, jika Anda tahu apa yang Anda lakukan, Anda dapat menyentuh variabel global modul dengan notasi yang sama yang digunakan untuk merujuk ke fungsinya, modname.itemname.

Modul dapat mengimpor modul lain. Merupakan kebiasaan tetapi tidak diharuskan untuk menempatkan semua importpernyataan di awal modul (atau skrip, dalam hal ini). Nama modul yang diimpor, jika ditempatkan di tingkat atas modul (di luar fungsi atau kelas apa pun), ditambahkan ke ruang nama global modul.

6.1.2. Jalur Pencarian Modul 
Saat nama modul spamdiimpor, interpreter pertama-tama mencari modul bawaan dengan nama itu. Nama modul ini tercantum dalam sys.builtin_module_names. Jika tidak ditemukan, ia akan mencari file bernama spam.pydalam daftar direktori yang diberikan oleh variabel sys.path. sys.pathdiinisialisasi dari lokasi berikut:

Direktori yang berisi skrip input (atau direktori saat ini ketika tidak ada file yang ditentukan).

PYTHONPATH(daftar nama direktori, dengan sintaks yang sama dengan variabel shellPATH).

Default yang bergantung pada penginstalan (berdasarkan konvensi termasuk site-packagesdirektori, ditangani oleh sitemodul).

6.1.3. File Python yang “dikompilasi” 
Untuk mempercepat pemuatan modul, Python meng-cache versi terkompilasi dari setiap modul di __pycache__direktori dengan nama , di mana versi mengkodekan format file yang dikompilasi; umumnya berisi nomor versi Python. Misalnya, dalam rilis CPython 3.3, versi spam.py yang dikompilasi akan di-cache sebagai . Konvensi penamaan ini memungkinkan modul yang dikompilasi dari rilis yang berbeda dan versi Python yang berbeda untuk hidup berdampingan.module.version.pyc__pycache__/spam.cpython-33.pyc

Python memeriksa tanggal modifikasi sumber terhadap versi yang dikompilasi untuk melihat apakah sudah kedaluwarsa dan perlu dikompilasi ulang. Ini adalah proses yang sepenuhnya otomatis. Selain itu, modul yang dikompilasi tidak bergantung pada platform, sehingga pustaka yang sama dapat digunakan bersama di antara sistem dengan arsitektur yang berbeda.

Python tidak memeriksa cache dalam dua keadaan. Pertama, ia selalu mengkompilasi ulang dan tidak menyimpan hasil modul yang dimuat langsung dari baris perintah. Kedua, tidak memeriksa cache jika tidak ada modul sumber. Untuk mendukung distribusi non-sumber (hanya dikompilasi), modul yang dikompilasi harus berada di direktori sumber, dan tidak boleh ada modul sumber.

Beberapa tips untuk para ahli:

Anda dapat menggunakan -Oatau -OOmengaktifkan perintah Python untuk mengurangi ukuran modul yang dikompilasi. Sakelar -Omenghapus pernyataan tegas, -OOsakelar menghapus pernyataan tegas dan string __doc__. Karena beberapa program mungkin mengandalkan ketersediaan ini, Anda hanya boleh menggunakan opsi ini jika Anda tahu apa yang Anda lakukan. Modul "Dioptimalkan" memiliki opt-tag dan biasanya berukuran lebih kecil. Rilis mendatang dapat mengubah efek pengoptimalan.

Program tidak berjalan lebih cepat saat dibaca dari .pyc file daripada saat dibaca dari .pyfile; satu-satunya hal yang lebih cepat tentang .pycfile adalah kecepatan pemuatannya.

Modul compilealldapat membuat file .pyc untuk semua modul dalam direktori.

Ada detail lebih lanjut tentang proses ini, termasuk bagan alur keputusan, diPEP 3147 .
