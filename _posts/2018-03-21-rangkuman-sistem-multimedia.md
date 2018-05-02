---
title: Rangkuman Sistem Multimedia
description: membahas tentang jenis text, image dan video
category : tugas kuliah
---

Multimedia  : Adalah beberapa media yang berbeda untuk menggabungkan dan menyampaikan informasi dalam bentuk Text , Audio , Grafik , Animasi dan Video atau bisa juga di katakan kombinasi antara tiga elemen yaitu suara, gambar dan text.

Sistem  : Adalah kumpulan dari elemen – elemen yang berinteraksi untuk mencapai suatu tujuan tertentu.

Sistem Multimedia : Adalah beberapa sistem yang mendukung lebih dari satu macam   media.
## Text

jenis text terbagi dalam 3 kategori


### Plain text
Plain text adalah teks yang dikode dalam format ASCII

Contoh :

![plain]({{site.url}}/assets/images/plaintext.jpg)

### Hyper Text
Hypert Text adalah teks yang memiliki fasilitas linking dan betujuan untuk menyambungkan/berhubungan dengan dokumen lain/teks sebelumnya yang telah diberi atau memiliki format pada sisi penulisannya. Hypert Text disebut juga sebagai link penghubung.
 Hypertext terbagi menjadi dua,yaitu  :

- HTML (Hypertext Markup Language) yang berfungsi untuk mengontrol tampilan web

- XML (Extensible Markup Language) yang berfungsi untuk menjadikan dokumen lebih simple dan lebih cepat.

### Rich text
Rich Text Format adalah teks yang sudah diformatting dan sudah di desain sedemikian rupa sehingga pada teks ini kita dapat memberikan efek pada teks dengan di Bold, Italic, Underline dan diberi warna.

![richtext]({{site.url}}/assets/images/richtext.jpg)
## Image
Image atau citra adalah gambar pada bidang dua dimensi
Sebuah titik terkecil dalam sebuah gambar grafis yang dihitung per inci disebut dengan pixel.
![pixel]({{site.url}}/assets/images/pixel.png)

## Video
Video
Merupakan rangkaian gambar yang ditampilkan secara sekuensial

# Representasi dan Kompresi Data

Kompresi Data merupakan cara untuk memperkeil kebutuhan penyimpanan data

Kompresi terbagi 2 jenis yaitu Lossy dan Loseless

- Lossy : teknik kompresi dengan menghilangkan beberapa informasi penting

- Loseless : teknik kompresi dengan tidak menghilangkan beberapa informasi





## Representasi dan Kompresi pada Data Teks

### Run Length Encoding
Suatu teknik kompresi dengan menghasilkan output Loseless


Contoh :

Data: ABCCCCCCCCDEFGGGG = 17 karakter

dapat menggunakan tanda ! untuk mengurangi panjang nya data sehingga menjadi seperti ini

Data: ABCCCCCCCCDEFGGGG = 17 karakter


### Huffman Coding
Huffman merupakan teknik dengan banyak nya 1 huruf kemudian dibagi banyak nya huruf maka dilakukan Kompresi

Contoh :

MAMA SAYA
A = 4 -> 4/8 = 0.5
M = 2 -> 2/8 = 0.25
S = 1 -> 1/8 = 0.125
Y = 1 -> 1/8 = 0.125
Total = 8 karakter

kemudian dibuat pohon Huffman nya maka menjadi seperti ini
![huffman]({{site.url}}/assets/images/huffman.jpg)

## Representasi dan Kompresi pada Data Suara

Kompresi pada Audio yaitu dengan memotong jarak amplitudo paling maksimum dan minimum yang dianggap noise

Contoh Lossy format :Vorbis, MP3

Contoh Loseless format : FLAC


# Jaringan Multimedia
Penggunaan komputer untuk menampilkan media dengan interaksi dan komunikasi

## Streaming Multimedia

Merupakan multimedia yang secara terus menerus diterima dan ditampilkan oleh user

## Voice Over Internet protocol

teknologi yang memungkinkan komunikasi suara menggunkana jaringan berbasis IP

## Session Internet Protocol
SIP merupakan sebuah protocol standart multimedia dimana merupakan produk dari Internet Engineering Task Force (IETF) dan telah digunakan menjadi suatu standart penggunaan VoIP


## Real Time Transport

Real Time Transport Protocol  (RTP) didefinisikan sebagai standarisasi paket untukmengirimkan audio dan video pada jaringan IP.


# Distribusi multimedia

    B. Broadcasting
penyiaran multimedia baik berupa video maupun suara yang disiarkan kepada penonton melalui media elektronik.
Ex: Live instagram

Cara kerja tv:
    • Kamera merekam sebuah objek yang dengan sistem prism dibagi menjadi tiga warna
    • CCD mengubahnya menjadi sebuah elektronik signal yang disebut video signal
    • Tranmisi merubahnya menjadi signal televisi yang disiarkan melalui antenna dengan gelombang elektromagnetik
    • Anttena rumah akan menerima signal televisi
    • Tunner memisahkan video signal dengan audio signak
    • Video signal dibagi menjadi tiga signal
    • Ketiga signal akan menampilkan gambar  




Cara kerja live broadcasting:
bekerja di saat yang bersamaan secara langsung, dimana audio mengirim datanya ke sound card dan dienkripsi oleh encoder yang akan langsung diupload ke streaming server oleh streamer.
EX:

    C. Internet Radio
Yaitu: audio digital yang ditransmisikan melalui internet.
Cara kerja internet radio:
    1. Audio pada sebuah sound card diencoding pada komputer yang digunakan untuk broadcasting
    2. Sistem encode menterjemahkan audio ke streaming format dan mengkompresnya untuk bisa dikirimkan via internet.
    3. Audio yang telah dikompres dikirim ke server
    4. Server mengirimkan data audio melalui internet ke komputer pendengar melalui sebuah plug-in atau software.
    5. Plug-in akan menterjemhkan data audio dari server ke suara yang bisa didengar pendengar  
EX: Prambors









    D. Video on Demand (VoD)
sistem televisi interaktif yang memfasilitasi untuk memilih sendiri program televisi atau video yang ingin ditonton.

# Augmented Reality

sebuah konsep yang memadukan dunia maya(virtual) dan dunia nyata dengan cara menanamkan sebuah object di dalam proses pembuatannya.

## Jenis - jenis
- Memakai Marker (Marker Based Tracking), yaitu terdapat proses pemakaian marker didalamnya untuk memunculkan objek 2D atau 3D.

- Tanpa Marker (Markerless), yaitu tidak terdapat pemakaian marker didalamnya tetapi menggunakan teknik yang mempunyai ruang lingkup lebih luas daripada metode Marker Based Tracking.


# Digital Culture

suatu perkembangan yang menjadikan budaya di era digital contoh nya seperti mengakses informasi dari internet, serta mengirimkan email dan download upload

contoh : E-commerce, E-book dll  
