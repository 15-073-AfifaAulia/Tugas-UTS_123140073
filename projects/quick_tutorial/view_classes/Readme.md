Analysis
Pada tahap ini saya belajar menggunakan templating system supaya kode Python tidak lagi bercampur langsung dengan HTML. Dengan menambahkan dependensi pyramid_chameleon, kini tampilan HTML bisa dipisahkan ke file .pt, sementara fungsi view hanya mengembalikan data berupa dictionary.
Pendekatan ini bikin kode jadi lebih bersih dan mudah dibaca, karena setiap bagian punya tanggung jawab yang jelas — logika di Python, tampilan di template. Selain itu, saat testing pun jadi lebih sederhana, karena pengujian cukup fokus pada data yang dikembalikan view, bukan lagi memeriksa isi HTML secara langsung.
Dekorator @view_config juga bisa dikombinasikan dengan parameter renderer, jadi kita nggak perlu bikin Response secara manual. Hal ini mempermudah integrasi antara kode Python dan template HTML.

Extra Credit
- Kenapa Pyramid mendukung banyak templating engine? Karena Pyramid punya konsep replaceability. Framework ini tidak memaksa developer untuk pakai satu sistem tertentu. Jadi, kita bisa pilih engine seperti Chameleon, Jinja2, atau Mako sesuai preferensi tim atau kebutuhan proyek.
- Apa keuntungan view mengembalikan data, bukan HTML langsung? Dengan begitu, kode jadi lebih fleksibel dan bisa diuji lebih mudah. Jika suatu saat mau ganti template, view-nya tidak perlu diubah karena yang dikembalikan hanyalah data. Template-lah yang bertugas menampilkan hasil akhirnya.