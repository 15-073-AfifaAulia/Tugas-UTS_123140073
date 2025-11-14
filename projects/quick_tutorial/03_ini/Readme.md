Analysis
Pada langkah ini, pembelajaran berfokus pada bagaimana Pyramid memisahkan konfigurasi dari kode aplikasi, dan bagaimana file .ini memegang peran sentral dalam mengatur aplikasi tanpa perlu mengubah kode Python secara terus-menerus.
1. File .ini untuk Inisialisasi Aplikasi: Perintah pserve development.ini --reload digunakan untuk mem-boot aplikasi. pserve akan membaca bagian [app:main] di dalam file itu, menemukan arahan use = egg:tutorial, dan kemudian mencari entry point (titik masuk) bernama tutorial:main yang telah didefinisikan di setup.py.
2. Entry Point (setup.py) sebagai Penunjuk Lokasi: Entry point di setup.py bertindak sebagai "petunjuk" yang memberitahu Pyramid di mana lokasi pabrik (factory) aplikasi WSGI berada (dalam hal ini, fungsi main()).
3. Pemindahan Kode Startup: Kode inisialisasi aplikasi kini dipindahkan ke fungsi main() yang terletak di tutorial/__init__.py. Fungsi main() ini berisi logika inti:
- Inisialisasi Configurator.
- Definisi route dan view.
- Pembuatan aplikasi WSGI.
4. Pengaturan Server dan Logging: File .ini juga bertanggung jawab mengonfigurasi server WSGI (melalui bagian [server:main], yang menentukan penggunaan Waitress dan port-nya) serta mengelola konfigurasi logging, yang menghasilkan output konsol yang lebih rapi.
5. Manfaat --reload: Opsi --reload sangat vital untuk pengembangan (development). Fitur ini membuat server otomatis restart setiap kali ada perubahan pada file Python atau .ini, sehingga tidak perlu melakukan stop-start server secara manual.

Extra Credit
1. Menjalankan Tanpa .ini: Ya, sangat bisa. Seperti yang dipelajari di tahap sebelumnya, kita dapat membuat Configurator, menghasilkan aplikasi WSGI, dan menjalankan Waitress secara programatik hanya menggunakan kode Python murni tanpa bergantung pada file .ini.
2. Multiple .ini Files: Ya, bisa. Ini adalah praktik umum untuk mengelola lingkungan yang berbeda, misalnya:
- development.ini (Debug on, toolbar aktif, logging verbose)
- production.ini (Debug off, logging minim, konfigurasi server berbeda)
- testing.ini (Setting khusus untuk unit/functional test)
3. Makna tutorial:main: Ini adalah notasi standar Python (yang digunakan oleh Setuptools) untuk merujuk ke sebuah objek di dalam sebuah package. Formatnya adalah package_name:object_name. Dalam konteks ini, tutorial:main berarti "gunakan objek main (sebuah fungsi) yang berada di dalam package tutorial".
4. Makna **settings: Notasi ** (dua bintang) dalam **settings adalah sintaks Python untuk dictionary unpacking (membongkar kamus). Ini berarti semua pasangan key-value yang ada di dalam dictionary (kamus) bernama settings akan diteruskan sebagai keyword arguments individual ke dalam fungsi tersebut.