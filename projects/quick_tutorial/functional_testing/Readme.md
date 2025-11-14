Analysis
Pada tahap ini, implementasi pengujian fungsional end-to-end yang memanfaatkan WebTest telah berhasil dirampungkan. Hasil yang didapat mengonfirmasi bahwa metode pengujian ini dapat dieksekusi secara bersamaan (simultan) dengan unit test standar (via pytest), dengan semua keluaran laporan (output) yang terkonsolidasi secara rapi.

Extra Credit
Penggunaan notasi b'' (byte literal) dalam functional test diperlukan karena res.body (isi respons) mengembalikan data dalam format bytes, bukan string (teks) biasa. Apabila perbandingan dilakukan menggunakan string standar (tanpa prefix b''), akan terjadi error karena adanya ketidakcocokan tipe data (membandingkan bytes dengan string).