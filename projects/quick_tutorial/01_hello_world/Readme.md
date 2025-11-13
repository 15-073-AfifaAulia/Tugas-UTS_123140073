. Instalasi dan Persiapan
Kita menambahkan pytest ke dalam dependensi pengembangan (dev), sama seperti pyramid_debugtoolbar.
- Perintah setup.py yaitu menambahkan 'pytest' ke daftar dev_requires fungsinya memastikan pytest hanya diinstal untuk lingkungan pengembangan.
- Perintah yaitu $VENV/bin/pip install -e ".[dev]" fungsinya tu menginstal package kita bersama semua alat pengembangan, termasuk pytestnya.
- Perintah yaitu $VENV/bin/pytest tutorial/tests.py -q di mana fungsinya tu untuk menjalankan test kita. 