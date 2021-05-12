---
title: Hackerrank test solution part 1
description: Hackerrank test solution
categories:
  - tutorial
---

# Simple Array Sum

tujuannya adalah untuk mendapatkan jumlah dari tiap elemen array, contohnya **1 + 2 + 4 + 10 + 11 = 31**

## Input
```
6
1 2 3 4 10 11
```
## Output
```
31
```

## Code

```javascript
  var sum = 0;
    for (var i = 0; i <ar.length; i++) {
    sum += ar[i];
    }
    return sum;
```
## Alternative

```javascript
  let sum = (accumulator, currentValue) => accumulator + currentValue;
  return ar.reduce(sum);
```

# Compare the Triplets
di **compare the triplets** ini bertujuan untuk menentukan nilai mana yang lebih besar dari tiap elemen array, contohnya kasus nya :
jika a mempunyai array **[1,2,3]** dan b mempunyai array **[3,2,1]** dengan kondisi di bawah ini
- jika a[0] lebih besar dari pada b[0] maka a mendapatkan poin 1
- jika a[1] sama dengan b[1]maka tidak ada yang mendapatkan poin
- jika a[2] lebih kecil dari b[2] maka b yang mendapatkan poin

kemudian hasil poin antara a dan menggabungkan ke dalam array menjadi [1,1]

## Input 
```
17 28 30
99 16 8
```

## Output
```
2 1
```

## Code
```javascript
    let score = [0,0]

    for (let i = 0; i < a.length; i++)
        a[i] > b[i] ? score[0]++ : a[i] < b[i] ? score[1]++ : ""
    return score
```

# A Very Big Sum
tujuannya adalah untuk mendapatkan jumlah dari tiap elemen array, contohnya **1 + 2 + 4 + 10 + 11 = 31**

## Input
```
6
1 2 3 4 10 11
```
## Output
```
31
```

## Code
```javascript
    let score = [0,0]

    for (let i = 0; i < a.length; i++)
        a[i] > b[i] ? score[0]++ : a[i] < b[i] ? score[1]++ : ""
    return score
```

## Alternative
```javascript
  let sum = (accumulator, currentValue) => accumulator + currentValue;
  return ar.reduce(sum);
```

# Diagonal Difference

## Input
```
3
11 2 4
4 5 6
10 8 -12
```

## Output
```
15
```

## Explanation

The primary diagonal is:
```
11
   5
     -12
```

Sum across the primary diagonal: 11 + 5 - 12 = 4
The secondary diagonal is:
```
     4
   5
10
```

## Code

```javascript
    var n = matrix.length;
    var diag1 = 0;
    var diag2 = 0;
    for(var i=0; i<n; i++){
        for(var j=0; j<n; j++){
            // an element from the main diagonal
            if(i === j) { 
                diag1 += matrix[i][j];
            }
            // an element from the counterdiagonal
            if(i + j === n - 1){
                diag2 += matrix[i][j];
            }
        }
    }
    return Math.abs(diag1 - diag2);
```
# Plus Minus

## Input
```
STDIN           Function
-----           --------
6               arr[] size n = 6
-4 3 -9 0 4 1   arr = [-4, 3, -9, 0, 4, 1]
```

## Output
```
0.500000
0.333333
0.166667
```

## Code
```javascript
 let positives = 0, negatives = 0, zeros = 0;
     const len = arr.length || 0;
      
     if (len > 0 && len <= 100) {
          arr.map((elem, key) => {
               if (elem > 0) {
                    positives++;
               } else if (elem < 0) {
                    negatives++; 
               } else {
                    zeros++;
               }
                  
               return elem; 
          }); 
     } 
     
     console.log((positives / len) || 0);
     console.log((negatives / len) || 0);
     console.log((zeros / len) || 0);  
```

## Alternative
```javascript
    let positive = arr.filter(number => number > 0).length / arr.length;
    let negative = arr.filter(number => number < 0).length / arr.length;;
    let zeronums = arr.filter(number => number == 0).length / arr.length;;
    return console.log(positive.toFixed(6) + '\n' + negative.toFixed(6) + '\n' + zeronums.toFixed(6))
```


