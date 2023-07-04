7. Masukan dan Keluaran 
Ada beberapa cara untuk mempresentasikan output dari suatu program; data dapat dicetak dalam bentuk yang dapat dibaca manusia, atau ditulis ke file untuk digunakan di masa mendatang. Bab ini akan membahas beberapa kemungkinan.

7.1. Pemformatan Keluaran Lebih Menarik 
Sejauh ini kita menemukan dua cara penulisan nilai: pernyataan ekspresi dan print()fungsi. (Cara ketiga menggunakan write()metode objek file; file keluaran standar dapat dirujuk sebagai sys.stdout. Lihat Referensi Perpustakaan untuk informasi lebih lanjut tentang ini.)

Seringkali Anda menginginkan kontrol lebih besar atas pemformatan keluaran Anda daripada sekadar mencetak nilai yang dipisahkan oleh ruang. Ada beberapa cara untuk memformat keluaran.

Untuk menggunakan literal string terformat , awali string dengan fatau Fsebelum tanda kutip pembuka atau tanda kutip tiga. Di dalam string ini, Anda dapat menulis ekspresi Python antara karakter {dan } yang dapat merujuk ke variabel atau nilai literal.

Metode str.format()string membutuhkan lebih banyak usaha manual. Anda masih akan menggunakan {dan }untuk menandai di mana variabel akan diganti dan dapat memberikan arahan pemformatan yang mendetail, tetapi Anda juga harus memberikan informasi yang akan diformat.

Terakhir, Anda dapat melakukan semua penanganan string sendiri dengan menggunakan pemotongan string dan operasi penggabungan untuk membuat tata letak apa pun yang dapat Anda bayangkan. Tipe string memiliki beberapa metode yang melakukan operasi berguna untuk mengisi string ke lebar kolom tertentu.

Saat Anda tidak membutuhkan output mewah tetapi hanya ingin tampilan cepat dari beberapa variabel untuk keperluan debugging, Anda dapat mengonversi nilai apa pun menjadi string dengan fungsi repr()atau str().

Fungsi ini str()dimaksudkan untuk mengembalikan representasi nilai yang dapat dibaca oleh manusia, sementara repr()dimaksudkan untuk menghasilkan representasi yang dapat dibaca oleh penafsir (atau akan memaksa a SyntaxErrorjika tidak ada sintaks yang setara). Untuk objek yang tidak memiliki representasi khusus untuk konsumsi manusia, str()akan mengembalikan nilai yang sama dengan repr(). Banyak nilai, seperti angka atau struktur seperti daftar dan kamus, memiliki representasi yang sama menggunakan salah satu fungsi. String, khususnya, memiliki dua representasi berbeda.

7.1.1. Literal String Terformat 
Literal string terformat (disingkat juga disebut f-string) memungkinkan Anda menyertakan nilai ekspresi Python di dalam string dengan mengawali string denganforFdan menulis ekspresi sebagai {expression}.

7.1.2. Metode String format() 
Penggunaan dasar metode ini str.format()terlihat seperti ini:

>>>
print('We are the {} who say "{}!"'.format('knights', 'Ni'))
We are the knights who say "Ni!"
Tanda kurung dan karakter di dalamnya (disebut bidang format) diganti dengan objek yang diteruskan ke str.format()metode. Angka dalam tanda kurung dapat digunakan untuk merujuk ke posisi objek yang diteruskan ke metode str.format().
