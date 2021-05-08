---
title: Belajar Uni Testing Javascript
description: Unit Testing Javascript menggunakan Mocha JS & Chai
categories:
  - tutorial
---
# Teori
>Unit Testing is a level of software testing where individual units/ components of a software are tested
 
 Penjelasan dari teori unit testing yaitu untuk menguji apakah fungsi yang kita buat telah sesuai dengan desain sistem. 

 Kalau diibaratkan dalam kegiatan nyata misalkan kita ingin memasak tentunya hal pertama yang dilakukan adalah menyiapkan baik itu peralatan atau bahan memasak. Dalam membuat suatu masakan, hal - hal yang harus diperhatikan adalah seperti berapa lama dalam mengaduk bahan - bahan yang telah dicampurkan, menentukan suhu pada kompor atau oven, atau takaran untuk menaruh bumbu masak. Dalam unit testing, langkah - langkah untuk melakukan adalah  :
  - Menentukan nilai dari parameter input
  - Memanggil unit yang dites melewatkannya dengan parameter input
  - Menerima parameter kembalian dari unit yang dites dan mencetaknya, menampilkannya, atau mengetes hasilnya terhadap hasil yang diharapkan

Keuntungan yang didapat dengan melakukan dengan unit testing adalah
- Mencari error atau bug yang disebabkan oleh perubahan code menjadi lebih mudah
- Code menjadi lebih reusable
- Waktu yang dibutuhkan untuk melakukan debug lebih sedikit karena tidak perlu melakukan “developer test” dimana kita menjalankan program kita sambil menyediakan beberapa input untuk menguji apakah program akan berjalan sesuai keinginan kita.

Pada javascript, unit testing yang digunakan adalah Mocha JS dan Chai. 

```
npm install mocha chai
```

Kemudian fungsi untuk development 

```javascript
module.exports = function(){
    return 'hello'
}
```

Lalu untuk membuat fungsi unit testing untuk menguji fungsi yang mengembalikan nilai string 'hello'. berikut ini adalah fungsi uit testing nya 

```javascript
const assert = require('chai').assert
const app = require('../app')


describe('App', function(){ 
    it('should return hello', function(){
        assert.equal(app(), 'hello')
    })
})
```

Dari describe yaitu untuk mengambil dari export controller **App** 