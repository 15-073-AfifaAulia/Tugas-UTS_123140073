Extra Credit 
- Ganti Status Code ke 404 hasilnya pasti bakal pytest akan gagal dengan AssertionError. Pesan error akan sangat jelas: 200 is not equal to 404. Yang ngajarin kita cara membaca laporan kegagalan test.
- Masukkan Bug di View hasilnya pasti merusak view (misalnya, kesalahan NameError), menjalankan pytest akan langsung menunjukkan kegagalan dengan traceback lengkap di konsolnya.
- Menguji Body Respons (HTML) hasilnya Untuk menguji konten HTML yang dikembalikan, dan bisa menambahkan assertion ini: self.assertIn(b'Hello World!', response.body)