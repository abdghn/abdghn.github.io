---
title: Sentiment Analysis with Python 3
description: menganalisis komentar pada suatu post facebook menggunakan NLTK
categories:
  - tutorial
---

# Scraping


Untuk mengambil data dari suatu post facebook, pertama kita scraping suatu post tersebut dengan kodingan dibawah ini

```python
import requests

graph_api_version = 'v2.9'
# paste your access token below
access_token = 'EAAanvSwEfswBAG4xDMDJuJqmsPb179nvHy0XPMR7BcgPejGKBhaa7Iy0EaQu2W5PCOA92BcgiZA9nXJCJrFZBzKksVGwMCQHX7oq7lAXsn4YZBObZAZCI9kKa04m0eMsOpNoeZAwveKaZBu2cKQDUfycIM8zjbor0tbSplAABUlwQZDZD'

# LHL's Facebook user id
user_id = '125845680811480'

# the id of LHL's response post at https://www.facebook.com/leehsienloong/posts/1505690826160285
post_id = '1505690826160285'

# the graph API endpoint for comments on LHL's post
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
import library requests agar mendapatkan akses token dari facebook, kemudian memasukkan access token yang terdapat pada facebook. Berikutnya untuk mengambil semua data komentar pada suatu post facebook yang dibutuhkan adalah id dari user facebook dan id dari post  yang ditentukan dalam variabel url nya. Setelah itu untuk mengambil semua komentar di dalam suatu post tersebut membuat array dengan nama comments and menggunakan library requests untuk mendapatkan akses token, untuk dibuat scraping atau data komentar dari suatu post dibuat kondisi terdapat error dalam data JSON tersebut maka ditampilkan pesan error, jika tidak maka dimuat isi array dengan banyak nya komentar menggunakan perintah
```python
for comment in data['data']:
  text = comment['message'].replace('\n', ' ')
  comments.append(text)
```

Kemudian untuk data comment yang sudah di extract disimpan dalam file bernama comments.txt dan output yang dhasilkan dari script python diatas berupa :

![images]

# Sentiment Analysis

Sebelum melakukan sentiment analysis, import library seperti NLTK, pandas
```python
import nltk
import pandas as pd
import string
```
library yang digunakan yaitu vader lexicon untuk pemanggilan fungsi SentimentIntensityAnalyzer
```python
from nltk.sentiment.vader import SentimentIntensityAnalyzer
sid = SentimentIntensityAnalyzer()
```
## Print Positive, Negative and Neutral

```Python
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

untuk penentuan suatu komentar termasuk komentar positif dibuat kondisi jika nilai variabel ss yang merupakan perhitungan pada library SentimentIntensityAnalyzer sama dengan 0 maa akan masuk ke dalam indeks "neutral" akan bertambah 1, untuk nilai lebih dari sama dengan maka akan masuk ke dalam indeks "positive" dan untuk nilai komentar yang negatif jika nilai nya kurang dari 0 maka indeks array negatif akan bertambah.
Setelah import library sentiment analyzer dari NLTK

```
{'neutral': 594, 'positive': 1187, 'negative': 271}
```

![my photo]({{ site.url }}/assets/images/Screenshot from 2018-03-18 23-37-32.png)


## Result from Pie Chart
```python
import matplotlib.pyplot as plt
pie_plot = pd.Series(summary,index=summary)
pie_plot.plot.pie(fontsize=11,figsize=(6,6),autopct='.%f');
```
![Pie Chart]({{ site.url }}/assets/images/output_5_0.png)
