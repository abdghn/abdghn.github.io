---
title: React VS Angular
description: Mempelajari perbedaan penggunaan pada react & angular 
---

# React
>React is a JavaScript library developed by Facebook to manage the user interface for web applications with ease. One of the main highlights of React is that it helps in creating manageable UI components, which makes it easier to scale large web applications. React works on the concept of Virtual DOM, where it keeps a mirror image of the actual DOM. Whenever a change occurs, React runs a diffing process, identifies the change, and updates it to the actual DOM. The concept of Virtual DOM makes app rendering faster and improves performance.

Dalam sebuah komponen dalam react, terdapat tiga lifecycle berikut:
Inisialisasi / mounting (ketika komponen dibuat/ditambahkan pertama kali pada DOM)
Update / rerender (ketika terdapat perubahan state/prop yang mengakibatkan perubahan pada DOM)
Unmounting (ketika komponen akan dihapus dari DOM)

## DOM (Document Object Model)

dikarenakan javascript dapat berinteraksi dengan HTML
DOM(Document Object Model) adalah model data standar. DOM adalah cara javascript melihat suatu halaman html. DOM adalah sebuah platform dan interface yang memperbolehkan pengaksesan dan perubahan pada konten, struktur, dan style pada sebuah dokumen oleh program dan  script. Istilah HTML DOM mengacu kepada dokumen html. Kasusnya disini ialah konten, struktur, dan style pada dokumen html dapat diakses dan dirubah dengan menggunakan sintaks javascript.
Pada model DOM ini, setiap elemen html dipandang sebagai sebuah object. Setiap object bisa terdiri dari object-object lain, sama halnya dengan dokumen html yang terdiri dari elemen root (elemen <html>), elemen root terdiri dari elemen <head> dan elemen <body>, elemen <body> boleh jadi terdiri dari elemen <a>, <h1>, <p>, dst. Elemen-elemen pada dokumen html membentuk sebuah object document yang merupakan object dari dokumen html itu sendiri. Dibawah ini adalah representasi HTML DOM dalam model pohon:

dom_tree
Kalau dalam pemrograman OOP(Object Oriented Programing), sebuah object memiliki property dan method, begitu juga elemen pada dokumen html ini memiliki property yaitu nilai pada elemen html yang bisa ditetapkan atau dirubah dan method yakni aksi yang dapat dilakukan pada elemen html. Contoh property yang biasa digunakan ialah innerHTML yang digunakan untuk memperoleh atau merubah konten dari elemen html itu sendiri. Kemudian method, contoh misalnya getElementById(“id”) milik object document yang digunakan untuk mengakses elemen html dalam dokumen html berdasarkan id.

## Virtual DOM
Dari pada langsung bekerja dengan DOM secara langsung pada browser, pada virtual DOM kita terlebih dahulu membuat abstraksi DOM dalam bentuk virtual. Sehingga setiap perubahan terhadap struktur dokumen tidak terjadi secara langsung pada permukaan browser, akan tetapi terjadi di dalam memory. Sehingga proses menjadi lebih cepat.

Setelah modifikasi pada Virtual DOM selesai, kita lakukan proses differing untuk membedakan antara struktur tree yang telah dirender sebelumnya pada browser dengan virtual tree yang sudah dibuat. Sehingga akan menghasilkan bagian-bagian yang 'kotor' alias berbeda. Dan hanya bagian yang butuh diubah saja yang kita render ulang.

Proses ini tentu jauh lebih efektif dan lebih cepat dari pada jika kita harus bekerja secara langsung pada DOM yang asli.

Lantas, bagaimana cara implementasinya?
Oke, jawaban ini cukup rumit. Karena secara umum --pada virtual dom-- kita akan menemui dua permasalahan:

Kapan kita harus melakukan render ulang?
Dan bagaimana cara kita untuk mengetahui bagian mana saja yang berubah dari struktur tree yang lama?
Karena jawaban dari dua pertanyaan di atas adalah kunci kenapa Virtual DOM bisa resource-cheap atau lebih cepat. Kalau anda salah dalam menentukan kapan sistem harus melakukan render ulang, maka aplikasi anda akan tidak jelas dan tidak interaktif. Plus bisa menjadi super-lemot jika ternyata aplikasi anda selalu merender ulang padahal proses tersebut sedang tidak diperlukan. Atau pada proses kedua --yaitu proses differing/comparing tree lama dan yang baru--, kalau anda tidak menggunakan algoritma yang efektif dan efisien, maka teknik Virtual DOM yang anda gunakan akan lebih lelet dari pada cara yang konvensional.

## Flux
>Flux adalah konsep pemrograman untuk mengolah data. Pada react hal ini sangat terkait dengan pengelolaan state pada komponen. Flux memberikan banyak manfaat untuk pengolahan data tersebut. Silahkan simak ulasan ini untuk mengetahui fungsi flux pada react.

Flux merupakan konsep pemrograman yang mengatur aliran atau flow dari data. Pada konsep flux data dibuat menjadi uni-directional. Artinnya , seluruh data akan masuk ke dalam satu gerbang yang kemudian baru di distribusikan pada komponen-komponen didalamnya. Ilustrasinnya seperti saat kita masuk ke kelas yang memiliki satu pintu, seluruh siswa harus masuk ke dalam pintu tersebut yang secara otomatis “pintu” itu akan mengenali seluruh siswa yang masuk dan pada ahirnya mereka menuju ke bangku mereka masing-masing.

1.Action , yaitu suatu object yang akan mentrigger aliran data. Actions akan menentukan data yang akan dikirimkan ke store melalui dispatcher. lebih detailnya, action adalah suatu javascript object yang menggunakan property berupa “type”  yang berfungsi untuk memberitahukan kepada dispatcher mengenai data yang harus disimpan pada store. Action ini akan mentrigger perubahan pada suatu komponen namun tidak dapat menspesifikan pada bagian mana yang harus berubah. Reducer merupakan modul yang dapat melakukan hal tersebut.
Dispatcher, yaitu object yang berfungsi layaknya suatu router. Data – data yang tersentral tersebut tentunnya akan dibagikan ke komponen-komponen lain. Disinilah peran dari suatu dispatcher.
Store, tempat untuk menyimpan state dan data-data logical lainnya. State pada store dapat diupdate secara parsial ketika memang dibutuhkan
View, object yang menerima data dari store dan melakukan proses rendering


React nya biasa nya digunakan untuk pengerjaan proyek2 kecil dikarenakan konsep library dimana dapat menentukan yang mau dipakai jadinya tidak banyak pilihan yang tersedia

contoh aplikasi yang menggunakan react : 
- Facebook
- AirBnb
- Uber
- Netflix
- Instagram
- Whatsapp
- Dropbox

### Initialization 
Pada initialization, terdapat 3 methods yang akan dieksekusi yaitu componentWillMount, render dan componentDidMount. Method tersebut dieksekusi sesuai urutan pada gambar di atas dengan urutan dari atas ke bawah.
ComponentWillMount akan dieksekusi paling awal pada saat pertama kali komponen dibuat, sebelum method render dieksekusi.
Render merupakan method yang wajib ada pada setiap komponen pada react. Method ini akan mengembalikan sebuah react element yang merupakan representasi dari DOM komponen.
Setelah method render dieksekusi, selanjutnya componentDidMount akan dieksekusi. Kita dapat mengakses DOM dan memanipulasi DOM atau melakukan proses pengambilan data atau AJAX request pada method ini. Selain itu, jika kita menggunakan JavaScript framework lain seperti jQuery, kita dapat memanggilnya pada method ini.

### Update / rerender

Proses ini merupakan phase dimana komponen akan di-render ulang. Proses render ulang sebuah komponen dapat dipicu dari perubahan props atau state pada komponen tersebut.

Pada gambar di atas terdapat 5 methods yang akan dieksekusi. Method tersebut adalah componentWillReceiveProps, shouldComponentUpdate, componentWillUpdate, render, componenDidUpdate. Urutan eksekusi ditunjukkan pada gambar di atas dengan urutan dari atas ke bawah.
ComponentWillReceiveProps akan dieksekusi ketika terdapat perubahan pada props dan bukan merupakan render komponen yang pertama kali. Method ini dapat digunakan untuk mengubah state sesuai dengan props baru yang diterima. Perubahan state pada method ini tidak akan memicu phase update pada komponen (tidak akan merender komponen).
ShouldComponentUpdate selalu dieksekusi sebelum method render. Method ini merupakan penentu apakah sebuah komponen akan di-render ulang atau tidak. Method shouldComponentUpdate mengembalikan nilai true atau false dengan nilai default adalah true. Jika method ini mengembalikan nilai true, maka komponen akan di-render ulang dan berlaku juga sebaliknya.
ComponentWillUpdate akan dieksekusi jika method shouldComponenUpdate mengembalikan nilai true. Pada method ini, kita tidak dianjurkan untuk mengubah state dengan alasan bahwa method ini digunakan untuk mempersiapkan proses update komponen bukan untuk memicu proses update komponen.
Setelah componentWillUpdate selesai dieksekusi, maka method render akan dieksekusi.
Setelah method render selesai dieksekusi, componentDidUpdate akan dieksekusi. Method ini sama dengan method componentDidMount. Method ini dapat digunakan untuk interaksi dengan DOM setelah komponen selesai di-render.
Unmounting
Pada proses unmounting hanya ada satu method yang akan dieksekusi yaitu componentWillUnmount. Method ini akan dieksekusi sebelum komponen dihapus atau dihilangkan dari DOM.
Implementasi Kode
Setelah memahami component lifecycle, untuk lebih memahami setiap phase dari component lifecycle, saya telah membuat kode yang akan menunjukkan urutan eksekusi method pada setiap phase.
Implementasi dengan menggunakan react, react-dom dan webpack-dev-server.


## Keunggulan React js ?
Mudah dipahami
Gaya penulisan yang deklaratif membuat react js mudah dipahami dan membuat react mudah di prediksi jika ada kesalahan penulisan kode.
JSX
JSX adalah sebuah extension javascript yang di gunakan react untuk menulis HTML di dalam Javascript. JSX bukanlah sintaks javascript, sehingga browser tidak bisa membaca sintaks ini, di butuh kan sebuah JSX compiler yang di gunakan untuk menterjemahkan JSX kedalam bahasa regular javascript agar bisa terbaca oleh browser. Saya sendiri menggunakan BABEL JS sebagai JSX compilernya.
Modular
Untuk membuat aplikasi dengan skala besar, kita dapat menulis kode-kode dengan skala yang lebih kecil untuk di satukan menjadi aplikasi utuh, dan dapat di gunakan kembali (reusable).
Scalable
React js dapat menangani dengan sangat baik sebuah program dengan skala yang besar yang dapat menampilkan perubahan data yang sangat kompleks.
Flexibel
Dengan belajar 1 libary saja kita dapat membuat aplikasi Web, Moblie, maupun Desktop.
Effisien dan Cepat
React JS menciptakan Virtual DOM untuk mempercepat urusan perubahan DOM. Semua operasi di kerjakan di dalam Virtual DOM, setelah operasi selesai React JS menulis perubahan tersebut di dalam DOM. Contoh kasusnya seperti ini: “Jika kita menulis dalam secarik kertas menggunakan spidol, apabila terjadi kesalahan penulisan kita harus menulis di kertas yang baru. Berbeda jika kita menggunakan pensil, cukup menghapus dan memperbaiki pada bagian yang salah ”.
Mudah Debugging
Ketika kita mulai menggunakan React JS, jangan lupa menginstall extensi resmi React JS. Kita dapat dengan mudah menjelejah Virtual DOM pada aplikasi yang sudah kita buat, sehingga jika ada bug bisa cepat ditemukan.
SEO Bagus
Salah satu masalah terbesar dari library Javascript pada umumnya adalah mereka sidak support search engine. Meskipun sudah banyak perbaikan, mesin pencari umumnya masih mengalami kesulitan. Namun tidak dengan React JS, kita dapat menjalankan React JS pada server dan Virtual DOM diberikan ke browser sebagai halaman web biasa, sehingga sangat support SEO.
## Kelemahan react js ?
Meskipun React JS sangat powerfull, namun juga memiliki beberapa kelemahan antara lain:
Hanya View Layer
React js hanya sebuah pustaka View Layer, untuk membangun aplikasi besar kita harus menyusun sendiri kebutuhan aplikasi lainya seperti data layer, router, struktur aplikasi dan event system(kecuali event DOM).
Dokumentasi tidak bagus
Beberapa sumber artikel yang saya baca mengatakan bahwa dokumentasi react js tidak bagus karena informasi yang di berikan tidak lengkap, meskipun seperti itu kita tetap bisa mempelajarinya kok, tentunya dengan semangat dan ketekunan.
Permasalahan lisensi
Baru-baru ini muncul issue tentang lisensi react. Sebetulnya issue ini sudah ada sejak 2015, namun tampaknya ada pihak-pihak yang belum puas dan mempermasalahkanya. Menurut pemahaman saya bahwa “facebook memperbolehkan kita menggunakan react js untuk mengembangkan produk kita dengan catatan tidak untuk berkompetisi dengan produknya facebook”. Tapi sebenarnya ini tidak masalah , temen-teman bisa baca penjelasanya detail disini.
Dukungan browser
React js tidak mendukung browser versi lama, hanya browser versi baru. React js menghentikan dukungan pada browser Internet Explorer versi 8, sampai saat ini react yang bisa jalan di IE 8 adalah react versi v0.14. Versi terbaru dari react hanya mendukung Internet Explorer versi 9 keatas.


## Mengapa harus pakai react js ?
React js mudah di pahami.
Konsep Components pada react js merupakan konsep pengembangan web modern.
Jika data elements pada aplikasi kita berubah setiap satuan waktu, maka kita bisa menggunakan react sebagai solusinya.
Jika dalam satu team sama-sama sedang belajar react, maka pengembangan aplikasi bisa lebih cepat.

## JSX
JSX is a JavaScript syntax extension which looks similar to XML. Here is an example:

 When compared to JavaScript, it's easier to write JSX. It is as simple as opening and closing XML tags. Here is a JSX example:

<div>
<p>Welcome to TutsPlus</p>
</div>
Here is the compiled React code: 
"use strict";
 
React.createElement(
  "div",
  null,
  React.createElement(
    "p",
    null,
    "Welcome to TutsPlus"
  )
);
1. JSX code ensures readability and makes maintainability easier.

2. JSX optimizes the code while compiling, so it runs faster compared to the equivalent JavaScript code.


# Angular
Dalam angular untuk yang dikategorikan sebagai framework, angular mempunyai struktur untuk proyek yang lebih kompleks. Tentunya Angular digunakan untuk 

contoh aplikasi yang menggunakan angular adalah berikut ini : 
- Eat24
- CVS shop
- onefootball
- Google Express
- NBA
- Delta
- wix.com

# Persamaan

# Perbedaan 


# Unidirectional VS Bidirectional 

