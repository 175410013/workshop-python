Memulai dengan conda
Conda adalah pengelola paket dan pengelola lingkungan tangguh yang Anda gunakan dengan perintah baris perintah di Anaconda Prompt untuk Windows, atau di jendela terminal untuk macOS atau Linux.

Panduan 20 menit untuk memulai conda ini memungkinkan Anda mencoba fitur-fitur utama conda. Anda harus memahami cara kerja conda saat Anda menyelesaikan panduan ini.

LIHAT JUGA: Memulai dengan Anaconda Navigator , antarmuka pengguna grafis yang memungkinkan Anda menggunakan conda dalam antarmuka seperti web tanpa harus memasukkan perintah manual. Bandingkan panduan Memulai masing-masing untuk melihat program mana yang Anda sukai.

Sebelum kamu memulai
Anda seharusnya sudah menginstal Anaconda .

Isi
Memulai conda di Windows, macOS, atau Linux. 2 MENIT

Mengelola konda . Verifikasi bahwa Anaconda diinstal dan periksa apakah conda diperbarui ke versi saat ini. 3 MENIT

Mengelola lingkungan . Ciptakan lingkungan dan pindahkan dengan mudah di antaranya. 5 MENIT

Mengelola Python . Buat lingkungan yang memiliki versi Python yang berbeda. 5 MENIT

Mengelola paket . Temukan paket yang tersedia untuk Anda instal. Instal paket. 5 MENIT

Mengelola konda
Verifikasi bahwa conda diinstal dan dijalankan di sistem Anda dengan mengetik:

conda --version
Conda menampilkan nomor versi yang telah Anda instal. Anda tidak perlu menavigasi ke direktori Anaconda.

CONTOH:conda 4.7.12

Catatan

Jika Anda mendapatkan pesan kesalahan, pastikan Anda menutup dan membuka kembali jendela terminal setelah menginstal, atau lakukan sekarang. Kemudian verifikasi bahwa Anda masuk ke akun pengguna yang sama dengan yang Anda gunakan untuk menginstal Anaconda atau Miniconda.

Perbarui conda ke versi saat ini. Ketik berikut ini:

conda update conda
Conda membandingkan versi dan kemudian menampilkan apa yang tersedia untuk diinstal.

Jika versi conda yang lebih baru tersedia, ketik yuntuk memperbarui:

Proceed ([y]/n)? y
Tip

Kami menyarankan Anda untuk selalu memperbarui conda ke versi terbaru.

Mengelola lingkungan
Conda memungkinkan Anda membuat lingkungan terpisah yang berisi file, paket, dan dependensinya yang tidak akan berinteraksi dengan lingkungan lain.

Saat Anda mulai menggunakan conda, Anda sudah memiliki lingkungan default bernama base. Anda tidak ingin memasukkan program ke dalam lingkungan dasar Anda. Buat lingkungan terpisah untuk menjaga agar program Anda tetap terisolasi satu sama lain.

Buat lingkungan baru dan instal paket di dalamnya.

Kami akan memberi nama lingkungan snowflakesdan menginstal paket BioPython. Di Anaconda Prompt atau di jendela terminal Anda, ketik berikut ini:

conda create --name snowflakes biopython
Conda memeriksa untuk melihat paket tambahan apa ("ketergantungan") yang dibutuhkan BioPython, dan menanyakan apakah Anda ingin melanjutkan:

Proceed ([y]/n)? y
Ketik "y" dan tekan Enter untuk melanjutkan.

Untuk menggunakan, atau "mengaktifkan" lingkungan baru, ketik berikut ini:

Jendela:conda activate snowflakes

macOS dan Linux:conda activate snowflakes

Catatan

conda activatehanya berfungsi pada conda 4.6 dan versi yang lebih baru.

Untuk versi conda sebelum 4.6, ketik:

Jendela:activate snowflakes

macOS dan Linux:source activate snowflakes

Sekarang Anda berada di snowflakeslingkungan Anda, perintah conda apa pun yang Anda ketikkan akan masuk ke lingkungan itu hingga Anda menonaktifkannya.

Untuk melihat daftar semua lingkungan Anda, ketik:

conda info --envs
Daftar lingkungan muncul, mirip dengan berikut ini:

conda environments:

    base           /home/username/Anaconda3
    snowflakes   * /home/username/Anaconda3/envs/snowflakes
Tip

Lingkungan aktif adalah lingkungan dengan tanda bintang (*).

Ubah lingkungan Anda saat ini kembali ke default (basis): conda activate

Catatan

Untuk versi sebelum conda 4.6, gunakan:

Jendela: activate

macOS, Linux:source activate

Tip

Saat lingkungan dinonaktifkan, namanya tidak lagi ditampilkan di prompt Anda, dan asterisk (*) kembali ke dasar. Untuk memverifikasi, Anda dapat mengulangi perintah.conda info --envs

Mengelola Python
Saat Anda membuat lingkungan baru, conda menginstal versi Python yang sama dengan yang Anda gunakan saat mengunduh dan menginstal Anaconda. Jika Anda ingin menggunakan versi Python yang berbeda, misalnya Python 3.5, cukup buat lingkungan baru dan tentukan versi Python yang Anda inginkan.

Buat lingkungan baru bernama "ular" yang berisi Python 3.9:

conda create --name snakes python=3.9
Saat conda menanyakan apakah Anda ingin melanjutkan, ketik "y" dan tekan Enter.

Aktifkan lingkungan baru:

Jendela:conda activate snakes

macOS dan Linux:conda activate snakes

Catatan

conda activatehanya berfungsi pada conda 4.6 dan versi yang lebih baru.

Untuk versi conda sebelum 4.6, ketik:

Jendela:activate snakes

macOS dan Linux:source activate snakes

Verifikasi bahwa lingkungan ular telah ditambahkan dan aktif:

conda info --envs
Conda menampilkan daftar semua lingkungan dengan tanda bintang (*) setelah nama lingkungan aktif:

# conda environments:
#
base                     /home/username/anaconda3
snakes                *  /home/username/anaconda3/envs/snakes
snowflakes               /home/username/anaconda3/envs/snowflakes
Lingkungan aktif juga ditampilkan di depan prompt Anda di (tanda kurung) atau [tanda kurung] seperti ini:

(snakes) $
Verifikasi versi Python mana yang ada di lingkungan Anda saat ini:

python --version
Nonaktifkan lingkungan ular dan kembali ke lingkungan dasar: conda activate

Catatan

Untuk versi sebelum conda 4.6, gunakan:

Jendela: activate

macOS, Linux:source activate

Mengelola paket
Di bagian ini, Anda memeriksa paket mana yang telah Anda instal, memeriksa mana yang tersedia dan mencari paket tertentu dan menginstalnya.

Untuk menemukan paket yang telah Anda instal, aktifkan terlebih dahulu lingkungan yang ingin Anda cari. Lihat di atas untuk perintah untuk mengaktifkan lingkungan ular Anda .

Periksa untuk melihat apakah paket yang belum Anda instal bernama "beautifulsoup4" tersedia dari repositori Anaconda (harus terhubung ke Internet):

conda search beautifulsoup4
Conda menampilkan daftar semua paket dengan nama itu di repositori Anaconda, jadi kami tahu itu tersedia.

Instal paket ini ke lingkungan saat ini:

conda install beautifulsoup4
Periksa untuk melihat apakah program yang baru diinstal ada di lingkungan ini:

conda list
