---
title: Pertemuan 2 Mata Kuliah Pengantar Komputasi Modern
description: Rangkuman materi tentang Map Reduce, NoSQL dan Quantum Computation
category : tugas kuliah
---

# Map Reduce
MapReduce merupakan model pemrograman untuk memproses data berukuran besar secara terdistribusi dan paralel dalam cluster yang terdiri atas ribuan komputer

## Map
Proses Map yaitu mengumpulkan informasi dari potongan - potongan data dari komputer - komputer yang saling terhubung.

## Reduce
Hasil dari proses Map di arakhkan ke proses Reduce yaitu mengirimkan hasil akhr kepada pengguna.

## produk
- Apache Hadoop
- Pig
- Cascading
- Microsoft Dryad
- IBM MapReduce Tool for   Eclipse  
- Skynet
- CouchDB

# NoSQL
NoSQL adalah sebuah konsep mengenai penyimpanan data non-relasional. NoSQL sangat berguna pada data-data yang terus-menerus berkembang, dimana  data tersebut sangat kompleks sehingga sebuah database relational tidak lagi bisa mengakomodir

- Kelebihan NoSQL

NoSQL bisa menampung data yang terstruktur, semi terstruktur dan tidak terstuktur secara efesien dalam skala besar.
Menggunakan OOP dalam pengaksesan atau manipulasi datanya.
jika database noSQL di jalankan di cluster server (multiple server) maka data akan tersebar secara otomatis dan merata keseluruh server

- Kekurangan NoSQL

Hostingnya mahal. beberapa layanan di luar negeri mencharge biaya 100-200USD untuk hosting database noSQL
Sulitnya mencari hosting Cpanel yang mendukung database MongoDB atau database noSQL lainnya


## CouchDB
CouchDB yang dikembangkan oleh Apache lebih dulu muncul jauh sebelum mongoDB yaitu pada tahun 2005. CouchDB tidak menyimpan datanya dalam tabel melainkan dalam dokumen seperti halnya mongoDB.
Basis data ini juga merupakan proyek open source serta dikembangkan dalam bahasa pemrograman Erlang oleh karena itu kita bisa ikut berkontribusi dalam pengembangan CouchDB agar basis data ini lebih baik.

![couchdb]({{site.url}}/assets/images/couchdb.jpg)

## Cassandra
Cassandra merupakan sebuah sistem penyimpanan data terdistribusi untuk menangani jumlah data yang sangat besar dan terstruktur. Cassandra juga dikembangkan Apache.

Cassandra juga merupakan aplikasi open source yang ditulis dalam bahasa Java dengan lisensi Apache License 2.0.

Untuk memproses datanya, Cassandra menggunakan bahasa sendiri yang mirip dengan SQL yaitu Cassandra Query Language (CQL).

![cassandra]({{site.url}}/assets/images/cassandra.jpg)

## MongoDB

MongoDB merupakan basis data yang paling populer diantara basis data NoSQL lainnya. Hal ini dikarenakan pemasangan maupun penggunaan mongoDB tidaklah sulit atau merepotkan penggunanya. Selain itu mongoDB juga merupakan salah satu basis data yang open source.
MongoDB merupakan basis data NoSQL yang document based. Ia menyimpan data-datanya dalam suatu dokumen JSON yang disebut BSON (Binary JSON).
Dikembangkan sejak tahun 2009, mongoDB sekarang telah mendukung hampir semua bahasa pemrograman untuk dapat berinteraksi dengan mongoDB.

![mongodb]({{site.url}}/assets/images/mongodb.jpg)

## Riak
Riak merupakan basis data NoSQL terdistribusi yang menyimpan datanya dalam bentu key-value. Riak menawarkan fitur high availability, fault tolerance, operational simplicaity, dan scalability.

Riak memiliki dua versi yakni Open source edition dan Enterprise edition. Enterprise edition menawarkan dukungan berbayar intensif dari pengembangnya. Pengguna Open source edition dapat bermigrasi kapan saja ke Enterprise edition jika dibutuhkan. Erlang ditulis dalam bahasa pemrograman Erlang dengan lisensi Apache License 2.0

![riak]({{site.url}}/assets/images/riak.jpg)


## Redis
Redis merupakan basis data berbasis key-value. Redis merupakan singkatan dari REmote DIctionary Server. Basis data ini dikembangkan oleh Salvatore Sanfilippo pada tahun 2009 dan ditulis dalam bahasa C. Redis banyak dipilih karena memiliki fitur in-memory, networked, dan durabilitas tinggi.

Redis mendukung banyak bahasa pemrograman seperti ActionScript, C/C++, C#, Clojure, Common LIsp, Dart, Erlang, Go, Haskell, Haxe, Io, Java, JavaScript (Node.js), Lua, Objective-C, Perl, PHP, Pure Data, Python, R, Ruby, Scala, Smalltalk, dan Tcl.

![redis]({{site.url}}/assets/images/redis.jpg)

# Quantum Computation

Quantum computation atau komputasi quantum merupakan sebuah perhitungan yang menggunakan kuantum mekanika fenomena yang dilakukan untuk melakukan operasi data


## Entaglement
Entanglement adalah suatu teori mekanika quantum yang menggambarkan seberapa cepat dan betapa kuatnya keterhubungan partikel-partikel pada Quantum computer yang dimana jika suatu partikel diperlakukan “A” maka akan memberikan dampak “A” juga ke partikel lainnya


## Quantum Gates
Quantum gates merupakan gerbang dari kuantum yang berfungsi mengoperasikan bit yang terdiri dari 0 dan 1 juga dalam qubits sehingga proses yang terjadi lebih cepat, karena setiap perhitungan dilakukan secara bersamaan

![quantumgates]({{site.url}}/assets/images/quantumgates.jpg)

## Pengoperasian Data Qubit
Dalam komputer kuantum, sejumlah partikel elemental seperti elektron atau foton dapat digunakan yang  bertindak sebagai representasi dari 0 dan  1. Setiap partikel-partikel ini dikenal sebagai qubit, sifat dan perilaku partikel-partikel ini membentuk dasar dari komputasi kuantum.
Namun dalam mekanika quantum, objek apapun yang memiliki dua status berbeda pasti memiliki rangkaian status potensial, disebut superposisi, yang menjerat kedua status hingga derajat bermacam-macam.
![Entaglement]({{site.url}}/assets/images/entaglement.jpg)


## Algoritma Shor

Inti dari algoritma ini merupakan bagaimana cara menyelesaikan faktorisasi terhaadap bilanga interger atau bulat yang besar.

Algoritma Shor terdiri dari dua bagian:
- Penurunan yang bisa dilakukan pada komputer klasik, dari masalah anjak untuk masalah ketertiban - temuan.
- Sebuah algoritma kuantum untuk memecahkan masalah order-temuan
