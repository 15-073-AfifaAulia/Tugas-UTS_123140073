Analysis
Pada tahap ini, saya mempelajari proses refaktor dari view function (fungsi view) menjadi view class (kelas view) di Pyramid. Tujuan dari perubahan ini bukanlah untuk menambah fungsionalitas baru, melainkan untuk menata struktur kode agar lebih rapi dan skalabel jika aplikasi berkembang menjadi lebih besar.

Awalnya, semua view diimplementasikan sebagai fungsi yang berdiri sendiri. Namun, ketika beberapa view memiliki hubungan logis atau menggunakan konfigurasi yang sama (contohnya, renderer atau template yang sama), akan lebih masuk akal untuk menggabungkan mereka ke dalam satu kelas. Dengan pendekatan view class ini:
- view-view tersebut lebih terorganisir,
- konfigurasi yang berulang bisa dipusatkan di @view_defaults,
- dan kita bisa menyimpan state atau helper melalui __init__.

Perubahan paling besar ternyata ada di bagian unit test. Karena sekarang view bukan fungsi bebas lagi, saya harus membuat instance dari kelas view (TutorialViews(request)) sebelum memanggil metodenya. Sisanya tetap sama seperti sebelumnya. Setelah itu semua test berjalan normal (4 passed) dan aplikasi tetap bisa dijalankan seperti biasa.