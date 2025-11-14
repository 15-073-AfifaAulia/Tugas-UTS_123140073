Analysis
Pada tahap ini, fokus pembelajaran beralih ke cara Pyramid menangani HTML menggunakan template, sebagai pengganti metode hardcoding HTML langsung di dalam kode Python.

Metode sebelumnya (hardcoding) diakui masih valid, namun sangat tidak praktis dan sulit dirawat (unmaintainable) untuk aplikasi yang berkembang. Pyramid sendiri tidak membatasi (agnostik) pada satu templating engine tertentu. Dalam latihan ini, pyramid_chameleon digunakan karena dokumentasinya yang ringan dan proses integrasi yang mulus.

Sebuah observasi penting adalah bagaimana kedua view (home dan hello) dapat memanfaatkan template yang sama, hanya dengan melewatkan data yang berbeda. Hal ini menunjukkan bagaimana template mendorong reusability (penggunaan kembali) dan modularitas kode.

Untuk alur kerja pengembangan, penambahan pyramid.reload_templates = true di dalam development.ini terbukti sangat bermanfaat. Pengaturan ini memungkinkan pembaruan pada file template agar langsung terlihat di browser tanpa perlu me-restart server.

Pola pengujian juga mengalami adaptasi. Karena view kini mengembalikan dictionary (berisi data untuk template), unit test dapat difokuskan untuk memvalidasi isi dictionary tersebut secara langsung, tanpa perlu melakukan parsing HTML. Sementara itu, tanggung jawab untuk memastikan HTML akhir telah di-render dengan benar dan berisi teks yang sesuai, kini ditangani oleh functional test.