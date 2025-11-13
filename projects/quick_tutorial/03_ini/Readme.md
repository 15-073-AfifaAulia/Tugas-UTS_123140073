Konsep Kunci Testing

- pyramid.testing.DummyRequest() yaitu permintaan palsu yang dibuat Pyramid. Yang mana objek ini meniru semua yang ada dalam permintaan HTTP yang sebenarnya, tetapi tanpa perlu server berjalan. Yang mana bisa gunakan ini untuk memanggil fungsi view kita secara langsung.

- Pengujian Kontrak fungsi hello_world yang akan mengembalikan respons HTTP yang sukses atau berhasil. Test kita (self.assertEqual(response.status_code, 200)) memastikan "kontrak" ini terpenuhi atau tidak.

- Impor di Dalam Test (Kredit Tambahan)
* Kita sengaja mengimpor from tutorial import hello_world di dalam metode test_hello_world supaya tetap tetap terisolasi.