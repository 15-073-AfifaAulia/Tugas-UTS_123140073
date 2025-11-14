Analysis
Pada langkah ini, saya mempelajari dasar-dasar unit test (uji unit) di Python untuk memastikan bahwa setiap komponen kecil kode berfungsi seperti yang diharapkan. Pyramid sendiri terbukti sangat mendukung proses pengujian, bahkan menyediakan helper (pembantu) seperti pyramid.testing untuk mempermudah pembuatan konfigurasi tiruan (dummy) serta request tiruan.

Saya menggunakan pytest sebagai test runner (pelaksana tes). Alasan pemilihannya adalah karena pytest lebih simpel, menghasilkan output yang rapi, dan saat ini telah menjadi standar de facto (standar tidak resmi) di komunitas Python.

Dalam contoh ini, saya membuat satu test sederhana yang:
1. Memanggil view hello_world.
2. Membuat request palsu menggunakan testing.DummyRequest().
3. Menguji apakah status code dari response adalah 200.

Extra Credit
1. Jika assertion diubah menjadi 404: Apabila pengujian diubah menjadi self.assertEqual(response.status_code, 404), maka pytest akan gagal (error). Output di terminal akan menunjukkan AssertionError, karena nilai yang diharapkan (404) tidak cocok dengan nilai aktual yang diterima (200).
2. Jika ada error di kode view: Jika saya menambahkan kode yang jelas salah (misalnya x = not_defined_variable) ke dalam fungsi view dan menjalankan pytest, error (NameError) akan langsung muncul di terminal. Ini menghemat waktu debugging secara signifikan karena saya mendapatkan umpan balik instan tanpa perlu menjalankan server dan membuka browser.
3. Jika view sengaja diubah: Sebagai contoh, jika view diubah menjadi:
from pyramid.response import Response
def hello_world(request):
    return Response('Hi', status=404)
Saat pytest dijalankan, test akan gagal karena nilai status aktual adalah 404 (bukan 200). Ini membuktikan bahwa testing membantu menegakkan "kontrak" kode—memastikan bahwa perilaku yang diharapkan (misalnya, "view ini harus mengembalikan 200 OK") tetap konsisten.
4. Pengujian response.body: Untuk menguji isi dari body respons (contoh: self.assertIn(b'<h1>Hello</h1>', response.body)), kita harus menggunakan bytestring (string dengan prefix b''). Ini karena response.body secara default mengembalikan data dalam format bytes, bukan string teks biasa.
5. Alasan import di dalam fungsi test: Alasan import (misalnya import view) dilakukan di dalam fungsi test alih-alih di bagian atas file adalah untuk isolasi:
- Import di level modul dapat memicu side effects (efek samping), seperti memuat konfigurasi Pyramid, menjalankan inisialisasi modul, atau memanggil fungsi lain.
- Dengan mengimpor di dalam fungsi test, kita memastikan setiap test berjalan secara terisolasi dan tidak saling memengaruhi.
- Ini menjaga test tetap murni sebagai "unit", memastikan hanya kode yang relevan yang berjalan dalam lingkup test tersebut.
