
#REST API
REST API merupakan implementasi dari API (Application Programming Interface). REST (Representional State Transfer) adalah suatu arsitektur metode komunikasi yang menggunakan protokol HTTP untuk pertukaran data dan metode ini sering diterapkan dalam pengembangan aplikasi. Dimana tujuannya adalah untuk menjadikan sistem yang memiliki performa yang baik, cepat dan mudah untuk di kembangkan (scale) terutama dalam pertukaran dan komunikasi data.

RESTful API memiliki 4 komponen penting di dalamnya diantaranya adalah

URL Design
HTTP Verbs
HTTP Response Code
Format Response
URL Design
RESTful API diakses menggunakan protokol HTTP. Penamaan dan struktur URL yang konsisten akan menghasilkan API yang baik dan mudah untuk dimengerti developer. URL API biasa disebut endpoint dalam pemanggilannya. Contoh penamaan URL / endpoint yang baik adalah seperti berikut :

/users
/users/1234
/users/1234/photos
/users/1234/photos/abc


#WSGI


Web Server Gateway Interface
untuk membuat standard interface antara web aplikasi yang dibuat
dengan python dengan web server.
WSGI mempunyai dua sisi:

sisi server
aplikasi / framework
WSGI pada dasarnya hanya sebuah referensi interface yang harus
diimplementasi baik oleh server maupun oleh applikasi, sehingga
sebuah applikasi yang mengimplementasi wsgi dapat di-deploy,
diserver mana saja asalkan server itu juga mengimplementasi WSGI
interface.

Ini dapat dibandingkan dengan dunia java, dimana banyak terdapat web
framework, akan tetapi web framework itu bisa diapplikasikan di java
web server mana saja, karena baik web framework maupun java web
server mengimplentasi JavaEE interface yang salah satunya adalah
servlet.

Cara Kerja WSGI
Server berhubungan dengan applikasi dengan memanggil sebuah callable
(baik itu fungsi maupun object) yang disediakan oleh
applikasi. callable itu mempunyai dua buah argumen yaitu environ dan
start_response. Environ berupa python dictionary sedangkan
start_response berupa fungsi.

Sedangkan applikasi berhubungan dengan server, dengan mengirimkan
header (dapat diartikan sebagai http header), dan memanggil
start_response dan memberi argumen http response dan http header,
kemudian mengembalikan list python yang berisi response. Agak
membingunkan bila cuma membaca spesikasi, akan lebih mudah bila kita
melihat contohnya

 def application(environ, start_response):
    "Contoh Sederhana dari WSGI Application"
    status = "200 OK"
    headers = [("Content-type","plain/text")]
    start_response(status,headers)
    return ['Hello world !\n']

dari contoh diatas, bisa kita lihat bagaimana applikasi berhubungan
dengan server, dimana applikasi mengirimkan status dan header dengan
menggunakan fungsi start_response, dan mengembalikan body response
kepada server.

Middleware
Yang dimaksud dengan middleware, adalah sebuah komponen python, yang
mempunyai dua fungsi sebagai server, sekaligus sebagai
applikasi. Pada awalnya memang membuat bingung, bagaimana bisa
sebuah component dapat berfungsi sebagai server sekaligus sebagai
aplikasi?.
Jadi bila sebuah komponen berfungsi sebagai middleware, maka dia
bertindak sebagai penengah/buffer/pembungkus dari applikasi
lain. Jadi server tidak akan memanggil fungsi dari wsgi dari
aplikasi,akan tetapi memanggil fungsi wsgi dari komponen middleware,
yang nantinya akan memanggil fungsi wsgi dari applikasi.
Middleware itu sendiri bisa merubah keluaran dari applikasi,
melakukan routing dan berbagai macam hal lainnya.
Contoh code dari Middleware

class Upperware:
   def __init__(self, app):
      self.wrapped_app = app

   def __call__(self, environ, start_response):
      for data in self.wrapped_app(environ, start_response):
         return data.upper()



#GEVENT
#FALCON API
#FLASK
