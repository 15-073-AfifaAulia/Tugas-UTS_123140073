Analysis
Pada tahap ini saya sudah berhasil membuat functional test end-to-end menggunakan WebTest. Hasil pengujian menunjukkan bahwa pendekatan ini bisa dijalankan bersamaan dengan unit test biasa menggunakan pytest, dan hasilnya tetap ditampilkan dalam satu output yang rapi.
Keunggulannya, functional test ini bisa menguji keseluruhan proses dari request sampai response (termasuk template HTML) tanpa perlu menjalankan server sungguhan. Selain itu, waktu eksekusinya juga tetap cepat, jadi masih efisien untuk digunakan dalam proses TDD (Test-Driven Development).

Extra Credit – Kenapa functional test pakai b''
Functional test memakai b'' karena objek res.body yang dikembalikan oleh WebTest berupa byte string, bukan string biasa (str). Jadi, untuk membandingkan isi response dengan teks HTML yang diharapkan, datanya juga harus dalam bentuk bytes. Kalau pakai string biasa tanpa b, hasil perbandingan bakal error karena tipe datanya beda.