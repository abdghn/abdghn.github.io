---
title: Belajar Nest JS Part 1
description: Mempelajari atau Berkenalan terlebih dahulu dengan Nest JS
---
> Nest is a framework for building efficient, scalable Node.js server-side applications. It uses progressive JavaScript, is built with TypeScript (preserves compatibility with pure JavaScript) and combines elements of OOP (Object Oriented Programming), FP (Functional Programming), and FRP (Functional Reactive Programming).
Under the hood, Nest makes use of Express, but also provides compatibility with a wide range of other libraries (e.g. Fastify). This allows for easy use of the myriad third-party plugins which are available.


Untuk melakukan instalasi, saya menggunakan git

```
git clone https://github.com/nestjs/typescript-starter.git project
cd project
npm install
npm run start
```

or


```
npm i -g @nestjs/cli
nest new nest-restaurant-api
npm run start:dev
```

setelah di clone, otomatis membuat template dari Nets JS. kemudian setelah run di terminal dapat membuka di browser localhost:3000 maka muncul output seperti gambar di bawah ini


kemudian untuk menghubungkan database MongoDB dengan mongoose, buat folder database di dalam folder src

```
src
  database
    database.module.ts
    database.providers.ts
```

setelah buka file database.module.ts dan isikan kode dibawah ini

```javascript
import * as mongoose from 'mongoose';
import { DB_PROVIDER } from '../constants';

export const databaseProviders = [
    {
        provide: DB_PROVIDER,
        useFactory: async () => {
            (mongoose as any).Promise = global.Promise;
            return await mongoose.connect('mongodb://localhost:27017/parley');
        },
    },
];
```

pada {DB_PROVIDER} module yang dipanggil tidak ada, buat file constants.ts

```javascript
export const DB_PROVIDER = 'DbConnectionToken';
```

setelah berhasil menghubungkan MongoDB dengan Nest JS, install MongoDB dengan perintah
```
npm i --save mongoose
npm i --save-dev
```


setelah itu untuk mengakses alamat MongoDB yaitu mongodb://localhost:27017/parley dan otomatis membuat database dengan nama parley.


Kemudian definisikan database ke modul di dalam file database.module.ts

```javascript
import { Module } from '@nestjs/common';
import { databaseProviders } from './database.providers';

@Module({
    components: [...databaseProviders],
    exports: [...databaseProviders],
})
export class DatabaseModule { };
```

setelah itu baru kita bisa menarik database modul di dalam modul2 lain dan menggunakan mongoose untuk menghubungkan objek untuk dijalankan query nya di database.

# Post module
Kemudian mendesain app nya pendekatan dari entitas berbasis modular. Untuk membuat direktori modul pertama di dalam  direktori src.

```
src
  -posts
    --dto
      ---create-post.dto.ts
    --interfaces
      --post.interface.ts
    --posts.controller.ts
    --posts.module.ts
    --posts.providers.ts
    --posts.schema.ts
    --posts.service.ts
```


pada dto kita mendefinisikan struktur data untuk API endpoint. Ketika membuat

```javascript
export class CreatePostDto {
    readonly title: string;
    readonly content: string;
    readonly userId: string;
}
```

kemudian kita membuat post interface di posts.interface.ts

```javascript
import { Document } from 'mongoose';

export interface Post extends Document {
    readonly title: string;
    readonly content: string;
    readonly userId: string;
}
```
ketika sudah membuat 2 file diatas sekarang membuat post service pada posts.service.ts. Untuk postService membuat komponen kelas konstruktor , untuk menginjeksi dimana Nest JS melakukan depedency injection.

```javascript
import { Model } from 'mongoose';
import { Component, Inject } from '@nestjs/common';

import { Post } from './interfaces/post.interface';
import { CreatePostDto } from './dto/create-post.dto';
import { POST_MODEL_PROVIDER } from '../constants';

@Component()
export class PostsService {
    constructor(
        @Inject(POST_MODEL_PROVIDER) private readonly postModel: Model<Post>) { }

    async create(createPostDto: CreatePostDto): Promise<Post> {
        const createdPost = new this.postModel(createPostDto);
        return await createdPost.save();
    }

    async findAll(): Promise<Post[]> {
        return await this.postModel.find().exec();
    }
}
```

Di dalam provider, membangun mongoose model dan injeksi model. Untuk membuat model, kita harus mendefiniskan skema pada file posts.schema.ts

```JavaScript
import * as mongoose from 'mongoose';

export const PostSchema = new mongoose.Schema({
    title: {
        type: String,
        required: true,
    },
    content: {
        type: String,
        required: false,
    },
    userId: {
        type: mongoose.SchemaTypes.ObjectId,
        required: true,
    }
});
```
# Kegunaan pada file src
app.controller.ts and app.service.ts: those files are responsible for generating the message Hello world when the endpoint / is accessed through the browser. Because this endpoint is not important to this application you may delete these files as well. Soon you are going to learn in more details what controllers and services are.
app.module.ts: this is a class of the type module that is responsible for declaring imports, exports, controllers, and providers to a Nest.js application. Every application has at least one module but you may create more than one module for more complex applications (more details on Nest.js documentation). The application of this tutorial will have only one module.
main.ts: this is the file responsible for starting the server.
main.hrm.ts: is a Hot Module Replacement file that installs modules during the server execution and it is useful to speed up the development process.


# Penjelasan REST API
>RESTful API / REST API merupakan implementasi dari API (Application Programming Interface). REST (Representional State Transfer) adalah suatu arsitektur metode komunikasi yang menggunakan protokol HTTP untuk pertukaran data dan metode ini sering diterapkan dalam pengembangan aplikasi. Dimana tujuannya adalah untuk menjadikan sistem yang memiliki performa yang baik, cepat dan mudah untuk di kembangkan (scale) terutama dalam pertukaran dan komunikasi data

![post]({{site.url}}/assets/images/.png)



URL Design
RESTful API diakses menggunakan protokol HTTP. Penamaan dan struktur URL yang konsisten akan menghasilkan API yang baik dan mudah untuk dimengerti developer. URL API biasa disebut endpoint dalam pemanggilannya. Contoh penamaan URL / endpoint yang baik adalah seperti berikut :

/users
/users/1234
/users/1234/photos
/users/1234/photos/abc
HTTP Verbs
Setiap request yang dilakukan terdapat metode yang dipakai agar server mengerti apa yang sedang di request client, diantaranya yang umum dipakai adalah :

GET
GET adalah metode HTTP Request yang paling simpel, metode ini digunakan untuk membaca atau mendapatkan data dari sumber.
Contoh :
GET /users : Mengembalikan daftar user
GET /users/1234 : Mengembalikan data user dengan ID 1234

POST
POST adalah metode HTTP Request yang digunakan untuk membuat data baru dengan menyisipkan data dalam body saat request dilakukan.
Contoh :
POST /users : Membuat data user baru

PUT
PUT adalah metode HTTP Request yang biasanya digunakan untuk melakukan update data resource.
Contoh :
PUT /users/1234 : Mengupdate data user dengan ID 1234

DELETE
DELETE adalah metode HTTP Request yang digunakan untuk menghapus suatu data pada resource.
Contoh :
DELETE /users/1234 : Menghapus data user dengan ID 1234

Selain HTTP Verbs diatas, masih ada metode HEAD dan PATCH dalam HTTP Request, tetapi jarang sekali digunakan.

HTTP Response Code
HTTP response code adalah kode standarisasi dalam menginformasikan hasil request kepada client. Secara umum terdapat 3 kelompok yang biasa kita jumpai pada RESTful API yaitu :

2XX : adalah response code yang menampilkan bahwa request berhasil.
4XX : adalah response code yang menampilkan bahwa request mengalami kesalahan pada sisi client.
5XX : adalah response code yang menampilkan bahwa request mengalami kesalahan pada sisi server.

Dan berikut ini adalah response code yang biasa digunakan pada REST :

200 OK
Response code ini menandakan bahwa request yang dilakukan berhasil.

201 Created
Response code ini menandakan bahwa request yang dilakukan berhasil dan data telah dibuat. Kode ini digunakan untuk mengkonfirmasi berhasilnya request PUT atau POST.

400 Bad Request
Response code ini menandakan bahwa request yang dibuat salah atau data yang dikirim tidak ada.

401 Unauthorized
Response code ini menandakan bahwa request yang dibuat membutuhkan authentication sebelum mengakses resource.

404 Not Found
Response Code ini menandakan bahwa resource yang di dipanggil tidak ditemukan.

405 Method Not Allowed
Response code ini menandakan bahwa request endpoint ada tetapi metode HTTP yang digunakan tidak diizinkan.

409 Conflict
Response code ini menandakan bahwa request yang dibuat terdapat duplikasi, biasanya informasi yang dikirim sudah ada sebelumnya.

500 Internal Server Error
Response code ini menandakan bahwa request yang dilakukan terdapat kesalahan pada sisi server atau resource.

Format Response
Setiap request yang dilakukan client akan menerima data response dari server, response tersebut biasanya berupa data XML ataupun JSON. Setelah mendapatkan data response tersebut barulah client bisa menggunakannya dengan cara memparsing data tersebut dan diolah sesuai kebutuhan.
Contoh :
XML

HTTP/1.1 200 OK
Date: Sat, 06 Oct 2001 23:20:04 GMT
Server: Apache.1.3.12 (Unix)
Connection: close
Content-Type: text/xml
Content-Length: 124

<?xml version=”1.0″?>
<methodResponse>
<params>
<param>
<value><double>18.24668429131</double></value>
</param>
</params>
</methodResponse>
JSON

GET /users/1234

HTTP/1.1 200 OK
Content-Type: application/vnd.api+json

{
“id”: “1234”,
“first_name”: “jhon”,
“last_name”: “doe”,
“created”: “2015-05-22T14:56:29.000Z”,
“updated”: “2015-05-22T14:56:29.000Z”
}
# Penjelasan Tentang Mongoose
Mongoose adalah sebuah Object Document Mapper (ODM). Ini berarti Mongoose mengizinkan Anda untuk mendefinisikan obyek dengan skema yang benar-benar diketik yang dipetakan ke sebuah dokumen MongoDB.

Mongoose menyediakan jumlah fungsionalitas yang luar biasa yang berkaitan dengan pembuatan dan pengerjaan skema. Mongoose saat ini memiliki delapan tipe skema dimana propertinya disimpan seperti saat berada di MongoDB. Diantaranya:

String
Number
Date
Buffer
Boolean
Mixed
ObjectId
Array
Setiap tipe data memungkinkan Anda untuk menentukan:

sebuah nilai default
sebuah fungsi validasi custom
menunjukan field yang dibutuhkan
fungsi get yang memungkinkan Anda untuk memanipulasi data sebelum dikembalikan sebagai obyek
sebuah set fungsi yang memungkinkan Anda untuk memanipulasi data sebelum disimpan ke database
membuat indeks yang memungkinkan data agar ditarik secara lebih cepat
Selanjutnya untuk opsi umum ini, tipe data tertentu memungkinkan Anda untuk menyesuaikan lebih lanjut bagaimana data disimpan dan diambil dari database. Sebagai contoh, sebuah tipe data String juga memungkinkan Anda untuk menentukan pilihan tambahan sebagai berikut:

mengubah menjadi huruf kecil
mengubah menjadi huruf besar
memangkas data sebelum disimpan
regular-expression yang dapat membatasi data yang diizinkan untuk disimpan selama dalam proses validasi
sebuah enum yang dapat menentukan daftar string yang valid
Properti Number dan Date keduanya mendukung penentuan nilai minimal dan maksimal yang diizinkan untuk field tersebut.

Sebagian besar dari delapan jenis data yang diizinkan seharusnya cukup familiar untuk Anda. Namun, ada beberapa pengecualian yang mungkin menjadi pengecualian bagi Anda, seperti Buffer, Mixed, ObjectId, dan Array.

Tipe data Buffer memungkinkan Anda untuk menyipan data biner. Contoh yang umum untuk data biner seperti gambar atau file encodem seperti dokumen PDF.

Tipe data Mixed mengubah properti menjadi field "dapat menjadi apa saja". Field ini menyerupai berapa banyak pengembang yang menggunakan MongoDB karena tidak ada struktur yang jelas. Berhati-hatilah menggunakan tipe data ini karena tipe ini kehilangan banyak fitur hebat yang disediakan oleh Mongoose, seperti validasi data dan pendeteksi perubahan entitas untuk dapat mengetahui secara otomatis dalam memperbarui properti saat menyimpan.

Tipe data ObjectId umumnya menentukan sebuah tautan ke dokumen yang lain di dalam database Anda. Sebagai contoh, jika anda memiliki sebuah koleksi buku dan penulis, dokumen buku kemungkinan berisi sebuah properti ObjectId yang menunjuk ke penulis tertentu dari dokumen.

Tipe data Array memungkinkan anda untuk menyimpan array yang seperti JavaScript. Dengan sebuah tipe data Array, anda dapat melakukan operasi array Javascript yang umum, seperti push, pop, shift, slice, dll.
