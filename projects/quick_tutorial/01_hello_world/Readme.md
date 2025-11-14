Analisis
Pada tahap pertama ini, fokus pembelajaran adalah mengeksekusi aplikasi Pyramid dalam bentuk paling minimalis, yaitu hanya menggunakan satu file Python. Tujuannya adalah untuk memahami secara mendalam mekanisme "di balik layar" sebelum beralih ke struktur proyek yang lebih kompleks.

- Poin-poin kunci yang dipelajari:
- Penggunaan if __name__ == '__main__': sebagai titik awal (entry point) eksekusi program.
- Peran Configurator sebagai pusat pengaturan utama aplikasi Pyramid.
- Fungsi view (view function) bertugas menghasilkan objek Response.
- Waitress digunakan sebagai server untuk menjalankan aplikasi berstandar WSGI.
- Pyramid terbukti fleksibel, dapat digunakan untuk aplikasi yang sangat sederhana maupun skala besar.

Extra Credit
1. Sintaks print (Python 2 vs Python 3): Alasan menggunakan print('Incoming request') (dengan tanda kurung) adalah karena ini sintaks fungsi yang valid dan wajib di Python 3. Sebaliknya, print 'Incoming request' (tanpa tanda kurung) adalah sintaks lama dari Python 2. Karena Pyramid dan ekosistem modern berjalan di Python 3, penggunaan sintaks Python 2 akan langsung menyebabkan SyntaxError.
2. Tipe Data yang Dikembalikan (Return) oleh View: Jika sebuah view mengembalikan string HTML atau sequence integer: Pyramid dan Python 3 mengharapkan objek Response atau data lain yang dapat diadaptasi (dikonversi) menjadi body HTTP dengan encoding tertentu. Web server (WSGI) tidak tahu cara mengubah tipe data arbitrer seperti integer menjadi payload HTTP. Standar WSGI mengharuskan body respons berupa bytestring yang iterable, bukan integer.
3. Efek Kode Invalid dalam View: Jika kode yang sengaja disalahkan (misalnya print xyz) dimasukkan ke view function, kemudian server dihentikan (Ctrl+C) dan dijalankan ulang: Saat browser di-reload untuk mengakses view tersebut, terminal (konsol) akan segera menampilkan traceback lengkap. Ini terjadi karena xyz tidak terdefinisi (NameError), dan error ini muncul sebelum view sempat mengembalikan Response. Hal ini menunjukkan bahwa semua error Python standar akan langsung terlihat di konsol saat aplikasi dijalankan dengan python app.py.
4. Asal Mula WSGI (Gateway Interface): WSGI (dimana "GI" adalah "Gateway Interface") dimodelkan berdasarkan standar yang lebih tua, yaitu CGI (Common Gateway Interface). CGI dulu jamak digunakan untuk menjalankan skrip server-side (seperti Perl, Python, dll.), namun memiliki kelemahan besar: performanya lambat karena harus membuat proses sistem operasi baru untuk setiap request yang masuk. WSGI adalah versi modern yang jauh lebih efisien dan "Pythonic" (sesuai idiom Python) untuk tugas yang sama.