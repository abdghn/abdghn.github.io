---
title: Belajar Go Part 1
description: Membahas tentang golang, kelebihan dan kekurangan golang dibanding bahas pemrograman dan hello world
categories:
  - tutorial
---

# Penjelasan Golang 
Golang atau Go merupakan bahasa pemrograman yang di publikasikan tahun 2009 oleh Google dan Bahasa Go mengambil struktur sintaks seperti C / C++. 

<!---(https://www.comestoarra.com/news/garbage-collection, Garbage Collection merupakan suatu bentuk manajemen memori otomatis,dimana terdapat suatu yang disebut Collector yang akan berusaha untuk melakukan dealokasi terhadap Garbage,yaitu memori yang dialokasikan untuk objek tertentu yang sudah tidak digunakan lagi.)
--->
# Kelebihan Golang 
- Mendukung konkurensi di level bahasa dengan pengaplikasian cukup mudah
- Mendukung pemrosesan data dengan banyak prosesor dalam waktu yang bersamaan (pararel processing)
- Memiliki garbage collector
- Proses kompilasi sangat cepat
- Bukan bahasa pemrograman yang hirarkial, menjadikan developer tidak perlu ribet memikirkan segmen OOP-nya
- Package/modul yang disediakan terbilang lengkap. Karena bahasa ini open source, banyak sekali developer yang juga mengembangkan modul-modul lain yang bisa dimanfaatkan


# Hello World! 

## Instalasi Go

## Konfigurasi Go

## Membuat Aplikasi Go 
```go 
package main

import "fmt"
func main () {
    fmt.Println("Hello World") 
}
```

atau bisa juga 

```go 
package main

func main () {
    print("Hello World") 
}
```

Kemudian untuk menjalankan aplikasi nya  dengan tahapan awal yaitu compile

```
go build main.go
```

Kemudian untuk menjalankan aplikasi dengan perintah 

```
./main
```
Jika ingin melakukan perbaikan bugs atau error tidak perlu menggunakan compile, bisa dengan perintah 

```
go run main.go
```

```go
import f "fmt"

func main(){
    f.Println("Hello World")
}
```
## Variabel 
Untuk mendekralasi variabel pada Go dapat menggunakan tipe data atau tidak. Perbedaannya hanya di bagian penulisan nya saja. 

### Variabel dengan tipe data 
Deklarasi dengan tipe data atau yang biasa disebut **manifest typing** pada Go memiliki standar yaitu menggunakan keyword var dan menggunakan jenis tipe data nya apa. contohnya bisa dilihat di bawha ini. 
```go 
package main

import "fmt"

func main() {
    var firstName string = "john"

    var lastName string
    lastName = "wick"

    fmt.Printf("halo %s %s!\n", firstName, lastName)
}

```


### Variabel tanpa tipe data  
Deklarasi tanpa tipe data atau yang biasa disebut **interfence** pada Go untuk mendeklarasikan variabel 

```go 
var firstName string = "john"
lastName := "wick"

fmt.Printf("halo %s %s!\n", firstName, lastName)
```
