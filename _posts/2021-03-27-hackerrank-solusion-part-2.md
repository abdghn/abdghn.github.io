---
title: Hackerrank test solution part 2
description: Hackerrank test solution
categories:
  - tutorial
---


# Staircase

## Input
```
6
```

## Output
```
     #
    ##
   ###
  ####
 #####
######
```

## Code

```javascript

    // want to declare a variable that will hold the final output that we will print 
    let output = ''
    
    // outer for loop to keep track of the overall number of rows (n)
    for (let i = 1; i <= n; i++) {
    
        // inner for loop to keep track of the preceding spaces on each line
            // s should start out at n-1 which we can see from the pic I drew
            // s should be greater than or equal to i because the number of spaces decreases as i increases
            // decrease s bc the number of spaces decreases as i increases
        for (let s = n - 1; s >= i; s--) {
            output += ' '
        }
        
        // inner for loop to keep track of the #s on each line
            // h should start at one because the first line will always have one #
            // h should be less than or equal to the row that we are on since h will approach and eventually equal n
            // h increases since we increment h to equal i which will eventually equal n
        for (let h = 1; h <= i; h++) {
            output += '#'
        }
        // new line
        output += "\n"
       
    }
    // log the final result
    console.log(output)
```

## Alternative
```javascript
// here we use just one for loop where i tracks the number of rows
  // the number of rows (i) should be less than or equal to n
    for (let i = 1; i <= n; i++) {
      // print out a " " n-i times and append a # i times
      // console log adds a new line by default
      
        console.log(" ".repeat(n-i) + "#".repeat(i))
    }    
```

# Birthday Cake Candles

## Input
```
4
3 2 1 3
```
## Output
```
2
```

## Explanation

Candle heights are **[3,2,1,3]** . The tallest candles are **3** units, and there are **2** of them.

## Code

```javascript
// Step 1
    let max = 0;
    let counter = 0;

    // Step 2 (a)
    arr.forEach(item => {
        // Step 3
        if (item > max) {
            // Step 4
            max = item;
            counter = 1;
            // Step 2 (b)
        } else if (item === max) {
            counter++;
        }
    });

    return counter;
```

## Alternative

``` javascript
    let maxNum = Math.max(...ar);
    let filtered = ar.filter(function(value, index, arr) {
        return value === maxNum;
    });
    return filtered.length;
```


# Time Conversion

## Input

## Output

## Code

```javascript
const arr = s.slice(0,8).split(':');
arr[0] = (s.indexOf('PM') > -1) ?
         (arr[0] == 12 ? '12' : Number(arr[0]) + 12) :
         (arr[0] == 12 ? '00' : arr[0]);
return arr.join(':');
```

# Grading Students

## Input

## Outputs

## Code

```javascript
    let output = [];
    for (let i = 0; i < grades.length; i++) {
        if (grades[i] >= 38) {
            let reminder = grades[i] % 5;
            if (reminder === 3) {
                output.push(grades[i] + 2)
            } else if (reminder === 4) {
                output.push(grades[i] + 1)
            } else {
                output.push(grades[i]);
            }
        } else {
            output.push(grades[i]);
        }
    }

    return output;
```

# Mini-Max Sum


## Input


## Output

## Code
```javascript
  let minValue = 0, maxValue = 0, minIndex = 0, maxIndex = 0, minSum = 0, maxSum = 0;
  minValue = Math.min(...arr);
  maxValue = Math.max(...arr);
  minIndex = arr.indexOf(minValue);
  maxIndex = arr.indexOf(maxValue);

  for (let i = 0; i < arr.length; i++){
      if (minIndex != i) {
          maxSum += arr[i];
      }
      if (maxIndex != i) {
          minSum += arr[i];
      }
  }
     console.log(minSum, maxSum);
```

## Alternative

```javascript
    let maxVal = Math.max(...arr);
    let minVal = Math.min(...arr);
    console.log((sum - maxVal) + ' ' + (sum - minVal));
```
