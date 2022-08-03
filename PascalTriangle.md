## Introduction
This article discusses the famous Pascal triangle and applies dynamic programming to solve it.

## Pascal's Triangle

![A GIF picture of Pascal's triangle with five rows](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wm8ogibhm8r0zwo5deza.gif)

- There are **n** rows
- Each row has **n** elements
- The First and last element of each row is 1

## Basic observation
Observing Pascal's triangle, you will notice that:
 - The first row has only one element [1]
 - The second row has two elements [1, 1]

## Base case
Using *Basic observation* we can drive the *Base Cases* for Pascal's triangle for *n = 1* and *n = 2*.
```js
  function generate(numRows: number): number[][] {
    let res: number[][] = [[1]];
    if(numRows === 1) {
        return res;
    }
    res.push([1, 1]);
    if(numRows === 2){
        return res;
    }
  /// for numRows > 2 we need to figure it out
}
```
When *n = 1*, there is a single row, so the answer is *[[1]]*
when *n = 2*, there are two rows and second row is *[1,1]* so the answer is [[1] [1,1]].
### Intuition

Let us consider *n = 3*
![Pascal's triangle with n = 3](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9rgp88tvopli72gv27a0.png)

We can use the previous *n - 1* values to determine all the values for the *nth* row.

We previously defined *Base Cases* n = 1 and n = 2 so we at least have this result ```[[1], [1,1]]```

### Filling the nth row
We know the first and last items are always 1. The rest of the items are filled using the previous row.
```js
 nthRow[0] = 1,
 nthRow[lastIndx] = 1
 nthRow[i] = prevRow[i] + prevRow[i + 1]
```

### Code
 ```ts
function generate(numRows: number): number[][] {
  let result: number[][] = [[1]];
  if (numRows === 1) {
    return result;
  }
  result.push([1, 1]);
  if (numRows === 2) {
    return result;
  }

  for (let i = 2; i < numRows; i++) {
    let tempList: number[] = [];
    let prevList: number[] = result[i - 1];
    tempList.push(1); //first item is always 1
    for (let j = 0; j < prevList.length - 1; j++) {
      tempList.push(prevList[j] + prevList[j + 1]);
    }
    tempList.push(1); //last item is always 1
    result.push(tempList);
  }

  return result;
}
console.log(generate(5));
```
### Time And Space Complexity
 - ***TC O(n ^ 2)***
 - ***Space O(n ^ 2)***
