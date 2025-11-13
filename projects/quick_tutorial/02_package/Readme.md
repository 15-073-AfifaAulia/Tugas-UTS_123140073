Struktur Unit Test (tutorial/tests.py)
Kita gunakan framework unittest standar Python dan bantuan dari pyramid.testing untuk mempermudah testing fungsi view Pyramidnya.

import unittest
from pyramid import testing

class TutorialViewTests(unittest.TestCase):
    # Setup dan Teardown disiapkan untuk testing yang lebih kompleks
    def setUp(self):
        self.config = testing.setUp()
    def tearDown(self):
        testing.tearDown()

    def test_hello_world(self):
        from tutorial import hello_world # Import lokal
        request = testing.DummyRequest() # Membuat permintaan palsu
        response = hello_world(request) # Memanggil view
        self.assertEqual(response.status_code, 200) # Memeriksa hasil