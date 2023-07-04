Lebih Banyak Alat Aliran Kontrol 
Selain whilepernyataan yang baru saja diperkenalkan, Python menggunakan pernyataan kontrol aliran biasa yang dikenal dari bahasa lain, dengan beberapa perubahan.

4.2. forPernyataan 
Pernyataan fordalam Python sedikit berbeda dari yang biasa Anda gunakan di C atau Pascal. Daripada selalu mengulangi perkembangan aritmatika angka (seperti di Pascal), atau memberi pengguna kemampuan untuk menentukan langkah iterasi dan menghentikan kondisi (sebagai C), pernyataan Python mengulangi item dari urutan apa pun (daftar atau fora string), dalam urutan yang muncul dalam urutan.

4.3. Fungsi range() _
Jika Anda perlu mengulangi urutan angka, fungsi bawaan range()akan berguna. Ini menghasilkan progresi aritmatika:

>>>
for i in range(5):
    print(i)

0
1
2
3
4
Titik akhir yang diberikan tidak pernah menjadi bagian dari urutan yang dihasilkan; range(10)menghasilkan 10 nilai, indeks legal untuk item dengan urutan panjang 10.

4.4. breakdan continuePernyataan, dan elseKlausul pada Pengulangan 
Pernyataan break, seperti di C, keluar dari penutup foratau whileloop terdalam.

Pernyataan pengulangan mungkin memiliki elseklausa; itu dieksekusi ketika loop berakhir melalui kelelahan iterable (dengan for) atau ketika kondisi menjadi salah (dengan while), tetapi tidak ketika loop diakhiri dengan breakpernyataan.

4.5. passPernyataan 
Pernyataan itu passtidak menghasilkan apa-apa. Itu dapat digunakan ketika pernyataan diperlukan secara sintaksis tetapi program tidak memerlukan tindakan. Misalnya:

>>>
while True:
    pass  # Busy-wait for keyboard interrupt (Ctrl+C)

matchPernyataan 
Pernyataan matchmengambil ekspresi dan membandingkan nilainya dengan pola berurutan yang diberikan sebagai satu atau lebih blok kasus. Ini mirip dengan pernyataan switch di C, Java atau JavaScript (dan banyak bahasa lainnya), tetapi lebih mirip dengan pencocokan pola dalam bahasa seperti Rust atau Haskell. Hanya pola pertama yang cocok yang akan dieksekusi dan juga dapat mengekstrak komponen (elemen urutan atau atribut objek) dari nilai menjadi variabel.

Mendefinisikan Fungsi
Kata kunci memperkenalkan definisidef fungsi . Itu harus diikuti oleh nama fungsi dan daftar parameter formal yang dikurung. Pernyataan yang membentuk isi fungsi dimulai dari baris berikutnya, dan harus diberi indentasi.

Pernyataan pertama dari badan fungsi secara opsional dapat berupa string literal; literal string ini adalah string dokumentasi fungsi, atau docstring . (Selengkapnya tentang docstring dapat ditemukan di bagian Documentation Strings .) Ada alat yang menggunakan docstring untuk menghasilkan dokumentasi online atau cetak secara otomatis, atau untuk membiarkan pengguna menelusuri kode secara interaktif; merupakan praktik yang baik untuk menyertakan dokumen dalam kode yang Anda tulis, jadi biasakanlah.

Eksekusi suatu fungsi memperkenalkan tabel simbol baru yang digunakan untuk variabel lokal dari fungsi tersebut . Lebih tepatnya, semua penugasan variabel dalam suatu fungsi menyimpan nilai dalam tabel simbol lokal; sedangkan referensi variabel pertama-tama terlihat di tabel simbol lokal, lalu di tabel simbol lokal fungsi terlampir, lalu di tabel simbol global, dan terakhir di tabel nama bawaan. Dengan demikian, variabel global dan variabel fungsi terlampir tidak dapat secara langsung diberi nilai dalam suatu fungsi (kecuali, untuk variabel global, disebutkan dalam pernyataan global, atau, untuk variabel fungsi terlampir, disebutkan dalam nonlocalpernyataan), meskipun mereka dapat direferensikan.

Parameter aktual (argumen) untuk pemanggilan fungsi diperkenalkan di tabel simbol lokal dari fungsi yang dipanggil saat dipanggil; dengan demikian, argumen diteruskan menggunakan call by value (di mana nilainya selalu merupakan referensi objek , bukan nilai objek). 1 Ketika suatu fungsi memanggil fungsi lain, atau memanggil dirinya sendiri secara rekursif, tabel simbol lokal baru dibuat untuk panggilan itu.

Definisi fungsi mengaitkan nama fungsi dengan objek fungsi dalam tabel simbol saat ini. Penerjemah mengenali objek yang ditunjuk oleh nama itu sebagai fungsi yang ditentukan pengguna.
