8. Kesalahan dan Pengecualian 
Sampai saat ini pesan kesalahan belum banyak disebutkan, tetapi jika Anda telah mencoba contoh-contohnya, Anda mungkin telah melihat beberapa. Ada (setidaknya) dua jenis kesalahan yang dapat dibedakan: kesalahan sintaks dan pengecualian .

8.1. Kesalahan Sintaks 
Kesalahan sintaksis, juga dikenal sebagai kesalahan parsing, mungkin merupakan jenis keluhan paling umum yang Anda dapatkan saat masih mempelajari Python:

>>>
while True print('Hello world')
  File "<stdin>", line 1
    while True print('Hello world')
                   ^
SyntaxError: invalid syntax
Parser mengulangi baris yang menyinggung dan menampilkan 'panah' kecil yang menunjuk ke titik paling awal di baris tempat kesalahan terdeteksi. Kesalahan disebabkan oleh (atau setidaknya terdeteksi pada) token yang mendahului tanda panah: dalam contoh, kesalahan terdeteksi pada fungsi print(), karena titik dua ( ':') tidak ada sebelumnya. Nama file dan nomor baris dicetak sehingga Anda tahu ke mana harus mencari jika input berasal dari skrip.

8.2. Pengecualian 
Bahkan jika sebuah pernyataan atau ekspresi benar secara sintaksis, itu dapat menyebabkan kesalahan ketika upaya dilakukan untuk mengeksekusinya. Kesalahan yang terdeteksi selama eksekusi disebut pengecualian dan tidak fatal tanpa syarat: Anda akan segera belajar cara menanganinya dalam program Python. Namun, sebagian besar pengecualian tidak ditangani oleh program, dan menghasilkan pesan kesalahan seperti yang ditampilkan di sini:

>>>
10 * (1/0)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: division by zero
4 + spam*3
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'spam' is not defined
'2' + 2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate str (not "int") to str
Baris terakhir dari pesan kesalahan menunjukkan apa yang terjadi. Pengecualian datang dalam berbagai jenis, dan jenisnya dicetak sebagai bagian dari pesan: jenis dalam contoh adalah ZeroDivisionError, NameErrordan TypeError. String yang dicetak sebagai tipe pengecualian adalah nama dari pengecualian bawaan yang terjadi. Ini berlaku untuk semua pengecualian bawaan, tetapi tidak harus benar untuk pengecualian yang ditentukan pengguna (walaupun ini adalah konvensi yang berguna). Nama pengecualian standar adalah pengidentifikasi bawaan (bukan kata kunci yang dicadangkan).

Baris selanjutnya memberikan detail berdasarkan jenis pengecualian dan apa yang menyebabkannya.

Bagian sebelumnya dari pesan kesalahan menunjukkan konteks di mana pengecualian terjadi, dalam bentuk stack traceback. Secara umum ini berisi baris sumber daftar traceback stack; namun, ini tidak akan menampilkan baris yang dibaca dari input standar.

Pengecualian Bawaan mencantumkan pengecualian bawaan dan artinya.

8.3. Menangani Pengecualian 
Dimungkinkan untuk menulis program yang menangani pengecualian yang dipilih. Lihat contoh berikut, yang meminta input dari pengguna sampai bilangan bulat yang valid telah dimasukkan, tetapi memungkinkan pengguna untuk menginterupsi program (menggunakan atau apa pun yang didukung oleh sistem operasi); perhatikan bahwa interupsi yang dibuat pengguna ditandai dengan memunculkan pengecualian .Control-CKeyboardInterrupt

>>>
while True:
    try:
        x = int(input("Please enter a number: "))
        break
    except ValueError:
        print("Oops!  That was no valid number.  Try again...")

Pernyataan tersebut tryberfungsi sebagai berikut.

Pertama, klausa try (pernyataan antara trydan exceptkata kunci) dijalankan.

Jika tidak ada pengecualian yang terjadi, kecuali klausa dilewati dan eksekusi pernyataan tryselesai.

Jika pengecualian terjadi selama eksekusi klausa try, klausa lainnya akan dilewati. Kemudian, jika tipenya cocok dengan pengecualian yang dinamai menurut exceptkata kunci, klausa kecuali dieksekusi, dan kemudian eksekusi dilanjutkan setelah blok coba/kecuali.

Jika pengecualian terjadi yang tidak cocok dengan pengecualian yang disebutkan dalam klausa kecuali , itu diteruskan ke trypernyataan luar; jika tidak ada penangan yang ditemukan, itu adalah pengecualian yang tidak tertangani dan eksekusi berhenti dengan pesan seperti yang ditunjukkan di atas.

Pernyataan trymungkin memiliki lebih dari satu kecuali klausa , untuk menentukan penangan untuk pengecualian yang berbeda. Paling banyak satu penangan akan dieksekusi. Penangan hanya menangani pengecualian yang terjadi pada klausa try yang sesuai , bukan pada penangan lain dari trypernyataan yang sama. Klausa exception dapat menyebutkan beberapa pengecualian sebagai tupel dalam tanda kurung, misalnya:

... except (RuntimeError, TypeError, NameError):
...     pass
Kelas dalam exceptklausa kompatibel dengan pengecualian jika itu adalah kelas yang sama atau kelas dasar daripadanya (tetapi bukan sebaliknya — klausa pengecualian yang mencantumkan kelas turunan tidak kompatibel dengan kelas dasar).
