---
layout: post
title:  "Memoization"
categories: algorithms memoization javascript
---

## Memoization
 From Wikipedia: "...[memoization](https://en.wikipedia.org/wiki/Memoization) is an optimization technique used primarily to speed up computer programs by storing the results of expensive function calls and returning the cached result when the same inputs occur again".  

 In other words, if you're going to do something more than once, save the result after doing it the first time so that you can just reference it later.

 Consider this contrived example using recursion to sum factorials taken for each of a list of values:
 ```javascript
 var list = [7,8,8,8,9,9];
 var timesFactorialCalled = 0;

 function factorial(num){
   timesFactorialCalled++;

   if (num <= 1){
     return 1;
   } else {
     return num-- * factorial(num);
   }
 }

 function sumFactorials(l){
   var result = 0;
   for (i = 0; i < l.length; i++){
     result += factorial(l[i]);
   }
   return result;
 }
 ```
We're taking the factorial of 3 (3 x 2 x 1) and adding the factorial of 3 and then adding the factorial of 4 and so on for the whole array of `list`.

The above code **does not** use memoization and as a result ends up calling the `factorial` function 49 times (the sum total of the `list` array's values).

Now let's look at a very similar implementation that **does** use memoization:

```javascript
var list = [7,7,8,8,9,9];
var timesFactorialCalled = 0;

function factorial(num){
  timesFactorialCalled++;

  if (num <= 1){
    return 1;
  } else {
    return num-- * factorial(num);
  }
}

function sumFactorials(l){
  var result = 0;
  var pre = null;

  for (i = 0; i < l.length; i++){
    if (l[i-1] != l[i]){
      pre = factorial(l[i]);
    }
    result += pre;
  }
  return result;
}

```

This block of code does the same thing as the first block of code, but **instead of calling the factorial function 49 times it only call it 24 times.**  It does this by **memoizing** the previous value of each iteration of the `sumFactorials` inner loop.  If the last number that was fed to `factorial` is the same as the number that you're about to feed to `factorial`, then just avoid the work and use the value that was computed on the previous iteration of the loop.

Granted, the advantages of this approach are obviously dependent on the data that is being used as well as the complexity of the operations being used.  e.g. a list of unique values would run at the same cost whether memoization  is used or not, but a list consisting of the same value repeated over and over again would only have to run the factorial function once before it could simply reference the cached value for the remainder of the iteration.  Still, it's a great thing to take advantage of whenever possible.  Using memoization is very much like using an early `return` and can be thought of in a similar capacity.
