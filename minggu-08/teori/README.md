10. Tur Singkat Perpustakaan Standar 
10.1. Antarmuka Sistem Operasi 
Modul ini osmenyediakan lusinan fungsi untuk berinteraksi dengan sistem operasi:

>>>
import os
os.getcwd()      # Return the current working directory
'C:\\Python311'
os.chdir('/server/accesslogs')   # Change current working directory
os.system('mkdir today')   # Run the command mkdir in the system shell
0
Pastikan untuk menggunakan gaya alih-alih . Ini akan mencegah membayangi fungsi bawaan yang beroperasi jauh berbeda.import osfrom os import *os.open()open()

Fungsi bawaan dir()dan help()berguna sebagai alat bantu interaktif untuk bekerja dengan modul besar seperti os:

>>>
import os
dir(os)
<returns a list of all module functions>
help(os)
<returns an extensive manual page created from the module's docstrings>
Untuk tugas manajemen file dan direktori harian, shutilmodul ini menyediakan antarmuka tingkat tinggi yang lebih mudah digunakan:

>>>
import shutil
shutil.copyfile('data.db', 'archive.db')
'archive.db'
shutil.move('/build/executables', 'installdir')
'installdir'
10.2. Ajukan Wildcard 
Modul ini globmenyediakan fungsi untuk membuat daftar file dari pencarian wildcard direktori:

>>>
import glob
glob.glob('*.py')
['primes.py', 'random.py', 'quote.py']
10.3. Argumen Baris Perintah 
Skrip utilitas umum seringkali perlu memproses argumen baris perintah. Argumen ini disimpan dalam atribut sysmodul argv sebagai daftar. Misalnya hasil keluaran berikut dari berjalan di baris perintah:python demo.py one two three

>>>
import sys
print(sys.argv)
['demo.py', 'one', 'two', 'three']
Modul ini argparsemenyediakan mekanisme yang lebih canggih untuk memproses argumen baris perintah. Skrip berikut mengekstrak satu atau lebih nama file dan sejumlah baris opsional untuk ditampilkan:

import argparse

parser = argparse.ArgumentParser(
    prog='top',
    description='Show top lines from each file')
parser.add_argument('filenames', nargs='+')
parser.add_argument('-l', '--lines', type=int, default=10)
args = parser.parse_args()
print(args)
Saat dijalankan pada baris perintah dengan , skrip diatur ke dan ke .python top.py --lines=5 alpha.txt beta.txtargs.lines5args.filenames['alpha.txt', 'beta.txt']

10.4. Kesalahan Pengalihan Keluaran dan Penghentian Program 
Modul ini sysjuga memiliki atribut untuk stdin , stdout , dan stderr . Yang terakhir berguna untuk memancarkan peringatan dan pesan kesalahan agar terlihat bahkan ketika stdout telah dialihkan:

>>>
sys.stderr.write('Warning, log file not found starting a new one\n')
Warning, log file not found starting a new one
Cara paling langsung untuk mengakhiri skrip adalah dengan menggunakan sys.exit().

10.5. Pencocokan Pola Tali 
Modul ini remenyediakan alat ekspresi reguler untuk pemrosesan string tingkat lanjut. Untuk pencocokan dan manipulasi yang rumit, ekspresi reguler menawarkan solusi ringkas dan optimal:

>>>
import re
re.findall(r'\bf[a-z]*', 'which foot or hand fell fastest')
['foot', 'fell', 'fastest']
re.sub(r'(\b[a-z]+) \1', r'\1', 'cat in the the hat')
'cat in the hat'
Ketika hanya kemampuan sederhana yang diperlukan, metode string lebih disukai karena lebih mudah dibaca dan di-debug:

>>>
'tea for too'.replace('too', 'two')
'tea for two'
10.6. Matematika 
Modul ini mathmemberikan akses ke fungsi library C yang mendasari matematika floating point:

>>>
import math
math.cos(math.pi / 4)
0.70710678118654757
math.log(1024, 2)
10.0
