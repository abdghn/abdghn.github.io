---
title: Pertemuan 1 Mata Kuliah Pengantar Komputasi Modern
description: Rangkuman Materi tentang Pengenalan Komputasi, Implementasi Komputasi dan Pengenalan Cloud Computing
---


# Teori Komputasi

## Pengertian Teori Komputasi
Teori komputasi adalah cabang ilmu komputer teoritis, berkaitan dengan studi bagaimana persoalan(problem) dapat diselesaikan pada sebuah model dengan menggunakan algoritma. Model tersebut dinamakan model komputasi.

## Teori Otomata
  Teori Otomata adalah teori mengenai mesin-mesin abstrak, dan berkaitan erat dengan teori bahasa formal. ada beberapa hal yang berkaitan dengan Otomata, yaitu Grammar. Grammar adalah bentuk abstrak yang dapat diterima (accept) untuk membangkitkan suatu kalimat otomata berdasarkan suatu aturan tertentu.

## Teori Komputabilitas

Teori komputabilitas bertujuan untuk memeriksa apakah persoalan komputasi dapat dipecahkan pada suatu model komputasi teoritis. Dengan kata lain, teori komputabilitas mengklasifikasikan persoalan sebagai dapat dipecahkan (solvable) atau persoalan yang tidak dapat dipecahkan (unsolvable).

## Teori Kompleksitas
Teori kompleksitas bertujuan untuk mengkaji kebutuhan waktu dan ruang untuk memecahkan persoalan yang diselesaikan dengan pendekatan yang berbeda-beda.


## Model komputasi

### Finite State Automata(FSA) / Finite State Machine(FSM)
Finite State Machine dapat berupa suatu mesin yang tidak memiliki output. Finite State Machine yang tidak mengeluarkan output ini dikenal sebagai Finite State Automata (FSA).

Secara formal FSA dapat didefinisikan sebagai TUPLE-5 : (K, VT, M, S, Z)
Dimana :
K	: himpunan hingga stata,
VT 	: himpunan hingga simbol input (alfabet)
M 	: fungsi transisi, menggambarkan transisi stata AH akibat pembacaan symbol input. (Fungsi transisi ini biasanya diberikan dalam bentuk tabel.)
S  	: stata awal
Z  	: himpunan stata penerima

Ada dua jenis Finite State Automata :
• Deterministic Finite Automata : transisi stata AH akibat pembacaan sebuah simbol
bersifat tertentu. “Jika pada setiap state dari FSA tersebut apabila menerima input
sebuah simbol maka HANYA ada SATU NEXT STATE yang mungkin dituju.”
**M(DFA) : K x VT x K**

• Non Deterministik Finite Automata : transisi stata AH akibat pembacaan sebuah simbol
bersifat tak tentu. “Jika FSA tersebut menerima input simbol maka minimal ada satu
state yang akan berpindah ke LEBIH DARI SATU NEXT STATE yang mungkin dituju.”
**M(AHN) : K x VT x 2K**

#### Contoh Soal


## Push Down Automata(PDA)
PDA adalah mesin otomata yang memiliki kendali masukan menggunakan teknik LIFO (Last In First Out), untuk menentukan apakah suatu output diterima atau tidak oleh mesin tsb. Dalam melakukan proses peneerimaan input, PDA menggunakan memory stack.
Mekanisme kerja memory stack adalah menyimpan input pertama pada alamat paling bawah, input berikutnya di simpan pada alamat di atasnya, dan input terakhir di simpan pada alamat paling atas. Perintah operasi yang digunakan untuk menyimpan input pada stack adalah “push”. Sedangkan perintah operasi untuk mengeluarkan input yang telah tersimpan adalah “pop”.

Sebuah PDA dinyatakan dengan 7 Tupel:
Q = himpunan state
Σ = himpunan simbol input
T = simbol stack
Δ = fungsi transisi
S = state awal
F = state akhir
Z = top of stack

## Turing Machine

Mesin Turing adalah model komputasi teoretis yang ditemukan oleh Alan Turing, berfungsi sebagai model ideal untuk melakukan perhitungan matematis. Walaupun model ideal ini diperkenalkan sebelum komputer nyata dibangun, model ini tetap diterima kalangan ilmu komputer sebagai model komputer yang sesuai untuk menentukan apakah suatu fungsi dapat selesaikan oleh komputer atau tidak (menentukan computable function). Mesin Turing terkenal dengan ungkapan " Apapun yang bisa dilakukan oleh Mesin Turing pasti bisa dilakukan oleh komputer."

![Model Computing]({{ site.url}}/assets/images/model_komputasi.png)

## Implementasi

### Bidang Fisika
Implementasi komputasi modern di bidang Fisika adalah Computational Physics yang mempelajari suatu gabungan antara Fisika, Komputer Sains dan Matematika Terapan untuk memberikan solusi pada “Kejadian dan masalah yang kompleks pada dunia nyata” baik dengan menggunakan simulasi juga penggunaan Algoritma yang tepat.
Banyak perangkat lunak ataupun bahasa yang digunakan, seperti : MatLab, Visual Basic, Fortran, Open Source Physics (OSP), Labview, Mathematica, dan lain sebagainya digunakan untuk pemahaman dan pencarian solusi numerik dari masalah-masalah pada Fisika komputasi.
### Bidang Kimia
Implementasi komputasi modern di bidang Kimia adalah Computational Chemistry yaitu penggunaan ilmu komputer untuk membantu menyelesaikan masalah Kimia. Contohnya penggunaan super komputer untuk menghitung struktur dan sifat molekul. Istilah Kimia teori dapat didefinisikan sebagai deskripsi Matematika untuk Kimia, sedangkan Kimia komputasi biasanya digunakan ketika metode Matematika dikembangkan dengan cukup baik untuk dapat digunakan dalam program komputer.
### Bidang Matematika
Menyelesaikan sebuah masalah yang berkaitan dengan perhitungan Matematis, namun dalam pengertian yang akan dibahas dalam pembahasan komputasi modern ini merupakan sebuah sistem yang akan menyelesaikan masalah Matematis menggunakan komputer dengan cara menyusun Algoritma yang dapat dimengerti oleh komputer.
### Bidang Geografi
Komputasi dalam bidang Geografi biasanya di gunakan untuk peramalan cuaca, di Indonesia khususnya ada salah satu instansi Negara dengan nama BMKG (Badan Meteorologi Klimatologi dan Geofisika) yakni instansi negara yang meneliti mengamati tentang Metereologi, Klimatologi kualitas udara dan Geofisika
### Bidang Geologi
Implementasi pada bidang ini untuk memetakan letak sumber daya dan kontur dari permukaan bumi yang terdapat hasil tambang.

# Cloud Computing
Cloud Computing hadir dengan memudahkan akses data dari mana saja dan kapan saja, karena dengan memanfaatkan internet dan menggunakan perangkat fixed atau mobile device menggunakan internet cloud sebagai tempat penyimpanan data, aplikasi dan lainya


## Grid Computing

Komputasi Grid sebenarnya merupakan sebuah aplikasi pengembangan dari jaringan komputer (network). Hanya saja, tidak seperti jaringan komputer konvensional yang berfokus pada komunikasi antar piranti (device), aplikasi pada grid computing dirancang untuk memanfaatkan sumber daya pada terminal dalam jaringannya.

## Virtualisasi
Virtualisasi adalah sebuah teknologi, yang memungkinkan anda untuk membuat versi virtual dari sesuatu yang bersifat fisik, misalnya sistem operasi, storage data atau sumber daya jaringan. Proses tersebut dilakukan oleh sebuah software atau firmware bernama Hypervisor. Hypervisor inilah yang menjadi nyawanya virtualisasi, karena dialah layer yang “berpura – pura” menjadi sebuah infrastruktur untuk menjalankan beberapa virtual machine.

Istilah virtualisasi perangkat-keras mengacu kepada upaya menciptakan mesin virtual yang bekerja layaknya sebuah komputer lengkap dengan sistem operasi.

**Para-virtualisasi**: Perangkat keras tidak disimulasikan tetapi perangkat-lunak tamu berjalan dalam domainnya sendiri seolah-olah dalam sistem yang berbeda. Dalam hal ini perangkat-lunak tamu perlu disesuaikan untuk dapat berjalan.

**Virtualisasi sebagian**: Tidak semua aspek lingkungan disimulasikan tidak semua perangkat-lunak dapat langsung berjalan, beberapa perlu disesuaikan untuk dapat berjalan dalam lingkungan virtual ini.

**Virtualisasi penuh**: Hampir menyerupai mesin asli dan mampu menjalankan perangkat lunak tanpa perlu diubah.

## Distributed Computation dalam Cloud Computing

Komputasi Terdistribusi merupakan salah satu tujuan dari Cloud Computing, karena menawarkan pengaksesan sumber daya secara parallel, para pengguna juga bisa memanfaatkannya secara bersamaan (tidak harus menunggu dalam antrian untuk mendapatkan pelayanan), terdiri dari banyak sistem sehingga jika salah satu sistem crash, sistem lain tidak akan terpengaruh, dapat menghemat biaya operasional karena tidak membutuhkan sumber daya (resourches).


## Standar Teknologi Informasi pada Cloud Computing
![Model test]({{ site.url}}/assets/images/Gartner.png)



### SaaS (Software as a Service)
Software as a Service adalah layanan software yang digunakan melalui internet. Sebenarnya hal ini bukan merupakan hal yang asing dan sering kita gunakan (hanya mungkin kita belum tahu aja), contoh dari SaaS ini adalah google docs, facebook, aplikasi CRM berbayar, dan lain-lain. Pengguna hanya perlu menggunakan aplikasi tersebut tanpa harus mengerti bagaimana data disimpan, bagaimana aplikasi tersebut di maintenance, karena hal tersebut merupakan service yang disediakan penyedia jasa. Pembayaran dari penggunaan aplikasi-aplikasi ini pun hanya per pemakaiannya (terkadang ada yang tak berbayar tetapi ada fitur-fitur tertentu yang bisa didapatkan ketika pengguna membayar fitur-fitur tersebut, yah semacam nyewa parabola gitu lah, bayar berdasar channel yang diinginkan).

### PaaS (Platform as a Service)
Platform as a Service adalah penyediaan platform bagi developer yang disediakan melalui internet. Hal ini dibutuhkan ketika aplikasi yang disediakan melalui SaaS tidak sesuai dengan kebutuhan proses bisnis yang terdapat pada perusahaan. PaaS memungkinkan kita untuk membangun aplikasi, mengupload aplikasi, melakukan testing aplikasi, ataupun mengatur konfigurasi yang dibutuhkan dalam proses pengembangan aplikasi.

### IaaS (Infrastructure as a Service)
Infrastructure as a Service adalah penyediaan infrastruktur yang disediakan melalui internet dan dibayarkan berdasarkan pemakaian. Hal ini terjadi apabila developer membutuhkan sebuah infrastruktur dimana dia dapat melakukan setting untuk jalannya sebuah aplikasi. IaaS memberikan kendali penuh bagi pengguna layanan untuk menyewa infrastruktur IT (storage, RAM, prosesor dll) secara virtual tanpa sistem operasi, yang tentunya pemilihan sistem operasi tersebut dipilih berdasarkan keinginan pengguna.  Apabila SaaS dan PaaS kurang terasa manfaatnya bagi perusahaan, IaaS ini sangat menguntungkan bagi perusahaan kecil yang membutuhkan sebuah infrastruktur IT tanpa harus membeli perangkat yang dibutuhkan tersebut.
