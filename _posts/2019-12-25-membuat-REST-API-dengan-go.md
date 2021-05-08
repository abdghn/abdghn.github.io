---
title: REST API dengan GO
description: Membahas tentang membuat API dengan Go atau Golang
categories:
  - tutorial
---


#  REST API

# Membuat Program Go 
Berikut ini adalah program Go 

```go 
package main

import (
    "log"
    "net/http"
)

type server struct{}

func (s *server) ServeHTTP(w http.ResponseWriter, r *http.Request) {
    w.WriteHeader(http.StatusOK)
    w.Header().Set("Content-Type", "application/json")
    w.Write([]byte(`{"message": "hello world"}`))
}

func main() {
    s := &server{}
    http.Handle("/", s)
    log.Fatal(http.ListenAndServe(":8080", nil))
}
```

lalu untuk run program nya menggunakan 

```
go run main.go
```


```json
{"message": "hello world"}
```

Berikut nya untuk menunjukkan menggunakan `ServeHTTP`

```go
package main

import (
    "log"
    "net/http"
)

func home(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "application/json")
    switch r.Method {
    case "GET":
        w.WriteHeader(http.StatusOK)
        w.Write([]byte(`{"message": "get called"}`))
    case "POST":
        w.WriteHeader(http.StatusCreated)
        w.Write([]byte(`{"message": "post called"}`))
    case "PUT":
        w.WriteHeader(http.StatusAccepted)
        w.Write([]byte(`{"message": "put called"}`))
    case "DELETE":
        w.WriteHeader(http.StatusOK)
        w.Write([]byte(`{"message": "delete called"}`))
    default:
        w.WriteHeader(http.StatusNotFound)
        w.Write([]byte(`{"message": "not found"}`))
    }
}

func main() {
    http.HandleFunc("/", home)
    log.Fatal(http.ListenAndServe(":8080", nil))
}
```


# Gorilla Mux 
 Dalam menggunakan gorilla mux dengan menggunakan perintah 

 ```
 go get github.com/gorilla/mux
 ```

 setelah menambahkan mod gorilla mux, kode program nya seperti ini 

```go
package main

import (
    "log"
    "net/http"

    "github.com/gorilla/mux"
)

func home(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "application/json")
    switch r.Method {
    case "GET":
        w.WriteHeader(http.StatusOK)
        w.Write([]byte(`{"message": "get called"}`))
    case "POST":
        w.WriteHeader(http.StatusCreated)
        w.Write([]byte(`{"message": "post called"}`))
    case "PUT":
        w.WriteHeader(http.StatusAccepted)
        w.Write([]byte(`{"message": "put called"}`))
    case "DELETE":
        w.WriteHeader(http.StatusOK)
        w.Write([]byte(`{"message": "delete called"}`))
    default:
        w.WriteHeader(http.StatusNotFound)
        w.Write([]byte(`{"message": "not found"}`))
    }
}

func main() {
    r := mux.NewRouter()
    r.HandleFunc("/", home)
    log.Fatal(http.ListenAndServe(":8080", r))
}
```

## Handle HTTP methods
Dalam menggunakan `Handlefunc` untuk membuat fungsi di handle oleh HTTP method

```go 
package main

import (
    "log"
    "net/http"

    "github.com/gorilla/mux"
)

func get(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(http.StatusOK)
    w.Write([]byte(`{"message": "get called"}`))
}

func post(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(http.StatusCreated)
    w.Write([]byte(`{"message": "post called"}`))
}

func put(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(http.StatusAccepted)
    w.Write([]byte(`{"message": "put called"}`))
}

func delete(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(http.StatusOK)
    w.Write([]byte(`{"message": "delete called"}`))
}

func notFound(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(http.StatusNotFound)
    w.Write([]byte(`{"message": "not found"}`))
}

func main() {
    r := mux.NewRouter()
    r.HandleFunc("/", get).Methods(http.MethodGet)
    r.HandleFunc("/", post).Methods(http.MethodPost)
    r.HandleFunc("/", put).Methods(http.MethodPut)
    r.HandleFunc("/", delete).Methods(http.MethodDelete)
    r.HandleFunc("/", notFound)
    log.Fatal(http.ListenAndServe(":8080", r))
}
```

## Sub Router

```go 
func main() {
    r := mux.NewRouter()
    api := r.PathPrefix("/api/v1").Subrouter()
    api.HandleFunc("", get).Methods(http.MethodGet)
    api.HandleFunc("", post).Methods(http.MethodPost)
    api.HandleFunc("", put).Methods(http.MethodPut)
    api.HandleFunc("", delete).Methods(http.MethodDelete)
    api.HandleFunc("", notFound)
    log.Fatal(http.ListenAndServe(":8080", r))
}
```

Kemudian menambahkan prefix dengan contoh `api/v1` jika ingin membuat v2 nanti nya 

```go
package main

import (
    "fmt"
    "log"
    "net/http"
    "strconv"

    "github.com/gorilla/mux"
)

func get(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(http.StatusOK)
    w.Write([]byte(`{"message": "get called"}`))
}

func post(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(http.StatusCreated)
    w.Write([]byte(`{"message": "post called"}`))
}

func put(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(http.StatusAccepted)
    w.Write([]byte(`{"message": "put called"}`))
}

func delete(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(http.StatusOK)
    w.Write([]byte(`{"message": "delete called"}`))
}

func params(w http.ResponseWriter, r *http.Request) {
    pathParams := mux.Vars(r)
    w.Header().Set("Content-Type", "application/json")

    userID := -1
    var err error
    if val, ok := pathParams["userID"]; ok {
        userID, err = strconv.Atoi(val)
        if err != nil {
            w.WriteHeader(http.StatusInternalServerError)
            w.Write([]byte(`{"message": "need a number"}`))
            return
        }
    }

    commentID := -1
    if val, ok := pathParams["commentID"]; ok {
        commentID, err = strconv.Atoi(val)
        if err != nil {
            w.WriteHeader(http.StatusInternalServerError)
            w.Write([]byte(`{"message": "need a number"}`))
            return
        }
    }

    query := r.URL.Query()
    location := query.Get("location")

    w.Write([]byte(fmt.Sprintf(`{"userID": %d, "commentID": %d, "location": "%s" }`, userID, commentID, location)))
}

func main() {
    r := mux.NewRouter()

    api := r.PathPrefix("/api/v1").Subrouter()
    api.HandleFunc("", get).Methods(http.MethodGet)
    api.HandleFunc("", post).Methods(http.MethodPost)
    api.HandleFunc("", put).Methods(http.MethodPut)
    api.HandleFunc("", delete).Methods(http.MethodDelete)

    api.HandleFunc("/user/{userID}/comment/{commentID}", params).Methods(http.MethodGet)

    log.Fatal(http.ListenAndServe(":8080", r))
}
```