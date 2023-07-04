Errors and Exceptions
Until now error messages haven’t been more than mentioned, but if you have tried out the examples you have probably seen some. There are (at least) two distinguishable kinds of errors: syntax errors and exceptions.

8.1. Syntax Errors
Syntax errors, also known as parsing errors, are perhaps the most common kind of complaint you get while you are still learning Python:

>>>
while True print('Hello world')
  File "<stdin>", line 1
    while True print('Hello world')
                   ^
SyntaxError: invalid syntax
The parser repeats the offending line and displays a little ‘arrow’ pointing at the earliest point in the line where the error was detected. The error is caused by (or at least detected at) the token preceding the arrow: in the example, the error is detected at the function print(), since a colon (':') is missing before it. File name and line number are printed so you know where to look in case the input came from a script.

8.2. Exceptions
Even if a statement or expression is syntactically correct, it may cause an error when an attempt is made to execute it. Errors detected during execution are called exceptions and are not unconditionally fatal: you will soon learn how to handle them in Python programs. Most exceptions are not handled by programs, however, and result in error messages as shown here:

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
The last line of the error message indicates what happened. Exceptions come in different types, and the type is printed as part of the message: the types in the example are ZeroDivisionError, NameError and TypeError. The string printed as the exception type is the name of the built-in exception that occurred. This is true for all built-in exceptions, but need not be true for user-defined exceptions (although it is a useful convention). Standard exception names are built-in identifiers (not reserved keywords).

The rest of the line provides detail based on the type of exception and what caused it.

The preceding part of the error message shows the context where the exception occurred, in the form of a stack traceback. In general it contains a stack traceback listing source lines; however, it will not display lines read from standard input.

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
Kelas dalam exceptklausa kompatibel dengan pengecualian jika itu adalah kelas yang sama atau kelas dasar daripadanya (tetapi bukan sebaliknya — klausa pengecualian yang mencantumkan kelas turunan tidak kompatibel dengan kelas dasar). Misalnya, kode berikut akan mencetak B, C, D dalam urutan tersebut:
