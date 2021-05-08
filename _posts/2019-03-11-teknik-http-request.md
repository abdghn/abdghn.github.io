---
title: Pengenalan Teknik - teknik request http pada javascript
description: Hal yang harus didasari adalah pengenalan Neural Network untuk bisa mencapai Deep Learning
---

# AJAX
Ajax adalah cara paling tradisional yang melakukan request HTTP. Data bisa dikirim dengan menggunakan method HTTP POST dan menerima data dengan HTTP GET.

Untuk membuat HTTP call di Ajax, kita perlu membuat sebuah objek XMLHttpRequest(), menentukan URL endpoint dan HTTP method-nya. Selanjutnya kita memanggil method open() untuk membuka koneksi ke URL yang dimasukkan menggunakan HTTP method yang diinginkan. Method send() akan memulai proses koneksi yang sebelumnya sudah dibuka oleh open().

Method onreadystatechange dipanggil saat objek Http telah berhasil mendapat data yang diperlukan atau gagal. Ia memiliki dua method yaitu readyState dan status untuk memeriksa status request yang dilakukan.


# Fetch
fetch adalah salah satu tool yang membantu melakuan request Asynchronous dengan lebih mudah. Ia mengembalikan sebuah Promise yang merupakan salah satu fitur andalan ES6. Perhatikan bagaimana cara penggunaan fetch di bawah ini:

*code
const API = 'https://hn.algolia.com/api/v1/search?query=';

  fetch(API + DEFAULT_QUERY)
      .then(response => {
        if (response.ok) {
          return response.json();
        } else {
          throw new Error('Something went wrong ...');
        }
      })
      .then(data => this.setState({ hits: data.hits, isLoading: false }))
      .catch (error => this.setState({ error, isLoading: false }));
*

Fungsi fetch meminta sebuah parameter yaitu alamat URL endpoint. Ia juga bisa menerima parameter lain sebagai query parameter untuk URL yang diberikan.

# Axios


Link : https://www.codepolitan.com/teknik-teknik-melakukan-request-http-di-javascript-5afa5536d44e9
