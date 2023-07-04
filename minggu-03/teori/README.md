5. Struktur Data 
Bab ini menjelaskan beberapa hal yang telah Anda pelajari secara lebih mendetail, dan menambahkan beberapa hal baru juga.

5.1. Selengkapnya tentang Daftar 
Tipe data daftar memiliki beberapa metode lagi. Berikut ini semua metode objek daftar:

daftar. tambahkan ( x )
Tambahkan item ke akhir daftar. Setara dengan .a[len(a):] = [x]

daftar. memperpanjang ( dapat diubah )
Perpanjang daftar dengan menambahkan semua item dari iterable. Setara dengan .a[len(a):] = iterable

daftar. sisipkan ( i , x )
Masukkan item pada posisi tertentu. Argumen pertama adalah indeks elemen sebelum disisipkan, jadi sisipkan di bagian depan daftar, dan sama dengan .a.insert(0, x)a.insert(len(a), x)a.append(x)

daftar. hapus ( x )
Hapus item pertama dari daftar yang nilainya sama dengan x . Itu memunculkan ValueErrorjika tidak ada item seperti itu.

daftar. pop ( [ i ] )
Hapus item pada posisi yang diberikan dalam daftar, dan kembalikan. Jika tidak ada indeks yang ditentukan, a.pop()hapus dan kembalikan item terakhir dalam daftar. (Kurung siku di sekitar i pada tanda tangan metode menunjukkan bahwa parameternya opsional, bukan berarti Anda harus mengetikkan tanda kurung siku pada posisi itu. Anda akan sering melihat notasi ini di Referensi Pustaka Python.)

daftar. jelas ( )
Hapus semua item dari daftar. Setara dengan .del a[:]

daftar. indeks ( x [ , awal [ , akhir ] ] )
Kembalikan indeks berbasis nol dalam daftar item pertama yang nilainya sama dengan x . Menaikkan a ValueErrorjika tidak ada item seperti itu.

Argumen opsional awal dan akhir diinterpretasikan seperti dalam notasi irisan dan digunakan untuk membatasi pencarian ke urutan tertentu dari daftar. Indeks yang dikembalikan dihitung relatif terhadap awal urutan penuh daripada argumen awal .

daftar. hitung ( x )
Kembalikan berapa kali x muncul dalam daftar.

daftar. urutkan ( * , kunci = Tidak ada , mundur = Salah )
Sortir item daftar pada tempatnya (argumen dapat digunakan untuk mengurutkan kustomisasi, lihat sorted()penjelasannya).

daftar. terbalik ( )
Balikkan elemen daftar pada tempatnya.

daftar. salin ( )
Kembalikan salinan daftar yang dangkal. Setara dengan a[:].

Anda mungkin telah memperhatikan bahwa metode seperti insert, removeatau sortyang hanya mengubah daftar tidak memiliki nilai kembalian yang dicetak – mereka mengembalikan default None. 1 Ini adalah prinsip desain untuk semua struktur data yang bisa berubah di Python.

Hal lain yang mungkin Anda perhatikan adalah tidak semua data dapat diurutkan atau dibandingkan. Misalnya, tidak mengurutkan karena bilangan bulat tidak dapat dibandingkan dengan string dan Tidak ada yang tidak dapat dibandingkan dengan tipe lainnya. Selain itu, ada beberapa tipe yang tidak memiliki relasi pengurutan yang ditentukan. Misalnya, bukan perbandingan yang valid.[None, 'hello', 10]3+4j < 5+7j

5.1.1. Menggunakan Daftar sebagai Tumpukan 
Metode daftar membuatnya sangat mudah untuk menggunakan daftar sebagai tumpukan, di mana elemen terakhir yang ditambahkan adalah elemen pertama yang diambil (“last-in, first-out”). Untuk menambahkan item ke atas tumpukan, gunakan append(). Untuk mengambil item dari atas tumpukan, gunakan pop()tanpa indeks eksplisit.
