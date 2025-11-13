Analysis
Pada tahap ini saya sudah memisahkan kode view dari __init__.py ke file baru views.py, lalu menggunakan @view_config sebagai cara declarative configuration. Dengan begitu, kode startup jadi lebih ringkas dan rapi karena view tidak dicampur dengan konfigurasi aplikasi.
Sekarang saya punya dua view (home dan hello) yang saling terhubung lewat link. Keduanya diuji menggunakan pytest dan hasilnya semua test berhasil. Pendekatan ini juga menunjukkan bahwa nama view, route, dan URL bisa berbeda satu sama lain tergantung konfigurasi.

Extra Credit
1. Apa arti tanda titik pada .views?
Tanda titik (.) pada config.scan('.views') menunjukkan bahwa file views.py berada di dalam package yang sama dengan __init__.py. Jadi . itu artinya relative import path dari modul saat ini (tutorial), bukan path absolut.
2. Kenapa assertIn lebih baik dari assertEqual?
assertIn lebih fleksibel karena hanya memeriksa apakah potongan teks tertentu ada di dalam response body, bukan harus sama persis dengan seluruh HTML. Ini membantu kalau nanti ada tambahan atribut HTML atau whitespace yang tidak memengaruhi hasil test, jadi test tetap valid dan tidak mudah gagal hanya karena detail kecil.