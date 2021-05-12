---
title: Hackerrank test solution part 3
description: Hackerrank test solution
categories:
  - tutorial
---

# Apple and Orange

## Input

## Output

## Code

```javascript
const fLoc = function (treeLoc, arr2d) {
       return arr2d.map(fruitLoc => (treeLoc + fruitLoc));
    }
    const fRange = function (s, t, arr2d) {
        let a, b;
        a = 0; b = 0;
        arr2d.forEach((f, i) => {
            if (i === 0) { // apple count
                f.forEach(loc => s <= loc && loc <= t ? a++ : null);
            }
            if (i === 1) { // orange count
                f.forEach(loc => s <= loc && loc <= t ? b++ : null);
            }
        });
        return [a, b];
    }
    console.log(fRange(s, t, [fLoc(a, apples), fLoc(b, oranges)]).join('\n'));
```

## Alternative

```javascript
// using filter
function countApplesAndOranges2(s, t, a, b, apples, oranges) {
  console.log(apples.filter(d => s - a <= d && d <= t - a).length);
  console.log(oranges.filter(d => s - b <= d && d <= t - b).length);
}

```

```javascript

// using reduce
function countApplesAndOranges3(s, t, a, b, apples, oranges) {
  console.log( apple.reduce((sum, d) => sum + (s - a <= d && d <= t - a), 0));
  console.log(orange.reduce((sum, d) => sum + (s - b <= d && d <= t - b), 0));
}
```

```javascript
// using filter and map
function countApplesAndOranges4 {
  function addBy(num) {
    return (d) => d + num;
  }
  function isScored(d) {
    return s <= d && d <= t;
  }
 const larry = apples.map(addBy(a)).filter(isScored).length;
  const rob = oranges.map(addBy(b)).filter(isScored).length;
  console.log(larry, rob);
}
```

```javascript
// using Array.prototype (bad because a new version of ECMA could come out with a 'sum' helper for arrays)
function countApplesAndOranges5 {
  Array.prototype.sum = function(f) {
      return this.reduce((s, v) => s + f(v), 0);
  }
  console.log( apple.sum(d => s - a <= d && d <= t - a));
  console.log(orange.sum(d => s - b <= d && d <= t - b));
}
```

# Number Line Jumps
pada soal ini dijelaskan bahwa jika ada case 2 kangguru sama - sama meloncat maka lokasi mana kah kedua kangguru tersebut mendarat di tempat yang sama. Misal

- x1 = 2
- v1 = 1
- x2 = 1
- v2 = 2

jika melompat bersamaan, yaitu counter nya bernilai 3 maka nilainya akan sama mengembalikan nilai 'YES'

## Input
```
0 3 4 2
```

## Output
```
YES
```

# Explanation
Pertama kita define variable dengan nama **result** kemundian kita kasih nilai default yaitu 'NO'. Kemudian kita lakukan melakukan perulangan sampai variable i lebih besar dari 10000, lalu check jika 
**x1 + v1 * i === x2 + v2 * i** maka langsung menghasilkan nilai 'YES', jika maka perulangan tetap di lanjutkan sampai ketemu kondisi diatas terpenuhi atau menghasil nilai 'YES'
## Code

```javascript
    let result = 'NO'
    for (let i = 0; i <= 10000; i++) {
        if (x1 + v1 * i === x2 + v2 * i) {
            result = 'YES'
        }
    }
    return result;
```