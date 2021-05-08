---
title: Sentiment Analysis with Python 3
description: Menganalisis komentar pada suatu post Facebook dengan topik pornografi menggunakan NLTK(Natural Language Toolkit)
categories:
  - tutorial
---

# Team

- Abdul Ghoni Abbasi (5C414919)
- Aldi Ginanjar (50414741)
- M. Fadlan Prayoga (56414918)
- Widya Maylani (5C414218)

# Scraping
>Web Scraping adalah pengambilan sebuah dokumen semi-struktur dari internet, umumnya berupa halaman-halaman web dalam bahasa markup seperti HTML atau XHTML, dan menganalisis untuk diambil data tertentu dari halaman tersebut



![post]({{site.url}}/assets/images/post.png)



```python
import requests

graph_api_version = 'v2.9'
# paste your access token below
access_token = 'EAAanvSwEfswBAG4xDMDJuJqmsPb179nvHy0XPMR7BcgPejGKBhaa7Iy0EaQu2W5PCOA92BcgiZA9nXJCJrFZBzKksVGwMCQHX7oq7lAXsn4YZBObZAZCI9kKa04m0eMsOpNoeZAwveKaZBu2cKQDUfycIM8zjbor0tbSplAABUlwQZDZD'

user_id = '164305410295882'


post_id = '1727321057327635'


url = 'https://graph.facebook.com/{}/{}_{}/comments'.format(graph_api_version, user_id, post_id)

comments = []

r = requests.get(url, params={'access_token': access_token})
while True:
    data = r.json()
    if 'error' in data:
        raise Exception(data['error']['message'])
    for comment in data['data']:
        text = comment['message'].replace('\n', ' ')
        comments.append(text)
    print('got {} comments'.format(len(data['data'])))
    if 'paging' in data and 'next' in data['paging']:
        r = requests.get(data['paging']['next'])
    else:
        break

#menyimpan komentar ke dalam suatu file
with open('comments.txt', 'w', encoding='utf-8') as f:
    for comment in comments:
        f.write(comment + '\n')
```

import library requests agar mendapatkan akses token dari facebook, kemudian memasukkan access token yang terdapat pada facebook. Berikutnya untuk mengambil semua data komentar pada suatu post facebook yang dibutuhkan adalah id dari user facebook dan id dari post  yang ditentukan dalam variabel url nya. Setelah itu bisa di ketahui konsep scraping untuk mengambil semua komentar di dalam suatu post tersebut membuat array dengan nama comments and menggunakan library requests untuk mendapatkan akses token, untuk dibuat scraping atau data komentar dari suatu post dibuat kondisi terdapat error dalam data JSON tersebut maka ditampilkan pesan error, jika tidak maka dimuat isi array dengan banyak nya komentar menggunakan perintah

```python
for comment in data['data']:
  text = comment['message'].replace('\n', ' ')
  comments.append(text)
```
Jika sudah simpan file python dengan nama `scraping.py` lalu run program yang sudah dibuat dengan perintah `python3 scraping.py` maka akan ditampilkan output
![output1]({{site.url}}/assets/images/output1.png)

Kemudian untuk data comment yang sudah di extract disimpan dalam file bernama `comments.txt` dan output yang dhasilkan dari script python diatas berupa:

![scraping]({{ site.url }}/assets/images/comments.png)

# Sentiment Analysis

Sebelum melakukan sentimen analisis, import library seperti NLTK, pandas

```python
import nltk
import pandas as pd
import string
```

Library yang digunakan yaitu vader lexicon untuk pemanggilan fungsi `SentimentIntensityAnalyzer()`
```python
from nltk.sentiment.vader import SentimentIntensityAnalyzer
sid = SentimentIntensityAnalyzer()
```
## Print Positive, Negative and Neutral

```python
summary = {"positive":0,"neutral":0,"negative":0}
for x in messages:
    ss = sid.polarity_scores(x)
    if ss["compound"] == 0.0:
        summary["neutral"] +=1
    elif ss["compound"] > 0.0:
        summary["positive"] +=1
    else:
        summary["negative"] +=1
print(summary)
```

untuk penentuan suatu komentar termasuk komentar positif dibuat kondisi jika nilai variabel ss yang merupakan perhitungan pada library `SentimentIntensityAnalyzer()` sama dengan 0 maa akan masuk ke dalam indeks "neutral" akan bertambah 1, untuk nilai lebih dari sama dengan maka akan masuk ke dalam indeks "positive" dan untuk nilai komentar yang negatif jika nilai nya kurang dari 0 maka indeks array "negative" akan bertambah. Untuk mencetak perolehan angka sentimen gunakan perintah `print(summary)`

```json

{'positive': 57, 'neutral': 81, 'negative': 55}
```


## Result from Pie Chart

```python
import matplotlib.pyplot as plt
pie_plot = pd.Series(summary,name='')
pie_plot.plot.pie(fontsize=11,figsize=(6,6),autopct='%.2f');
```

Kemudian untuk memvisualisasikan data sentimen nya,gunakan library matplotlib dan dipanggil perintah untuk menyajikan data chart dengan jenis pie sehingga data yang ditampilkan dengan menampilkan dictionary summary dan menampilkan angka persentasi 2 angka dibelakang koma dengan perintah `autopct=%2.f` maka outputnya adalah
![Pie Chart]({{ site.url }}/assets/images/output2.png)
